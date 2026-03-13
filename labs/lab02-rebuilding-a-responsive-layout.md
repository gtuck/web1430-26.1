# Lab 02 – Rebuilding a Responsive Layout

## Purpose

Reading about semantic HTML and mobile-first CSS is not the same as writing it. This lab puts you in a constrained, low-stakes environment to practice the core skills from Chapter 2: choosing semantic elements deliberately, building a layout that works at every screen size, and validating your markup.

## Skills practiced

- Choosing semantic HTML elements over generic `<div>` containers
- Writing mobile-first CSS with `min-width` media queries
- Using Flexbox or CSS Grid for layout
- Connecting form labels to inputs
- Validating HTML at validator.w3.org
- Testing at narrow viewport widths

## What you're building

A responsive page for a fictional campus club — the **Wildcat Hiking Club** — that includes a site header with navigation, a featured announcement section, a two-column member spotlight grid (collapsing to one column on mobile), a simple contact form, and a footer. No JavaScript is required for this lab.

---

## Provided wireframe description

**Mobile (single column, top to bottom):**
1. Site header: club name + a hamburger menu icon (static, no JS needed)
2. Hero section: large heading, one-sentence tagline, a "Join Us" link styled as a button
3. Upcoming hike card: date, trail name, difficulty rating, and a short description
4. Member spotlight: three member cards (name + short bio), stacked vertically
5. Contact form: name, email, message fields + submit button
6. Footer: copyright line and three social links

**Desktop (min-width: 768px):**
- Member spotlight cards display in a three-column grid
- Contact form is centered with a max-width of 600px
- Header nav links display horizontally (no hamburger)

---

## Tasks

### Task 1: HTML structure (no CSS yet)

Create `labs/lab02/index.html`. Build the complete HTML for the page described above.

Requirements:
- Use `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<form>`, `<footer>` — use a semantic element wherever one fits.
- No `<div>` where a semantic element would work.
- Every form input must have a `<label>` connected via matching `for` and `id` attributes.
- Every image (if you include any) must have a meaningful `alt` attribute.
- Your `<h1>` should appear exactly once, in `<main>`.

Open the raw HTML (no CSS) in a browser. Does it read logically top to bottom? Can you tab through the navigation and form fields with your keyboard?

### Task 2: Mobile-first CSS

Create `labs/lab02/style.css`. Link it in the `<head>`.

Write base styles for the narrowest viewport first (assume 375px wide, no media queries needed for the base). Your base styles should produce a working, readable single-column layout.

Requirements for base styles:
- Reset box model: `*, *::before, *::after { box-sizing: border-box; }`
- Define at least five CSS custom properties in `:root` for color, spacing, and font size
- Style the header, navigation, hero section, cards, form, and footer
- The member cards should stack vertically

### Task 3: Responsive breakpoints

Add at least two `min-width` media queries:

```css
@media (min-width: 600px) {
  /* tablet: two-column card grid */
}

@media (min-width: 900px) {
  /* desktop: three-column card grid, horizontal nav */
}
```

Test by dragging the browser window narrower and wider, or using DevTools → Toggle Device Toolbar (the phone/tablet icon).

### Task 4: Validate and fix

Run your HTML through validator.w3.org (paste in the HTML source). Fix every error and warning. Take a screenshot showing a clean validation result (zero errors).

### Task 5: Accessibility check

Tab through your entire page using only the keyboard (no mouse). Every link and button should be reachable and visually highlighted when focused. If the focus ring is invisible, add:

```css
:focus-visible {
  outline: 2px solid var(--color-brand);
  outline-offset: 2px;
}
```

---

## Deliverable

In `labs/lab02/`:
- `index.html`
- `style.css`
- `notes.md` — your reflection (see below)
- `screenshot-validation.png` — validator.w3.org showing no errors
- `screenshot-mobile.png` — page at 375px width
- `screenshot-desktop.png` — page at 900px+ width

Deploy via GitHub Pages or Netlify. Commit and push with at least three commits showing incremental progress (HTML first, then base CSS, then responsive CSS).

Submit to Canvas: live URL, GitHub repo URL, and a link to `labs/lab02/notes.md`.

---

## Process reflection (in notes.md)

Answer these questions in 4–6 sentences total:
- Which semantic element choice was least obvious to you, and why did you choose it?
- What happened when you started CSS at 375px instead of desktop width?
- What error did the validator catch that you didn't notice yourself?

---

## Rubric

| Criterion | Excellent (4) | Proficient (3) | Developing (2) | Incomplete (1) |
|-----------|--------------|----------------|----------------|----------------|
| **Semantic HTML** | All sections use appropriate semantic elements; no `<div>` where a semantic element fits; labels connected to inputs | Most sections semantic; one or two missed opportunities | Some semantic elements present; divs used for most structure | No semantic elements beyond default |
| **Mobile-first CSS** | Base styles target narrow viewport; `min-width` queries add layout; custom properties defined | Base styles present; breakpoints work but not strictly mobile-first | CSS present but written desktop-first with overrides | Minimal or no CSS |
| **Responsive behavior** | Layout adapts correctly at 375px, 600px, and 900px; tested in DevTools | Adapts at two breakpoints | Partially responsive | Single fixed-width layout |
| **Validation** | Zero errors on validator.w3.org; screenshot provided | 1–2 minor errors | Several errors | Not validated |
| **Keyboard accessibility** | All interactive elements reachable and visually focused | Most reachable | Some reachable | Not tested |
| **Reflection** | Specific answers to all three prompts | Addresses two prompts | Vague or one prompt | Missing |
