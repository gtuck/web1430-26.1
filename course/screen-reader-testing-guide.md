# Introduction to Screen Reader Testing

Screen readers are software tools that convert on-screen content to synthesized speech or Braille output, allowing people with visual impairments to navigate and use websites. Testing your work with a screen reader is the most direct way to experience what your HTML structure communicates — or fails to communicate — to users who cannot see the page.

This guide covers how to enable a screen reader, navigate with it, and evaluate whether your web pages pass a basic accessibility check.

---

## VoiceOver (Mac)

VoiceOver is built into every Mac. No installation is required.

### Enable and disable

| Action | Shortcut |
|--------|----------|
| Turn VoiceOver on/off | **Cmd + F5** |
| Open VoiceOver Utility (settings) | **Cmd + F5** (hold for 3 seconds, or go to System Settings → Accessibility → VoiceOver) |

When VoiceOver is on, your Mac will announce everything you interact with. Don't be alarmed — you can turn it off instantly with Cmd+F5.

### Basic navigation in the browser

VoiceOver uses a **cursor** that moves independently of the mouse. The primary modifier key is **Ctrl+Option** (abbreviated VO).

| What you want to do | Keys |
|---------------------|------|
| Move to next element | **VO + Right Arrow** |
| Move to previous element | **VO + Left Arrow** |
| Activate a link or button | **VO + Space** |
| Navigate by headings | **VO + Command + H** (next heading) |
| Open the rotor (landmark/heading navigator) | **VO + U**, then arrow keys to choose category |
| Stop reading | **Ctrl** |
| Read from current position | **VO + A** |

**The rotor** is the most useful tool for evaluating page structure. Press **VO + U**, then use the left/right arrow keys to select "Headings", "Links", "Form Controls", or "Landmarks". VoiceOver will list all items of that type on the page — letting you quickly check whether your heading structure is logical and your links have descriptive text.

### What to listen for on your own projects

1. **Page title** — VoiceOver announces the page title when you load a page. Is it descriptive?
2. **Headings** — Navigate by headings (VO+Cmd+H). Do the headings describe the sections? Are they in logical order (h1 → h2 → h3)?
3. **Links** — Are link labels descriptive? "Read more" fails; "Read more about Lab 07 requirements" passes.
4. **Buttons** — Does VoiceOver announce the button's purpose? A `<button>` with only an icon needs `aria-label`.
5. **Form fields** — Does VoiceOver announce the label when you focus each input? Inputs need associated `<label>` elements.
6. **Error messages** — After triggering a validation error, does VoiceOver announce the error? Check that `aria-live` regions are present and that `aria-describedby` connects inputs to their error elements.
7. **Live regions** — After an async data load, does VoiceOver announce the new content? `aria-live="polite"` on the results container handles this.

---

## NVDA (Windows)

NVDA (NonVisual Desktop Access) is a free, open-source screen reader for Windows.

### Install

1. Go to [nvaccess.org/download](https://www.nvaccess.org/download/)
2. Download and run the installer (it takes about 1 minute)
3. You can run NVDA from the system tray or start it from the Start menu

### Enable and disable

| Action | Method |
|--------|--------|
| Start NVDA | Ctrl+Alt+N (after install) or from Start menu |
| Quit NVDA | NVDA+Q, then Enter to confirm (NVDA key is Insert by default) |

### Basic navigation in the browser (Chrome/Edge recommended)

The primary modifier key is **Insert** (abbreviated NVDA).

| What you want to do | Keys |
|---------------------|------|
| Move to next element | **Tab** |
| Navigate by headings | **H** |
| Navigate to next landmark | **D** |
| Navigate by form controls | **F** |
| Navigate by links | **K** |
| Activate a link or button | **Enter** |
| Read current line | **NVDA + Up Arrow** |
| Stop reading | **Ctrl** |

In NVDA, pressing **H** in browse mode jumps to the next heading. This is the fastest way to evaluate your heading structure. Press **Shift+H** to go backward.

---

## What "passing" looks like

Use this checklist when testing any lab, assignment, or project with a screen reader:

### Structure
- [ ] The page title (visible in the browser tab) is descriptive and unique
- [ ] There is exactly one `<h1>` that describes the page's main topic
- [ ] Heading levels are hierarchical (no skipping from h1 to h4)
- [ ] Landmark regions are present: `<header>`, `<nav>`, `<main>`, `<footer>`

### Navigation
- [ ] All interactive elements (links, buttons, inputs) are reachable by Tab key
- [ ] Focus order matches the visual reading order
- [ ] Links have descriptive text (not "click here" or "read more")
- [ ] Buttons announce their purpose (have visible text or `aria-label`)

### Forms
- [ ] Every `<input>` has an associated `<label>` (announced when the field is focused)
- [ ] Required fields are communicated (via `required` attribute or `aria-required`)
- [ ] Error messages are associated with their fields via `aria-describedby`
- [ ] `aria-invalid="true"` is set on fields that fail validation
- [ ] Error containers have `aria-live="polite"` or `role="alert"` so errors are announced automatically

### Dynamic content
- [ ] After a fetch/async operation, new content is announced (via `aria-live` on the results container)
- [ ] Loading states are communicated (a visually hidden "Loading…" message in an `aria-live` region)
- [ ] Empty states are announced when a search returns no results

---

## Quick reference: common failures and fixes

| What screen reader says | Likely problem | Fix |
|------------------------|----------------|-----|
| "button" (nothing else) | Button has no label | Add text content or `aria-label="Describe action"` |
| "link" (nothing else) | Link has no text | Add descriptive text; if icon-only, add `aria-label` |
| Field name not announced | Input has no `<label>` | Add `<label for="inputId">` or `aria-label` |
| Error not announced | Error element has no `aria-live` | Add `aria-live="polite"` to the error container |
| New content not announced | Dynamic content lacks live region | Add `aria-live="polite"` to the container before content is inserted |
| Heading levels skip | h1 jumps to h3 | Fill in the missing level (h2) |

---

## Further resources

- **WebAIM Screen Reader User Survey** — real data on how screen reader users navigate the web: [webaim.org/projects/screenreadersurvey](https://webaim.org/projects/screenreadersurvey/)
- **WebAIM VoiceOver Guide** — detailed VoiceOver commands: [webaim.org/articles/voiceover](https://webaim.org/articles/voiceover/)
- **WebAIM NVDA Guide** — detailed NVDA commands: [webaim.org/articles/nvda](https://webaim.org/articles/nvda/)
- **ARIA Authoring Practices Guide (APG)** — patterns for accessible widgets: [w3.org/WAI/ARIA/apg](https://www.w3.org/WAI/ARIA/apg/)
