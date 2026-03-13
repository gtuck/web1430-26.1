# Lab 01 – Inspecting the Web

## Purpose

The browser is a tool you can look inside. This lab builds the habit of using DevTools to understand what a page is actually made of — not just what it looks like — and to connect what you see in the panels to the concepts from Chapter 1.

## Skills practiced

- Opening and navigating Chrome/Firefox DevTools
- Reading the DOM tree in the Elements panel
- Identifying semantic and non-semantic HTML elements
- Reading error and log output in the Console panel
- Observing HTTP requests in the Network panel
- Running simple JavaScript expressions in the Console

## What you're building

A written inspection report and a small annotated screenshot set documenting what you find inside two live websites. You will also write and run three JavaScript expressions in the Console and record the results.

---

## Part 1: Elements panel

Choose **two** real websites you use regularly (news site, university site, streaming service, etc.). For each site:

### 1.1 Open DevTools

Press F12 (Windows/Linux) or Cmd+Option+I (Mac). Click the **Elements** tab.

### 1.2 Find five elements

Expand the DOM tree and locate five HTML elements on the page. For each element record:
- The tag name
- Whether it is **semantic** (describes meaning: `<nav>`, `<main>`, `<article>`, `<header>`, `<footer>`, `<section>`, `<button>`, `<h1>–<h6>`) or **non-semantic** (`<div>`, `<span>`)
- What content or purpose it contains

Write your findings in your `notes.md` file (see deliverable section).

### 1.3 Edit text live

Double-click on a text node in the Elements panel and change it. Take a screenshot showing your edit. Note: this only changes your local view — the server is not affected.

### 1.4 Identify the page structure

Answer in your notes:
- Is there a `<main>` element? An `<h1>`? A `<nav>`?
- Are images using `alt` attributes? Right-click an image element and look for the `alt` attribute in the panel.

---

## Part 2: Console panel

Click the **Console** tab. For each site, type the following expressions, press Enter, and record what they return:

1. `document.title`
2. `document.querySelectorAll('a').length`
3. `document.querySelectorAll('img[alt=""]').length` — (images with empty alt text; any number above 0 is a potential accessibility issue)

Take a screenshot of your Console session showing the three results.

In your notes, explain what each expression means and what the result tells you about the page.

---

## Part 3: Network panel

Click the **Network** tab. Reload the page (the Network tab must be open before reload to capture traffic).

Locate the **first request** at the top of the list (this is the HTML document request). Click it and examine the **Headers** tab in the detail panel. Record:

- The request URL
- The HTTP method (GET, POST, etc.)
- The status code (200, 301, 404, etc.)
- The Content-Type of the response

Look at the overall waterfall. Roughly how many requests does the page make to load fully? How large is the total page weight (shown at the bottom of the Network panel)?

---

## Part 4: Your own page

Open the `labs/lab00/index.html` file you built last week in Live Server.

1. Open DevTools → Elements panel. Is your HTML structure what you expect?
2. Open the Console. Type `document.querySelector('h1').textContent`. What does it return?
3. Try to intentionally produce a `TypeError` by typing `document.querySelector('p').foo.bar`. Read the error message. What information does it give you?

Take a screenshot of the error in the Console and record the error message text in your notes.

---

## Deliverable

Create `labs/lab01/notes.md` in your repository with the following sections:

```
# Lab 01 – Inspection Notes

## Site 1: [URL]
### Elements found (5)
| Tag | Semantic? | Purpose |
|-----|-----------|---------|
...

### Console results
...

### Network: first request
...

## Site 2: [URL]
(same structure)

## My page (lab00/index.html)
...

## Reflection
What surprised you? What does DevTools tell you that you couldn't learn by just looking at the page?
```

Include your screenshots in a `labs/lab01/screenshots/` folder and reference them in the notes file.

Commit everything with a meaningful message and push to GitHub.

Submit to Canvas: your GitHub repository URL and a direct link to `labs/lab01/notes.md`.

---

## Rubric

| Criterion | Excellent (4) | Proficient (3) | Developing (2) | Incomplete (1) |
|-----------|--------------|----------------|----------------|----------------|
| **Elements analysis** | Five elements per site with accurate semantic classification and purpose notes | Four elements, mostly accurate | Two or three elements, classification inconsistent | One element or missing |
| **Console expressions** | All three expressions run on both sites, results recorded and explained | Three expressions run, results recorded but not explained | One or two expressions recorded | No Console work |
| **Network observation** | First request details fully recorded for both sites; page weight noted | One site's request recorded with some details | Partial network data | No network work |
| **Own page inspection** | Error produced, message quoted and explained; textContent result correct | Error shown in screenshot, no explanation | Page opened in DevTools but no analysis | Not attempted |
| **Reflection** | Specific and honest; connects observation to chapter concepts | Addresses prompts | Vague or generic | Missing |
