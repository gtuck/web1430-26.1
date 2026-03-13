# Quiz Alignment Document

This document maps each quiz and exam to the week it is administered, the textbook chapter(s) it covers, the specific learning outcomes it addresses, and the number of questions by type.

Use this document to verify assessment coverage, identify outcome gaps, or revise quiz content efficiently.

---

## Summary table

| Assessment | Week | Chapter(s) | Learning Outcomes | Questions |
|-----------|------|-----------|-------------------|-----------|
| Quiz 1 | 01 | Ch 1 | Browser internals, DevTools | 10 MC/TF + 2 application |
| Quiz 2 | 03 | Ch 3 | JS syntax, types, debugging | 10 MC/TF + 2 application |
| Quiz 3 | 05 | Ch 4–5 | Control flow, arrays, objects | 10 MC/TF + 2 application |
| Quiz 4 | 07 | Ch 6–7 | DOM, events, forms | 10 MC/TF + 2 application |
| Midterm | 08 | Ch 1–7 | All outcomes through Week 07 | 30 MC/TF + 5 application |
| Quiz 5 | 09 | Ch 9 | Fetch, async/await, failure states | 10 MC/TF + 2 application |
| Quiz 6 | 10 | Ch 10 | localStorage, sessionStorage, state | 10 MC/TF + 2 application |
| Quiz 7 | 12 | Ch 11–12 | Modules, Vite, Vue basics | 10 MC/TF + 2 application |
| Quiz 8 | 14 | Ch 9–12 | Integration: async + storage + modules + Vue | 10 MC/TF + 2 application |
| Final Exam | 15 | Ch 1–12 | Cumulative; weighted toward Ch 9–12 | 40 MC/TF + 8 application |

---

## Quiz 1 — Week 01

**Covers:** Chapter 1 – Thinking in the Browser
**Administered:** End of Week 01
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Use browser developer tools to inspect, debug, and improve client-side code
- Understand the client-side layer model (HTML/CSS/JS separation)

**Topic checklist:**
- [ ] HTTP request/response cycle (status codes)
- [ ] DOM construction from HTML parsing
- [ ] Render tree (DOM + CSSOM)
- [ ] Why `<script>` placement matters
- [ ] `defer` vs `async` distinction
- [ ] DevTools: Elements, Console, Network tabs

**Sample application questions:**
- *"A developer places `<script src="app.js"></script>` inside `<head>` without any attributes. What is the likely consequence? (A) The script is ignored. (B) HTML parsing pauses until the script downloads and executes. (C) The script runs after all CSS is loaded. (D) The script runs asynchronously."*
- *"A student inspects their page in DevTools Elements panel and sees a `<p>` element that does not exist in their HTML source file. What is the most likely explanation?"*

---

## Quiz 2 — Week 03

**Covers:** Chapter 3 – JavaScript Syntax, Values, and Expressions
**Administered:** End of Week 03
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Write readable JavaScript using variables, control flow, functions, arrays, objects, and modules

**Topic checklist:**
- [ ] `const` vs `let` (and why not `var`)
- [ ] Primitive types: string, number, boolean, null, undefined
- [ ] `typeof` output (including `typeof null === 'object'` quirk)
- [ ] `===` vs `==` (strict vs loose equality)
- [ ] Type coercion with `+` operator
- [ ] Template literals
- [ ] `NaN` and `isNaN()`

**Sample application questions:**
- *"What does `console.log(1 + '2')` output? (A) 3  (B) '12'  (C) NaN  (D) A TypeError"*
- *"A developer writes `if (userAge == '28')`. What is the risk? (A) It always returns false. (B) It uses type coercion and may match unexpected values. (C) The `if` statement is missing braces. (D) It throws a SyntaxError."*

---

## Quiz 3 — Week 05

**Covers:** Chapter 4 – Decisions, Loops, and Reusable Logic; Chapter 5 – Modeling Information in JavaScript
**Administered:** End of Week 05
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Write readable JavaScript using variables, control flow, functions, arrays, objects, and modules

**Topic checklist:**
- [ ] `if/else`, `switch` statements
- [ ] `for` and `while` loops
- [ ] Function declarations vs expressions vs arrow functions
- [ ] Return values and pure functions
- [ ] Block scope vs function scope
- [ ] Array literals, index access, `.length`
- [ ] `.map()`, `.filter()`, `.find()`, `.forEach()`
- [ ] Object literals, dot notation, destructuring
- [ ] `JSON.stringify` / `JSON.parse`

**Sample application questions:**
- *"Given `const prices = [10, 25, 5, 40]`, which expression produces `[20, 50, 10, 80]`? (A) `prices.filter(p => p * 2)` (B) `prices.map(p => p * 2)` (C) `prices.forEach(p => p * 2)` (D) `prices.find(p => p * 2)`"*
- *"What does `.filter()` return when no elements match the condition? (A) `null` (B) `undefined` (C) An empty array `[]` (D) `false`"*

---

## Quiz 4 — Week 07

**Covers:** Chapter 6 – The Document Object Model; Chapter 7 – Event-Driven Interfaces and Forms
**Administered:** End of Week 07
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Manipulate the DOM to create interactive interfaces that respond to user events
- Design and validate accessible forms that provide clear feedback and error recovery

**Topic checklist:**
- [ ] `querySelector` vs `querySelectorAll`
- [ ] `createElement`, `textContent` vs `innerHTML` (XSS risk)
- [ ] `classList.add`, `.remove`, `.toggle`
- [ ] `addEventListener` (click, submit, change, input, blur)
- [ ] `event.preventDefault()`
- [ ] `event.target` vs `event.currentTarget`
- [ ] Event delegation
- [ ] `aria-invalid`, `aria-describedby`, `aria-live`

**Sample application questions:**
- *"A developer writes `el.innerHTML = userInput`. What security risk does this introduce? (A) Memory leaks. (B) Cross-site scripting (XSS) — the user's input may contain executable script tags. (C) The element's existing children are preserved unnecessarily. (D) `innerHTML` is slower than `textContent`."*
- *"Which ARIA attribute should be set to `true` on a form input when it fails validation? (A) `aria-required` (B) `aria-live` (C) `aria-invalid` (D) `aria-disabled`"*

---

## Midterm Exam — Week 08

**Covers:** Chapters 1–7 (cumulative through Week 07)
**Administered:** Week 08
**Format:** 30 multiple-choice / true-false + 5 application questions
**Time limit:** 60 minutes

**Learning outcomes addressed:** All outcomes through Week 07:
- Browser DevTools and the render pipeline
- JS syntax, types, control flow, functions
- Data modeling with arrays and objects
- DOM manipulation
- Event handling and accessible form design

**Weight distribution:** Approximately 15 questions on HTML/CSS/browser (Ch 1–2), 10 questions on JS fundamentals (Ch 3–5), 10 questions on DOM and events (Ch 6–7).

---

## Quiz 5 — Week 09

**Covers:** Chapter 9 – Fetch, JSON, and Remote Data
**Administered:** End of Week 09
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Exchange data with external services using JSON and the Fetch API

**Topic checklist:**
- [ ] Why async exists (single-threaded JavaScript)
- [ ] Promise states: pending, fulfilled, rejected
- [ ] `async/await` syntax
- [ ] `fetch()` return value and the two-step pattern (`.json()`)
- [ ] `response.ok` check
- [ ] `try/catch/finally`
- [ ] Four UI states: loading, success, error, empty
- [ ] `aria-live` for async content

**Sample application questions:**
- *"After `const res = await fetch(url)`, a developer immediately calls `const data = await res.json()`. What is missing? (A) `await` should not be used with `.json()`. (B) The developer should check `res.ok` before calling `.json()` to handle HTTP errors. (C) `res.json()` does not return a Promise. (D) Nothing is missing."*

---

## Quiz 6 — Week 10

**Covers:** Chapter 10 – Storage, Preferences, and State
**Administered:** End of Week 10
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Persist client-side state with local storage and session storage when appropriate

**Topic checklist:**
- [ ] `localStorage` vs `sessionStorage` (persistence scope)
- [ ] `setItem`, `getItem`, `removeItem`, `clear`
- [ ] Storage stores strings only — JSON round-trip required for objects
- [ ] Boolean-as-string gotcha (`"false"` is truthy)
- [ ] Storage limits (~5 MB per origin)
- [ ] When to use each storage type

**Sample application questions:**
- *"A developer stores `localStorage.setItem('active', false)` and later reads `if (localStorage.getItem('active'))`. What happens? (A) The condition is false, as expected. (B) The condition is true, because `localStorage` stores the string `'false'`, which is truthy. (C) A TypeError is thrown. (D) `getItem` returns `null`."*

---

## Quiz 7 — Week 12

**Covers:** Chapter 11 – Modules, npm, and Vite; Chapter 12 – Introductory Component-Based Development
**Administered:** End of Week 12
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Write readable JavaScript using modules
- Apply introductory component-based thinking with a modern JavaScript framework

**Topic checklist:**
- [ ] Named exports vs default exports
- [ ] Import syntax with relative paths
- [ ] Module scope (no global leakage)
- [ ] What Vite provides: dev server, HMR, build step
- [ ] Vue SFC structure: `<script setup>`, `<template>`, `<style>`
- [ ] `ref()` and `.value`
- [ ] Template directives: `v-for`, `v-if`, `v-bind`, `v-on`
- [ ] `defineProps`

**Sample application questions:**
- *"In a Vue `<script setup>` component, a developer declares `const count = ref(0)` but writes `count = count + 1` in a click handler. What is the problem? (A) `ref` values are read-only. (B) `ref` values must be updated via `.value`: `count.value = count.value + 1`. (C) Arrow functions cannot modify reactive values. (D) `ref` is not available in `<script setup>`."*

---

## Quiz 8 — Week 14

**Covers:** Integration review — Chapters 9–12 (async, storage, modules, Vue)
**Administered:** End of Week 14
**Format:** 10 multiple-choice / true-false + 2 application questions

**Learning outcomes addressed:**
- Exchange data with external services using JSON and the Fetch API
- Persist client-side state with local storage and session storage
- Write readable JavaScript using modules
- Apply introductory component-based thinking with a modern JavaScript framework

**Topic checklist:**
- [ ] Lighthouse score categories and what affects each
- [ ] Common accessibility failures (missing alt, unlabeled inputs, low contrast)
- [ ] GitHub Pages deployment steps
- [ ] Props-down / events-up pattern in Vue
- [ ] `defineEmits` and `v-model` on components
- [ ] `computed()` for derived state

---

## Final Exam — Week 15

**Covers:** Chapters 1–12 (cumulative); weighted toward Chapters 9–12
**Administered:** Week 15
**Format:** 40 multiple-choice / true-false + 8 application questions
**Time limit:** 90 minutes

**Learning outcomes addressed:** All 10 course learning outcomes.

**Weight distribution:**
- Ch 1–2 (browser, HTML/CSS): ~8 questions
- Ch 3–7 (JS fundamentals, DOM, events): ~12 questions
- Ch 9–10 (async, storage): ~10 questions
- Ch 11–12 (modules, Vue): ~10 questions
- Application questions: 8 code-reading or scenario-based, spanning all topic areas

---

## Coverage gaps

| Learning Outcome | Directly assessed in quiz? | Notes |
|-----------------|---------------------------|-------|
| Browser DevTools / debugging | Quiz 1, Midterm | Lab 01, Lab 03 provide practice |
| Responsive semantic HTML | Midterm only | Assignment 1 is the primary assessment vehicle |
| Readable JavaScript | Quizzes 2–4, Midterm, Final | Strong coverage |
| DOM manipulation | Quiz 4, Midterm | Lab 06 and Assignment 3 provide practice |
| Accessible form design | Quiz 4, Midterm | Lab 07 dedicated; stronger in labs than quizzes |
| Fetch / JSON / APIs | Quiz 5, Quiz 8, Final | Strong coverage |
| localStorage / state | Quiz 6, Final | Only one dedicated quiz; Lab 09 and Project 2 carry more weight |
| Component-based thinking | Quiz 7, Quiz 8, Final | Coverage adequate given two weeks of Vue |
| Git / GitHub workflow | Not directly quizzed | Assessed through commit history on all submissions |
| Plan, build, test, present | Not quizzed | Assessed through project milestones and rationale documents |
