# Chapter 7: Event-Driven Interfaces and Forms

The browser waits. It waits for clicks, keystrokes, form submissions, and scroll events. Your job is to describe what should happen in response to those moments — without assuming when they will occur.

## What this chapter is really about

This chapter teaches you how to listen for user interactions, respond to them appropriately, validate form input on the client side, and communicate clearly what happened. It also covers accessibility for interactive elements: making sure error messages are perceivable, associated with their fields, and delivered at the right moment.

## Key ideas

**Adding event listeners** — always use `addEventListener`, never inline HTML handlers:

```js
const btn = document.querySelector('#submit-btn');
btn.addEventListener('click', handleClick);

function handleClick(event) {
  console.log('Button clicked', event.target);
}
```

Avoid `onclick="handleClick()"` in HTML. It mixes behavior into markup, is harder to remove or replace, and only allows one handler per event.

**The event object** is passed automatically to your handler. Key properties:

```js
function handleSubmit(event) {
  event.preventDefault();         // stop the form from navigating to a new page
  console.log(event.target);      // the element that triggered the event
  console.log(event.type);        // 'submit', 'click', 'input', etc.
}
```

**Common events**:
- `click` — any element clicked
- `submit` — a form submitted (always call `event.preventDefault()`)
- `input` — fires on every keystroke inside an input
- `change` — fires when an input loses focus after its value changed (also for select/checkbox)
- `keydown` — fires when a key is pressed; check `event.key` for which key

**Reading form values**:

```js
const form = document.querySelector('#contact-form');
form.addEventListener('submit', (event) => {
  event.preventDefault();
  const name = form.querySelector('#name').value.trim();
  const email = form.querySelector('#email').value.trim();
  // validate and process
});
```

**Client-side validation** — check before trusting:

```js
function isValidEmail(email) {
  return email.includes('@') && email.includes('.');
}

function showError(inputEl, message) {
  const errorEl = document.querySelector(`#${inputEl.id}-error`);
  errorEl.textContent = message;
  inputEl.setAttribute('aria-invalid', 'true');
}

function clearError(inputEl) {
  const errorEl = document.querySelector(`#${inputEl.id}-error`);
  errorEl.textContent = '';
  inputEl.removeAttribute('aria-invalid');
}
```

**Event delegation** — instead of adding a listener to every item in a list, add one listener to the container and check `event.target`:

```js
const list = document.querySelector('#task-list');
list.addEventListener('click', (event) => {
  if (event.target.matches('.remove-btn')) {
    event.target.closest('li').remove();
  }
});
```

This works even for items added dynamically after the listener is set up.

## Mental model

The browser runs an event loop. It sits idle until something happens, then fires the appropriate event, runs any listeners registered for it, and returns to idle. Your code doesn't run continuously — it runs in short bursts, triggered by user actions.

This means you cannot predict *when* your handler will run. You cannot assume the user has filled in all fields. You cannot assume the user clicked buttons in the order you designed them. Validate everything. Handle every state — not just the happy path.

## Working habits

- Always call `event.preventDefault()` in form submit handlers. Without it, the page navigates away before your JavaScript runs.
- Validate on `submit`, not on every `input` keystroke (validating while the user is still typing is annoying). Use `blur` (focus leaving a field) for optional early validation.
- Separate validation logic from rendering logic. Write `isValidEmail(email)` separately from `showError(input, message)`.
- Use `<button type="button">` for buttons inside a form that are not meant to submit. Otherwise every button is a submit button by default.
- Log `event.target` when debugging to confirm which element triggered the event.

## Common mistakes

- **Using `onclick` HTML attributes**: hard to remove, only one per element, mixes concerns. Always use `addEventListener`.
- **Forgetting `event.preventDefault()` on form submit**: the page navigates and you lose all your work.
- **Adding a listener inside a loop**: if you add a listener to each of 100 items, you have 100 listeners. Use event delegation — one listener on the parent, check `event.target`.
- **Not connecting error messages to their inputs**: a visible error message below an input is useless to a screen reader user unless it is associated with the input via `aria-describedby`.
- **Showing validation errors before the user has a chance to type**: validate on `submit` or on `blur`, not immediately on `input`.
- **Reading input `.value` at page load**: the value is empty at load time. Always read `.value` inside a handler, not as a constant at the top of the file.

## Accessibility and UX note

Form errors must be **perceivable** (not just a color change), **associated with their field** (not just placed nearby), and **delivered at the right time** (not before the user has interacted with the field).

Use `aria-describedby` to connect an error message element to its input:

```html
<label for="email">Email</label>
<input id="email" type="email" aria-describedby="email-error">
<span id="email-error" class="error-msg" aria-live="polite"></span>
```

When you set `errorEl.textContent = 'Please enter a valid email'`, the `aria-live="polite"` attribute causes screen readers to announce the message automatically.

After a successful form submission, move focus to the confirmation message so keyboard and screen reader users know what happened:

```js
confirmationEl.focus();
```

## Practice prompt

Build a contact form with `name`, `email`, and `message` fields and a Submit button.

1. Add a `submit` listener that prevents default page navigation.
2. Validate: name must be non-empty, email must contain `@`, message must be at least 10 characters.
3. For each invalid field, set a visible error message in a `<span>` linked to that input with `aria-describedby`. Set `aria-invalid="true"` on the input.
4. Clear errors from valid fields.
5. If all fields are valid, hide the form and show a success message. Move focus to the success message.

Use `addEventListener` — no `onclick` attributes. Use `textContent` — no `innerHTML`.

## Reflection

What happened when you submitted the form without `event.preventDefault()`? How did you structure your validation so that error messages appear at the right time? What did you need to add to the HTML to make error messages audible to a screen reader?

## Vocabulary

- **event** — a signal that something happened in the browser (click, input, submit, etc.)
- **event listener** — a function registered to run when a specific event fires on a specific element
- **handler** — the function that runs in response to an event
- **event object** — the argument passed to a handler containing information about the event
- **preventDefault** — stops the browser's default behavior for an event (e.g., form submission navigating away)
- **submit** — the event fired when a form is submitted
- **input** — the event fired on every change to an input's value
- **change** — the event fired when an input loses focus after its value changed
- **validation** — checking that user input meets required criteria before processing it
- **aria-describedby** — an ARIA attribute that associates a description element with an input
- **aria-invalid** — an ARIA attribute that communicates to assistive technology that a field has an invalid value
- **event delegation** — attaching one listener to a parent element and checking `event.target` to handle events from children

## Mini checklist

- I can add an event listener with `addEventListener` and explain why I avoid `onclick` HTML attributes.
- I can prevent default form submission behavior with `event.preventDefault()`.
- I can read form input values inside a submit handler.
- I can write a validation function that returns true or false and use it to conditionally show an error message.
- I can connect an error message to its input using `aria-describedby`.
- I can use event delegation to handle events on dynamically added elements.
