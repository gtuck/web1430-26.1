# Chapter 2: HTML, CSS, and Progressive Enhancement

Semantic HTML and mobile-first CSS are not prerequisites you get through — they are the foundation every interactive interface is built on. This chapter gives you the habits that keep that foundation solid.

## What this chapter is really about

Before adding any JavaScript, you need a page that is meaningful, readable, and usable on its own. This chapter focuses on writing HTML that communicates structure and meaning, writing CSS that works at any screen size starting from the smallest, and understanding the principle of progressive enhancement — the idea that your page should work at every layer, even if higher layers are unavailable.

## Key ideas

**Semantic HTML** means choosing elements for what they mean, not how they look by default. A `<nav>` element tells the browser (and assistive technologies) that this is navigation. A `<main>` element marks the primary content. An `<article>` wraps content that is self-contained and could stand alone. Using the right element costs nothing and provides free accessibility, better SEO, and clearer code.

Key semantic elements and their purpose:
- `<header>` — introductory content for a page or section
- `<nav>` — a block of navigation links
- `<main>` — the dominant content of the page (one per page)
- `<section>` — a thematic grouping with a heading
- `<article>` — self-contained content (post, card, product listing)
- `<aside>` — content tangentially related to the main content
- `<footer>` — closing content for a page or section

**The CSS cascade** determines which rule wins when multiple rules target the same element. It works in this order: origin (browser defaults → author styles → user preferences), then specificity (inline > ID > class > element), then source order (later rules override earlier ones). Understanding specificity prevents the frustration of writing CSS that "doesn't work" — it is always working; it is just being overridden.

**Mobile-first responsive design** means writing CSS for the smallest viewport first and adding complexity as the screen gets wider using `min-width` media queries. This produces leaner stylesheets, forces you to prioritize content, and aligns with the reality that most web traffic is on mobile devices.

```css
/* Mobile styles first — no media query needed */
.card {
  padding: 1rem;
}

/* Then expand for larger screens */
@media (min-width: 768px) {
  .card {
    padding: 2rem;
    display: grid;
    grid-template-columns: 1fr 2fr;
  }
}
```

**Progressive enhancement** means building in three layers: (1) HTML content that works in any browser with no CSS; (2) CSS that improves presentation; (3) JavaScript that adds behavior. Each layer enhances the previous one — it never replaces it. A user whose JavaScript fails still gets a readable page.

## Mental model

Build your page as three separate concerns you add one at a time. First, write just the HTML. Open it in a browser with no CSS. Does the content make sense? Is it in a logical order? Can you navigate it with just a keyboard? If yes, you have a solid foundation. Now add CSS. Does it look right at 375px first? Now add JavaScript. Does the page still work if the JS file is missing?

## Working habits

- Validate your HTML at validator.w3.org before every submission. Fix every error.
- Test CSS at 375px viewport width before testing at 1440px. Start narrow.
- Check color contrast with a contrast ratio tool. Text on background must be at least 4.5:1 for normal text, 3:1 for large text.
- Use `<button>` for actions and `<a>` for navigation — never swap them.
- Connect form labels to their inputs with matching `for` and `id` attributes.

## Common mistakes

- Using `<div>` and `<span>` for everything. If a more specific semantic element exists, use it.
- Writing desktop-first CSS and overriding with `max-width` queries. This produces bloated, contradictory styles. Start mobile-first.
- Using `!important` to solve specificity problems instead of fixing specificity.
- Relying on JavaScript to show and hide content that should be structured differently in HTML.
- Placing `<div>` inside `<p>` or other elements that don't accept block children (causes browser correction that breaks your layout).
- Not testing at narrow viewport sizes. Layouts that "look fine" on a desktop monitor often break at 375px.

## Accessibility and UX note

Semantic HTML is free accessibility. A `<button>` is focusable, activatable with Enter and Space, and announced as a button by screen readers — for no extra effort. A `<div>` with a click handler is none of those things without significant extra work. Form `<label>` elements connected to their inputs mean that clicking the label focuses the input — a usability benefit for everyone, not just screen reader users.

Headings (`<h1>` through `<h6>`) define the document outline. Screen reader users often navigate by jumping between headings. An `<h1>` should appear once, early in `<main>`. Heading levels should reflect content hierarchy, not font size preferences — use CSS for visual size.

## Practice prompt

Build or refactor a simple page (a profile page, a product listing, or an article) with the following requirements:

1. Include `<header>`, `<nav>`, `<main>`, at least one `<section>` or `<article>`, and `<footer>`. Use no `<div>` where a semantic element would work.
2. Connect at least one form label to its input.
3. Write mobile-first CSS. Your base styles should look correct at 375px. Add at least one `min-width` media query for a wider layout.
4. Validate your HTML at validator.w3.org and fix all errors.

Write a short note explaining one decision you made about element choice and one decision you made about layout.

## Reflection

What changed about your HTML when you tried to avoid `<div>` elements? What happened to your CSS when you started from a narrow viewport instead of a wide one? Where in your CSS did you notice specificity causing unexpected results?

## Vocabulary

- **semantic element** — an HTML element that describes the meaning of its content
- **cascade** — the set of rules that determines which CSS declaration wins when multiple rules apply
- **specificity** — a weight assigned to a CSS selector that determines its priority over other selectors
- **inheritance** — CSS properties that flow from parent to child elements automatically
- **mobile-first** — a design and CSS strategy that starts with the smallest viewport and adds layout for larger screens
- **viewport** — the visible area of the browser window
- **media query** — a CSS rule that applies styles conditionally based on screen size or device capability
- **progressive enhancement** — building in layers so that each layer adds to, rather than replaces, the previous one

## Mini checklist

- I can name at least six semantic HTML elements and explain what each one communicates.
- I can explain how the CSS cascade resolves conflicts between two rules targeting the same element.
- I can write a mobile-first stylesheet with at least one `min-width` media query.
- I can connect a form label to its input and explain why this matters.
- I can validate my HTML and interpret the errors the validator returns.
