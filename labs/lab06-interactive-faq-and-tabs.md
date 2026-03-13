# Lab 06 – Interactive FAQ and Tabs

## Purpose

DOM manipulation is most visible when it controls what users can see. This lab focuses on two of the most common interface patterns — accordions and tabs — and asks you to implement them correctly using class toggling, event delegation, and accessible markup.

## Skills practiced

- Selecting elements with `querySelector` and `querySelectorAll`
- Toggling CSS classes with `classList.toggle`, `.add`, `.remove`
- Using event delegation on a parent element
- Reading `event.target` and traversing the DOM with `.closest()`
- Adding `aria-expanded` and `aria-controls` for accessible disclosure patterns
- Creating tab panels with correct ARIA roles

## What you're building

A **Campus Services** help page with two sections:
1. An **accordion FAQ** — clicking a question reveals the answer; clicking again collapses it; only one answer is open at a time
2. A **tabbed panel** — three tabs that switch between content panels; only the active panel is visible

---

## Part 1: Accordion FAQ

### HTML

Create `labs/lab06/index.html`. The FAQ section should follow this structure:

```html
<section class="faq">
  <h2>Frequently Asked Questions</h2>

  <div class="faq-item">
    <button class="faq-question" aria-expanded="false" aria-controls="faq-answer-1">
      How do I register for classes?
    </button>
    <div class="faq-answer" id="faq-answer-1" hidden>
      <p>Log in to the student portal and navigate to Registration...</p>
    </div>
  </div>

  <div class="faq-item">
    <button class="faq-question" aria-expanded="false" aria-controls="faq-answer-2">
      Where is the financial aid office?
    </button>
    <div class="faq-answer" id="faq-answer-2" hidden>
      <p>The financial aid office is located in the Shepherd Union...</p>
    </div>
  </div>

  <!-- Add at least 4 more FAQ items total (6 minimum) -->
</section>
```

Key attributes:
- `aria-expanded="false"` on the button — updated by JavaScript when opened
- `aria-controls` points to the `id` of the answer panel
- `hidden` attribute on answer panels — CSS will reveal them when the `hidden` attribute is removed

### CSS

```css
.faq-answer[hidden] {
  display: none;
}

.faq-question[aria-expanded="true"] {
  /* style the open state — e.g., different background, arrow rotation */
}
```

### JavaScript

Write a function `initFaq(faqContainer)` that:

1. Adds a single `click` listener to `faqContainer` (event delegation)
2. When a click is detected, checks if `event.target.matches('.faq-question')`
3. Finds all other open questions and closes them (removes the `hidden` attribute trick: toggle `hidden` on the answer div, set `aria-expanded` to the correct string)
4. Toggles the clicked question open or closed

Specifically, for the clicked button:
- Toggle `aria-expanded` between `"true"` and `"false"` (as strings — ARIA attributes are always strings)
- Toggle the `hidden` attribute on the associated answer panel (use `answerEl.hidden = !answerEl.hidden` or `toggleAttribute('hidden')`)

For all *other* questions: set `aria-expanded="false"` and `hidden = true` (only one answer open at a time).

---

## Part 2: Tabbed panel

### HTML

```html
<section class="tabs-section">
  <h2>Campus Resources</h2>

  <div class="tab-list" role="tablist">
    <button role="tab" aria-selected="true" aria-controls="panel-library" id="tab-library">
      Library
    </button>
    <button role="tab" aria-selected="false" aria-controls="panel-gym" id="tab-gym">
      Recreation Center
    </button>
    <button role="tab" aria-selected="false" aria-controls="panel-dining" id="tab-dining">
      Dining
    </button>
  </div>

  <div role="tabpanel" id="panel-library" aria-labelledby="tab-library">
    <h3>Library Hours</h3>
    <p>Monday–Friday: 7am–10pm...</p>
  </div>

  <div role="tabpanel" id="panel-gym" aria-labelledby="tab-gym" hidden>
    <h3>Recreation Center</h3>
    <p>Open daily 6am–11pm...</p>
  </div>

  <div role="tabpanel" id="panel-dining" aria-labelledby="tab-dining" hidden>
    <h3>Dining Locations</h3>
    <p>Three dining halls on campus...</p>
  </div>
</section>
```

### JavaScript

Write a function `initTabs(tabListContainer)` that:

1. Adds a `click` listener to `tabListContainer`
2. When a `[role="tab"]` button is clicked:
   - Sets `aria-selected="false"` on all tab buttons
   - Hides all tab panels (set `hidden = true`)
   - Sets `aria-selected="true"` on the clicked tab
   - Shows the panel whose `id` matches `event.target.getAttribute('aria-controls')` (remove `hidden`)

### CSS

```css
[role="tabpanel"][hidden] {
  display: none;
}

[role="tab"][aria-selected="true"] {
  /* active tab styling */
}
```

---

## Part 3: Call both initializers

At the bottom of your script (or in a `DOMContentLoaded` handler):

```js
initFaq(document.querySelector('.faq'));
initTabs(document.querySelector('.tab-list'));
```

---

## Testing requirements

Test each behavior manually:

**Accordion:**
- [ ] Clicking a question opens its answer
- [ ] Clicking the same question again closes it
- [ ] Opening a second question automatically closes the first
- [ ] `aria-expanded` reflects the correct state in the Elements panel
- [ ] All buttons are keyboard-reachable and activatable with Enter/Space

**Tabs:**
- [ ] Clicking each tab shows that panel and hides the others
- [ ] `aria-selected` updates correctly in the Elements panel
- [ ] All tabs are keyboard-reachable

---

## Deliverable

In `labs/lab06/`:
- `index.html`
- `lab06.js`
- `style.css`
- `notes.md`

Commit at least twice (after each component). Push and deploy.

Submit to Canvas: live URL, repo URL, notes.md link.

---

## Process reflection (in notes.md)

Answer in 4–6 sentences:
- Why is event delegation better than adding a click listener to each individual button?
- What does `aria-expanded` communicate, and to whom?
- What would break if you used `display: none` in JavaScript directly instead of toggling the `hidden` attribute and controlling visibility through CSS?

---

## Rubric

| Criterion | Excellent (4) | Proficient (3) | Developing (2) | Incomplete (1) |
|-----------|--------------|----------------|----------------|----------------|
| **Accordion behavior** | Open/close works; only one panel open at a time; `aria-expanded` accurate | Open/close works; multiple panels can open simultaneously | Open works; close doesn't | Not functional |
| **Tab behavior** | Tabs switch panels correctly; all three panels reachable; `aria-selected` accurate | Tabs switch; ARIA not updated | Partially working | Not functional |
| **ARIA attributes** | `aria-expanded`, `aria-controls`, `aria-selected`, `role="tab"`, `role="tabpanel"` all present and accurate | Most ARIA present | Some ARIA present | No ARIA |
| **Event delegation** | One listener per component on a parent; `event.target.matches()` or `.closest()` used | Two listeners per component | Individual listeners on each button | No event delegation |
| **Keyboard accessibility** | All interactive elements reachable by Tab and activatable by Enter/Space | Most reachable | Partially reachable | Not tested |
| **Reflection** | Specific; addresses all three prompts | Two prompts addressed | Vague | Missing |
