# Lab 07 – Accessible Form Validation

## Purpose

Form validation is only useful if it communicates to every user — not just those who can see a red border change. This lab builds a complete event registration form with client-side validation that is perceivable, associated with its fields, and timed correctly.

## Skills practiced

- Using `addEventListener` for form `submit` and input `blur` events
- Calling `event.preventDefault()` to stop default form navigation
- Writing validation functions that return error strings or `null`
- Displaying error messages linked to inputs with `aria-describedby`
- Setting and removing `aria-invalid` on form inputs
- Managing focus after a successful or failed submission

## What you're building

An **Event Registration Form** for a fictional campus workshop. The form collects name, email, phone, student ID, event selection, and a dietary restriction field. All validation runs in the browser. On valid submission, the form is replaced with a confirmation message that receives focus.

---

## Part 1: HTML structure

Create `labs/lab07/index.html`. Build the form with the following fields. Every input must have:
- A `<label>` connected with matching `for`/`id` attributes
- An associated `<span>` with a unique `id` for the error message (`id="[field]-error"`)
- `aria-describedby="[field]-error"` on the input pointing to that span
- An empty error span by default (content is injected by JavaScript)

```html
<form id="registration-form" novalidate>
  <h1>Workshop Registration</h1>

  <div class="field-group">
    <label for="full-name">Full Name <span aria-hidden="true">*</span></label>
    <input type="text" id="full-name" name="full-name"
           aria-describedby="full-name-error" autocomplete="name">
    <span id="full-name-error" class="error-msg" aria-live="polite"></span>
  </div>

  <div class="field-group">
    <label for="email">Email Address <span aria-hidden="true">*</span></label>
    <input type="email" id="email" name="email"
           aria-describedby="email-error" autocomplete="email">
    <span id="email-error" class="error-msg" aria-live="polite"></span>
  </div>

  <div class="field-group">
    <label for="phone">Phone Number</label>
    <input type="tel" id="phone" name="phone"
           aria-describedby="phone-error" autocomplete="tel">
    <span id="phone-error" class="error-msg" aria-live="polite"></span>
  </div>

  <div class="field-group">
    <label for="student-id">Student ID <span aria-hidden="true">*</span></label>
    <input type="text" id="student-id" name="student-id"
           aria-describedby="student-id-error">
    <span id="student-id-error" class="error-msg" aria-live="polite"></span>
  </div>

  <div class="field-group">
    <label for="event-select">Select Workshop <span aria-hidden="true">*</span></label>
    <select id="event-select" name="event-select"
            aria-describedby="event-select-error">
      <option value="">-- Choose a workshop --</option>
      <option value="web-basics">Web Basics</option>
      <option value="intro-python">Intro to Python</option>
      <option value="ux-design">UX Design Fundamentals</option>
    </select>
    <span id="event-select-error" class="error-msg" aria-live="polite"></span>
  </div>

  <div class="field-group">
    <label for="dietary">Dietary Restrictions (optional)</label>
    <textarea id="dietary" name="dietary" rows="3"
              aria-describedby="dietary-error"></textarea>
    <span id="dietary-error" class="error-msg" aria-live="polite"></span>
  </div>

  <button type="submit">Register</button>
</form>

<div id="confirmation" hidden tabindex="-1">
  <h2>You're registered!</h2>
  <p id="confirmation-details"></p>
  <a href="index.html">Register another person</a>
</div>
```

The `novalidate` attribute disables the browser's built-in validation so yours runs instead.

---

## Part 2: Validation functions

In `labs/lab07/lab07.js`, write these pure validation functions that return an error string if invalid or `null` if valid:

```js
function validateName(value) {
  if (!value.trim()) return 'Full name is required.';
  if (value.trim().length < 2) return 'Name must be at least 2 characters.';
  return null;
}

function validateEmail(value) {
  if (!value.trim()) return 'Email address is required.';
  if (!value.includes('@') || !value.includes('.')) return 'Please enter a valid email address.';
  return null;
}

function validatePhone(value) {
  // Optional field — only validate format if a value is entered
  if (!value.trim()) return null;
  const digitsOnly = value.replace(/\D/g, '');
  if (digitsOnly.length < 10) return 'Phone number must have at least 10 digits.';
  return null;
}

function validateStudentId(value) {
  if (!value.trim()) return 'Student ID is required.';
  if (!/^\d{7,9}$/.test(value.trim())) return 'Student ID must be 7–9 digits.';
  return null;
}

function validateEvent(value) {
  if (!value) return 'Please select a workshop.';
  return null;
}
```

---

## Part 3: Error display functions

```js
function showError(inputEl, message) {
  const errorEl = document.getElementById(`${inputEl.id}-error`);
  errorEl.textContent = message;
  inputEl.setAttribute('aria-invalid', 'true');
  inputEl.classList.add('input-error');
}

function clearError(inputEl) {
  const errorEl = document.getElementById(`${inputEl.id}-error`);
  errorEl.textContent = '';
  inputEl.removeAttribute('aria-invalid');
  inputEl.classList.remove('input-error');
}
```

---

## Part 4: Validation timing

### On `blur` (early feedback)

For the Name and Email fields, add a `blur` listener that validates when the user leaves the field. Only show an error if the field was touched and is invalid — do not show errors on fields the user has not interacted with yet.

```js
const nameInput = document.getElementById('full-name');
nameInput.addEventListener('blur', () => {
  const error = validateName(nameInput.value);
  if (error) showError(nameInput, error);
  else clearError(nameInput);
});
```

Add a similar blur listener for the email field.

### On `submit`

The form's `submit` handler should:
1. Call `event.preventDefault()`
2. Validate all required fields
3. Show errors for all invalid fields
4. If any field is invalid, move focus to the first invalid field
5. If all fields are valid, hide the form, populate `#confirmation-details` with a summary, show `#confirmation`, and move focus to `#confirmation`

```js
const form = document.getElementById('registration-form');
form.addEventListener('submit', (event) => {
  event.preventDefault();

  const fields = [
    { el: nameInput, validate: validateName },
    { el: emailInput, validate: validateEmail },
    { el: phoneInput, validate: validatePhone },
    { el: studentIdInput, validate: validateStudentId },
    { el: eventSelect, validate: validateEvent },
  ];

  let firstError = null;

  fields.forEach(({ el, validate }) => {
    const error = validate(el.value);
    if (error) {
      showError(el, error);
      if (!firstError) firstError = el;
    } else {
      clearError(el);
    }
  });

  if (firstError) {
    firstError.focus();
    return;
  }

  // All valid — show confirmation
  const confirmation = document.getElementById('confirmation');
  const details = document.getElementById('confirmation-details');
  details.textContent = `${nameInput.value.trim()} has been registered for ${eventSelect.options[eventSelect.selectedIndex].text}.`;
  form.hidden = true;
  confirmation.hidden = false;
  confirmation.focus();
});
```

---

## CSS requirements

In `labs/lab07/style.css`:
- `.error-msg` should be visually distinct (red text, small font) — but also non-empty spans should have an icon or prefix so color is not the only indicator
- `.input-error` should show a visible border change on the input
- `:focus-visible` should show a clear focus ring on all interactive elements
- The form should be readable on mobile (single column) and centered on desktop

---

## Testing requirements

Test each of the following manually:

- [ ] Submit with all fields empty → errors appear on all required fields
- [ ] Focus moves to first invalid field on failed submit
- [ ] Fix all errors and resubmit → confirmation appears and receives focus
- [ ] Tab through the entire form using keyboard only — all fields reachable
- [ ] Check that error spans are announced by enabling a screen reader (VoiceOver on Mac, NVDA on Windows)
- [ ] Phone field: leave blank → no error; enter "555" → error appears

---

## Deliverable

In `labs/lab07/`:
- `index.html`
- `lab07.js`
- `style.css`
- `notes.md`

Commit at least three times. Push and deploy.

Submit to Canvas: live URL, repo URL, notes.md link.

---

## Process reflection (in notes.md)

Answer in 4–6 sentences:
- What is the difference between `input` and `blur` events, and why is `blur` more appropriate for validation timing?
- How does `aria-describedby` connect an error message to an input, and why does this matter?
- What happened to focus when a form error appeared? What did you need to do to return focus correctly?

---

## Rubric

| Criterion | Excellent (4) | Proficient (3) | Developing (2) | Incomplete (1) |
|-----------|--------------|----------------|----------------|----------------|
| **Validation logic** | All five validators correct including edge cases (optional phone, student ID format) | Four validators correct | Two or three correct | One or zero |
| **Error display** | Errors shown with correct text; `aria-invalid` set; cleared when fixed | Errors shown; ARIA not updated | Errors shown but not cleared | No error display |
| **Validation timing** | Blur validation on name/email; full validation on submit; first invalid field focused | Submit validation only | Partial submit validation | No event handling |
| **Confirmation flow** | Form hidden; confirmation shown with correct summary; focus moved to confirmation | Confirmation shown; no focus management | Some success handling | No confirmation |
| **Accessibility** | `aria-describedby`, `aria-live`, `aria-invalid`; keyboard navigable; color not only error indicator | Most ARIA present; keyboard works | Some ARIA | No ARIA |
| **Reflection** | Specific; all three prompts addressed | Two prompts | Vague | Missing |
