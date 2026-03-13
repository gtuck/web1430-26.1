# Instructional Design Review: WEB 1430 – Client Side Web Development

**Reviewer:** Claude (Instructional Design Analysis)
**Date:** March 2026 (Third revision)
**Scope:** Full course review — textbook, labs, lectures, assignments, projects, quizzes, starters, schedule, learning outcomes, syllabus, supplementary course documents
**Previous reports:** March 2026 initial draft; March 2026 second revision

---

## Executive Summary

WEB 1430 is a complete, professionally executed online learning experience ready for first delivery. All previously identified Priority 1 and Priority 2 deficiencies have been resolved since the second revision. The course now has substantive lecture notes for all 16 weeks, an expanded and corrected Chapter 1, resource-linked module overviews, a fully described exam format in the syllabus, application-level quiz questions across all assessments, a screen reader testing guide, a standalone course reflection document, differentiated assignments, and a problem-first project framing.

The course has no remaining critical or moderate gaps. The only open items are three optional Priority 3 enhancements — two supplementary textbook chapters and a dedicated localStorage assignment — which are appropriately deferred until after first delivery when student performance data is available to inform the decision.

**Overall verdict: Fully ready for delivery.**

---

## Section 1: Strengths

### 1.1 Coherent Course Narrative

The 15-week arc has a clear, defensible progression: browser fundamentals → semantic HTML/CSS → JavaScript syntax → control flow → data modeling → DOM → events/forms → design systems → async/Fetch → state persistence → modules → Vue → integration and deployment. Each layer builds on the previous one, and the placement of the midterm at Week 8 (after DOM and forms, before async) creates a natural integration checkpoint.

### 1.2 Textbook: Complete and Differentiated

All 12 chapters are written with topic-specific content throughout. Every chapter contains: a "What this chapter is really about" framing section, topic-specific key ideas with code examples, a concrete mental model, working habits, common mistakes, an accessibility note tied to the chapter's topic, a directed practice prompt, chapter-specific reflection questions, chapter-appropriate vocabulary, and a topic-specific mini checklist.

Chapter 1 (Thinking in the Browser) was expanded from 68 lines to approximately 170 lines. It now includes a step-by-step walkthrough of how a browser parses a small HTML document, an explanation of `defer` vs. `async` with before/after code examples, a description of the render tree and its relationship to JavaScript timing, and an expanded three-part practice prompt that requires students to inspect parsing behavior in DevTools rather than simply identifying elements.

### 1.3 Lectures: Substantive and Scaffolded

All 16 lecture files (Week 00 through Week 15) have been fully written with topic-specific content. Each file is 150–250 lines and contains: a specific "why this matters" framing for the week's topic, concrete learning targets, core concepts with code examples in named subsections, a list of common mistakes specific to the week, an accessibility connection tied to the week's topic, a step-by-step demo walkthrough, a focused practice prompt, and a bridge sentence connecting to the week's lab or assignment.

The syllabus now specifies that lectures are published as written notes in Canvas each week, to be read alongside the corresponding textbook chapter.

### 1.4 Labs: Concrete, Scaffolded, Accessible

All 14 labs have differentiated scenarios (Wildcat Hiking Club, Campus Services, Open Library Book Search, etc.), named skills, step-by-step tasks, manual testing checklists, and 4-level rubrics. Accessibility is embedded as a first-class requirement in every lab that involves interactivity. Lab 07 is dedicated entirely to accessible form validation; Lab 13 closes the course with a full Lighthouse audit cycle, now linked to the new Screen Reader Testing Guide.

Starter files (HTML shells, data arrays, function stubs) exist for Labs 00–10. The `starters/README.md` now includes full Vite scaffolding instructions for Labs 11 and 12 — exact commands, cleanup steps, and common troubleshooting — so the scaffolding step does not consume the first 20 minutes of those labs.

### 1.5 Assignments: Calibrated, Differentiated, and Distinct

All 6 assignments have distinct scenarios, requirements calibrated to their position in the course, specific function/component expectations, and rubrics with 4 performance levels and concrete descriptors. Every "Above baseline (stretch)" section now includes the sentence: *"Work in this section is reflected in the Excellent (4) column of the rubric."*

Assignment 5 (Modular Refactor) is now meaningfully differentiated from Lab 10 (Convert a Script Bundle into Modules). Lab 10 uses a provided product script; Assignment 5 uses the student's own code. Assignment 5 additionally requires a `constants.js` file for all magic strings and an `ARCHITECTURE.md` that diagrams the module dependency graph — neither of which is required in Lab 10.

### 1.6 Projects: Design-First, Milestone-Driven, Problem-First

All 3 projects include multi-milestone structures that prevent last-minute builds. Project 1 requires a written proposal before any code. Project 2 now opens with a problem-first scenario framing — three pre-code questions (who is this for? what do they need? what data solves it?) before API selection — and the Milestone 1 proposal template enforces problem statement before API choice. Vague problem statements are flagged for revision before building begins.

The Final Project requires a pitch, wireframes, a beta review, a final submission, and a course reflection — each graded separately.

### 1.7 Course Reflection: Visible and Standalone

The course reflection prompt has been extracted from the bottom of the Final Project brief into its own document (`course/course-reflection-prompt.md`), which includes the five prompts and a three-criterion rubric. It is now linked directly from both the Final Project brief and the Week 15 module overview with the instruction to read it before the Final Studio session. Its visibility now matches its instructional importance.

### 1.8 Accessibility Thread

Accessibility is woven throughout the course. It appears in the learning outcomes, in the mini checklist of every textbook chapter, in the rubric criteria of every lab, assignment, and project, in Lab 07 (accessible form validation), in Lab 13 (Lighthouse audit), and in the new `course/screen-reader-testing-guide.md`. The guide covers VoiceOver (Mac) and NVDA (Windows) with navigation commands, a structured passing checklist (structure, navigation, forms, dynamic content), and a common-failures reference table. It is linked from Lab 13 and the Final Project accessibility requirements.

### 1.9 Assessment Quality: Recall and Application

All 8 weekly quizzes, the midterm exam, and the final exam now include application-level questions alongside recall questions. Each quiz has 2 code-reading or scenario-based questions (e.g., *"What does `console.log(1 + '2')` output?"*, *"A developer writes `localStorage.setItem('active', false)` — what happens when they read it back?"*). The midterm has 3 application questions; the final has 3. A quiz alignment document (`course/quiz-alignment.md`) maps every assessment to its week, chapter(s), learning outcomes, question types, and sample application questions.

### 1.10 Module Integration

All 16 module overviews now include a Resources section with a direct link to the week's lecture file, a link to the relevant textbook chapter (or a contextual note for weeks without a chapter), and a time estimate. This significantly reduces navigation friction for asynchronous students who need to locate the right materials for each week.

### 1.11 Professional Practice Reinforcement

Git workflow (meaningful commits, public repositories, deployment links) is required on every submission. Separation of concerns is explicitly required in Assignments 2–5 and modeled in lab code. Named functions are required throughout. `innerHTML` with user-supplied data is prohibited and explained in Lab 06. These are professional standards presented as standards, not optional suggestions.

---

## Section 2: No Remaining Critical Issues

All issues previously classified as Priority 1 (critical, before first delivery) and Priority 2 (moderate, first revision cycle) have been resolved. The following table documents the resolution of each:

| Issue | Resolution |
|-------|-----------|
| Lectures are templates without content | All 16 lectures fully written with topic-specific content, code examples, demo walkthroughs, and practice prompts |
| Syllabus does not clarify lecture delivery model | "Lecture delivery" section added to syllabus |
| Chapter 1 underdeveloped (68 lines) | Expanded to ~170 lines with parsing walkthrough, defer/async, render tree |
| Module overviews lack resource links and estimates | All 16 overviews updated with lecture link, chapter link, time estimate |
| Final exam format not described | "Exams" section added to syllabus (format, scope, timing, weight split) |
| Quizzes assess recall only | 2 application questions added to each quiz; 3 each to midterm and final |
| No quiz alignment document | `course/quiz-alignment.md` created |
| No screen reader testing guide | `course/screen-reader-testing-guide.md` created and linked |
| Labs 11–12 scaffold instructions missing | Full Vite setup steps added to `starters/README.md` |
| Assignment 5 too similar to Lab 10 | `constants.js` and `ARCHITECTURE.md` now required in Assignment 5 |
| Project 2 API-first framing | Scenario section rewritten problem-first; proposal template enforces problem→API order |
| Course reflection prompt buried | Extracted to `course/course-reflection-prompt.md`; linked from project brief and Week 15 overview |
| Stretch-to-rubric connection unclear | Linkage sentence added to all 6 assignment stretch sections |

---

## Section 3: Remaining Items (Priority 3 — Post-Delivery)

These items are optional enhancements, not delivery blockers. They are deferred until after the first delivery when student performance data can inform prioritization.

### 3.1 Optional Chapter 13: Accessibility Synthesis

There is no textbook chapter dedicated to accessibility as a complete discipline — WCAG standards, ARIA authoring patterns, manual testing methodology, and contrast tools. The current course weaves accessibility throughout chapters and labs effectively, but a synthesis chapter would give students a single reference for the full picture.

**Deferral rationale:** The accessibility thread through existing materials is strong. A synthesis chapter is valuable but not urgently needed. If Lab 13 or Final Project outcomes show students struggling with accessibility breadth, this becomes Priority 1 for revision cycle 2.

### 3.2 Optional Chapter 14: Performance, Testing, and Deployment

There is no textbook chapter covering Lighthouse categories, image optimization, what `npm run build` produces, or deployment pipeline options. Students encounter these topics in Lab 13 and the Final Project without prior conceptual framing.

**Deferral rationale:** Lab 13 and the Week 14 lecture provide adequate scaffolding for first delivery. A chapter would improve retention and preparation; it is not required to run the course successfully.

### 3.3 Optional localStorage Assignment

`localStorage` is covered in Chapter 10, Lab 09, and both Project 2 and the Final Project, but has no dedicated graded assignment. Students who struggle with this topic have only one practice lab before applying it in Project 2.

**Deferral rationale:** If Project 2 scores show students consistently failing the persistence criteria, adding a localStorage assignment (or replacing Assignment 3 or 4 with one) becomes the right move. This decision is better made with delivery data than in advance.

### 3.4 Post-Delivery Evaluation

- **Survey students at Weeks 5 and 11** on workload, clarity, and confidence. Adjust time estimates in module overviews if Week 5 (arrays/objects + proposal) or Week 11 (modules + Assignment 5) consistently over-run.
- **Evaluate Vue pacing after first delivery.** If students consistently struggle with Assignment 6, consider expanding Vue coverage to Weeks 11–13 and shifting modules slightly.

---

## Section 4: Learning Outcome Alignment Audit

| Learning Outcome | Chapter(s) | Lab(s) | Assignment(s) | Project(s) | Quiz coverage | Status |
|---|---|---|---|---|---|---|
| Responsive semantic HTML | 2 | 02 | 1 | P1, FP | Q1, Midterm | Strong |
| Readable JavaScript | 3, 4, 5 | 03, 04, 05 | 2, 3 | P1 | Q2, Q3, Midterm | Strong |
| Browser DevTools / debugging | 1 | 01, 03 | — | — | Q1, Midterm | Moderate — no graded assignment |
| DOM manipulation | 6 | 06 | 3 | P1 | Q4, Midterm | Strong |
| Accessible form design | 7 | 07 | 2, 3 | FP | Q4, Midterm | Strong |
| Fetch / JSON / remote data | 9 | 08 | 4 | P2, FP | Q5, Q8, Final | Strong |
| localStorage / state | 10 | 09 | — | P2, FP | Q6, Final | Moderate — no dedicated assignment |
| Component-based thinking | 12 | 11, 12 | 6 | FP | Q7, Q8, Final | Moderate — two weeks of Vue |
| Git / GitHub workflow | 0 | 00 | All | All | — | Strong |
| Plan, build, test, present | All | All | Rationale | P1, P2, FP | — | Strong |

**Persistent gaps (acceptable for first delivery):**
- **Browser DevTools** — No dedicated graded assignment; addressed through Lab 01, Lab 03, and Lab 13.
- **localStorage** — No dedicated assignment; addressed through Lab 09 and both projects.
- **Component-based thinking** — Two-week Vue ramp (Weeks 12–13) before Assignment 6 is tight; monitor in delivery.

---

## Section 5: Overall Assessment

| Dimension | Rating | Change from Second Revision | Notes |
|---|---|---|---|
| Learning outcome clarity | Strong | — | Outcomes are action-verb, measurable, well-scoped |
| Curriculum sequence | Strong | — | Logical; minor compression risk at Vue introduction |
| Textbook content | Strong | — | All 12 chapters complete; Chapter 1 expanded |
| Lab specificity | Excellent | — | 14 labs with scenarios, tasks, rubrics, starters |
| Assignment differentiation | Excellent | — | 6 assignments calibrated; A5 differentiated from Lab 10 |
| Rubric quality | Excellent | — | 4-level rubrics with descriptors; stretch-to-rubric linkage added |
| Project structure | Excellent | — | Problem-first framing; milestone-driven; reflection extracted |
| Starter files | Strong | — | Labs 00–10 complete; Labs 11–12 scaffold instructions added |
| Assessment alignment | Strong | ↑ Was "Adequate" | Quiz alignment doc; application questions across all assessments |
| Lecture content | Strong | ↑↑ Was "Needs work" | All 16 lectures fully written with code, demos, and practice prompts |
| Quiz quality | Strong | ↑ Was "Adequate" | Application-level questions added to all quizzes and exams |
| Accessibility integration | Excellent | ↑ Was "Strong" | Screen reader guide added; linked from Lab 13 and Final Project |
| Module integration | Strong | ↑ Was "Adequate" | All overviews have resource links and time estimates |
| Course support documents | Strong | ↑↑ Not previously noted | quiz-alignment.md, screen-reader-testing-guide.md, course-reflection-prompt.md created |
| Tech stack relevance | Strong | — | Appropriate for 2026 front-end development |
| Portfolio integration | Strong | — | Live URLs, GitHub, and deployments throughout |

**Overall course readiness: Fully ready for delivery.**

All materials are sufficient for students to succeed. There are no delivery-blocking gaps. The three Priority 3 items are optional improvements that should be evaluated after first delivery, not before.

---

*Report updated March 2026 (third revision). Reflects full review of all source Markdown and JSON files following completion of Priority 1 and Priority 2 recommendations from the second revision.*
