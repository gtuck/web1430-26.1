# Instructional Design Review: WEB 1430 – Client Side Web Development

**Reviewer:** Claude (Instructional Design Analysis)
**Date:** March 2026
**Scope:** Full course review including textbook, labs, assignments, projects, schedule, learning outcomes, and syllabus

---

## Executive Summary

WEB 1430 has a strong conceptual skeleton: a sound learning progression, an authentic tech stack, consistent accessibility emphasis, and a portfolio-first workflow that serves students well beyond the course. However, the course materials as they currently exist are scaffolding rather than a finished product. The textbook chapters, labs, assignments, and projects are all built from nearly identical templates with placeholder-level content. Before the course is delivered to students, the individual documents need to be substantially differentiated and fleshed out. This report identifies those gaps in detail and provides prioritized, actionable recommendations.

---

## Section 1: Strengths

### 1.1 Coherent Conceptual Framework

The course opens with a unifying mental model — the web as layers (content, presentation, behavior, data) — and returns to it consistently. This is good instructional design: a single organizing idea that students can use to orient new knowledge throughout the semester.

### 1.2 Sound Learning Progression

The 16-week arc moves logically from browser fundamentals → semantic HTML/CSS → JavaScript syntax → control flow → data modeling → DOM → events → design systems → async/Fetch → state persistence → modules → Vue. Each topic builds on the prior one. The placement of the midterm at Week 8 as an integration checkpoint before the async pivot is well-considered.

### 1.3 Authentic Tech Stack

HTML5, CSS3, vanilla JavaScript, ES modules, Vite, and Vue represent a realistic, contemporary front-end skill set. Students who complete the course will have worked with the actual tools used in industry, not toy abstractions.

### 1.4 Portfolio-Oriented Assessment Design

Requiring live deployment URLs and GitHub repositories for every major submission is excellent practice. Students graduate with a demonstrable portfolio rather than a folder of graded files no employer will ever see.

### 1.5 Accessibility Thread

Accessibility is not a bolt-on topic; it appears in the stated learning outcomes, the rubric criteria for every lab and assignment, and the chapter notes. This is commendable and increasingly important in both industry and legal contexts.

### 1.6 Metacognitive Reflection Requirement

Asking students to submit a process reflection alongside every deliverable is pedagogically sound. It surfaces misconceptions, rewards effort and growth (not just correctness), and builds the habit of professional self-evaluation.

### 1.7 Grading Weights Favor Application

With projects at 30% and labs + assignments together at 40%, graded work skews toward doing rather than knowing. This aligns with the applied nature of the discipline.

---

## Section 2: Critical Issues

These issues must be addressed before the course is delivered. They represent gaps where students would be confused, under-served, or unable to complete tasks with the materials as written.

### 2.1 Textbook Chapters Are Undifferentiated Templates

**This is the most significant issue in the course.**

Every chapter (1–12) shares identical body content in the following sections:

- **Key ideas** — the same paragraph, word-for-word, in all 12 chapters
- **Mental model** — the same paragraph, word-for-word, in all 12 chapters
- **Working habits** — the same paragraph, word-for-word, in all 12 chapters
- **Common mistakes** — the same paragraph, word-for-word, in all 12 chapters
- **Accessibility and UX note** — the same paragraph, word-for-word, in all 12 chapters
- **Reflection** — the same question, word-for-word, in all 12 chapters
- **Vocabulary** — the same five terms (`semantics`, `enhancement`, `state`, `rendering`, `debugging`) in all 12 chapters
- **Mini checklist** — the same three bullets, word-for-word, in all 12 chapters

The only text that varies between chapters is the title, the one-sentence opening description, and a single practice prompt sentence that inserts the chapter topic name into a generic template (e.g., "Identify one part of the interface that depends on **fetch, json, and remote data**…").

**Concrete consequences for students:**

- A student reading Chapter 3 (JavaScript Syntax) will find vocabulary terms like *semantics* and *rendering* with no definition of *variable*, *operator*, *type coercion*, or *expression*.
- A student reading Chapter 9 (Fetch, JSON) will be told "the web is layered" and given the same checklist as Chapter 1, with no explanation of Promises, `async/await`, error handling, or JSON parsing.
- A student reading Chapter 12 (Vue) will encounter vocabulary that doesn't include *component*, *reactivity*, *props*, or *template*.

**Recommendation:** Each chapter must be written with topic-specific content throughout. At minimum, the following must be differentiated per chapter:
- Key ideas (concrete, chapter-specific technical concepts)
- Common mistakes (specific to that topic)
- Vocabulary (terms actually introduced in that chapter)
- Mini checklist (skills specific to that chapter's learning goals)
- Practice prompt (a concrete, directed task, not a fill-in-the-blank generic)

### 2.2 Labs Are Undifferentiated Templates

All 14 labs (Lab 00 through Lab 13) share identical content:

- **Purpose:** Always "a constrained practice space for the week's concepts" with a fixed emphasis line
- **Tasks:** The exact same 5 generic tasks in every lab
- **Deliverable:** Identical across all 14 labs
- **Rubric:** The same 4 generic bullets in every lab

A student opening Lab 00 (Local Setup and GitHub Workflow) receives no instructions for installing Node.js, configuring Git, creating a GitHub account, creating their repository, or connecting it to their local machine. They are told to "build the required interface or script in small increments" — but there is no interface specified, no script described, and no starter files provided.

Lab 08 (Build an API-Powered Viewer) is equally content-free. No API is suggested or provided, no data structure is described, no expected interface elements are identified.

**Recommendation:** Each lab needs:
- A specific scenario or starter context ("You are building a FAQ accordion for a fictional campus club")
- The specific skills to practice, named explicitly
- Concrete step-by-step tasks that guide students through the exercise without doing the work for them
- A grading rubric with performance-level descriptions (see Section 2.4)
- For Lab 00 specifically: a full setup walkthrough with OS-specific notes

### 2.3 Assignments Are Undifferentiated Templates

All 6 assignments share the same "What to build," requirements, submission instructions, and rubric bullet points. Only the summary paragraph and title differ.

**Concrete problem:** Assignment 1 (Responsive Content Page, due Week 2) lists "Readable JavaScript with named functions or modules" as a requirement — but JavaScript is not introduced until Week 3. A student following the course schedule cannot meet this requirement with the knowledge the course has provided at that point. Either the requirement must be removed from Assignment 1 or the schedule must be reordered.

Additionally, there is no meaningful differentiation between the requirements for Assignment 1 (HTML/CSS layout) and Assignment 6 (Reactive Vue Form Workflow). Both list "Semantic HTML, Responsive behavior, Accessible interaction patterns, Readable JavaScript with named functions or modules" — making it impossible for students to know what specifically distinguishes and elevates the later work.

**Recommendation:** Each assignment needs:
- A specific scenario, audience, or constraint that makes it unique
- Requirements that are calibrated to where students are in the course
- A "stretch" or "above baseline" section identifying what distinguishes good work from minimal work
- The JavaScript requirement removed from Assignment 1 (or appropriately scoped)

### 2.4 Rubrics Are Too Vague to Be Useful

Every lab and assignment uses the same rubric format:

```
- Functionality
- Code organization
- Accessibility and UX clarity
- Reflection quality
```

These are categories, not rubrics. A rubric requires:
- Performance levels (Excellent / Proficient / Developing / Beginning, or equivalent)
- Point values
- Descriptors that distinguish one level from another

Without descriptors, grading is entirely subjective, students cannot self-assess before submitting, and grading consistency across sections or over time is impossible.

**Recommendation:** Develop a master rubric template with 4 performance levels and point ranges for each criterion, then adapt it per assignment to include topic-specific descriptors. Even a simple 4×4 grid (4 criteria × 4 levels) would dramatically improve consistency and student clarity.

---

## Section 3: Moderate Issues

These issues do not block delivery but meaningfully reduce course effectiveness. They should be addressed in the first revision cycle.

### 3.1 No Starter Code or Example Files

Students are asked to build sophisticated things — API-powered viewers, reactive Vue forms, modular JavaScript refactors — with no starter files, no example code, and no model of what the finished product might look like. The "small loops" working habit described in every chapter is good advice, but it requires a starting point to loop from.

**Recommendation:** For each lab, provide at minimum:
- A minimal HTML/CSS shell to start from
- A README with the expected folder structure
- For later labs, a partially-completed starter that scaffolds the difficult parts while leaving the learning-critical parts for students to write

Consider creating a "gallery of examples" on the course site showing prior-semester work (with permission), so students have a concrete target.

### 3.2 Vue Introduction May Be Too Compressed

Weeks 12–13 introduce Vue: component thinking, props, state, templates, component communication, reactive forms, and derived state — all in two weeks. For a student coming from vanilla JavaScript, the Vue mental model shift (declarative vs. imperative, reactivity system, single-file components) is substantial. Two weeks leaves little room for confusion, debugging, or consolidation.

**Recommendation:** Consider one of:
- Moving the Vue introduction earlier (Week 10–11) and allowing three weeks total
- Narrowing the Vue scope to Composition API basics and simple component composition only, removing reactive forms and derived state from the required curriculum
- Providing a "Vue in 30 minutes" bridge reading that explicitly maps vanilla JS concepts students know to Vue equivalents

### 3.3 Debugging Is Under-Assessed

The learning outcome "Use browser developer tools to inspect, debug, and improve client-side code" appears in the syllabus and is referenced conceptually in chapters, but there is no lab or assignment specifically targeting debugging skills. Debugging is often where beginners spend most of their actual time, and it is a learnable, teachable skill.

**Recommendation:** Either Lab 03 (Console Exercises) or Lab 06 (Interactive FAQ) should include a debugging-specific component: provide intentionally broken code and ask students to identify, document, and fix the errors using DevTools. This directly assesses the stated learning outcome in a way the current labs do not.

### 3.4 No Explicit Peer Learning or Code Review

The course is fully asynchronous, which eliminates natural peer interaction. The only social artifact is a GitHub repository that other students might see — but there is no structured peer feedback mechanism.

**Recommendation:** Add one lightweight peer code review activity, ideally at Week 8 (Midterm Integration Week, which already functions as a studio week). Students swap repository links, run through a short checklist (Does it deploy? Is it accessible? Can you follow the code?), and write two sentences of feedback. This builds professional communication skills and gives students a low-stakes external perspective on their work.

### 3.5 Quiz Content Is Opaque

The Canvas package includes 10 QTI quiz files, but the course materials give no indication of what these quizzes assess, what format the questions use, or how they align to specific learning outcomes. With quizzes worth 10% of the grade, students and instructors need visibility into this coverage.

**Recommendation:** Add a `course/quiz-alignment.md` file that maps each quiz to the week, chapter, and 2–3 specific learning outcomes it covers. This also serves as a tool for maintaining assessment alignment if the course is revised.

### 3.6 Week 00 Orientation Is Under-Specified

The orientation week is critical for setting up the entire course workflow (GitHub, local environment, Canvas), yet Lab 00 gives students the same 5 generic tasks as every other lab. Students who struggle with setup in Week 00 often fall irreversibly behind.

**Recommendation:** Expand Lab 00 into a proper setup guide with:
- Step-by-step Git and GitHub configuration (with screenshots or a linked video)
- Node.js and VS Code installation instructions
- Repository naming conventions and required folder structure
- A "smoke test" — a specific first commit to verify everything is working
- A troubleshooting FAQ for the 4–5 most common setup problems

---

## Section 4: Minor Issues and Suggestions

### 4.1 Vocabulary Lists Should Be Chapter-Specific

Every chapter lists the same five vocabulary terms: *semantics, enhancement, state, rendering, debugging*. A chapter on arrays and objects should introduce *array, index, method, iteration, destructuring*. A chapter on Fetch should introduce *promise, async, await, response, JSON*. Vocabulary that doesn't change between chapters provides no learning value.

### 4.2 Reflection Prompts Are Identical Across Chapters

Every chapter ends with: "What did you assume the browser was doing automatically that actually depends on deliberate authoring? Where can you make your intent more visible in HTML, CSS, or JavaScript?"

This is a good prompt for Chapter 1. By Chapter 9 (Fetch/JSON), students need a reflection prompt that surfaces thinking about asynchronous mental models, error states, and user feedback during loading. Generic prompts lead to generic reflections.

### 4.3 Practice Prompts Are Not Specific Enough

The practice prompt in each chapter uses the template: "Identify one part of the interface that depends on **[chapter topic]** and explain what the browser needs…" This is too open-ended to be actionable. Students need a concrete context, not a meta-instruction to find their own context.

**Example improvement for Chapter 6 (DOM):**
> *"Starting from the provided FAQ starter page, write JavaScript that toggles the visibility of each answer when its question heading is clicked. Use `querySelector`, `addEventListener`, and `classList.toggle`. Explain in a comment why you selected elements the way you did."*

### 4.4 No Explicit Error Handling Instruction for Fetch

Assignment 4 (API Data Story) requires "error handling" but Chapter 9's content (as currently written) does not specifically address error handling patterns for `fetch`. Students will encounter `try/catch`, `.catch()`, HTTP status codes, and network failures but have no guided instruction on how to handle them. This should be a named section in Chapter 9.

### 4.5 The Final Exam Is Mentioned but Not Described

The syllabus and schedule mention a Final Exam at Week 15 worth part of the 15% exam credit, but there is no description of its format, scope, or how it differs from the midterm. Students need to know whether it is cumulative, project-based, or quiz-style.

### 4.6 Course Reflection Is Under-Specified

The Week 15 deliverables include a "Course Reflection" but there is no prompt, format, or rubric for it. A well-designed capstone reflection prompt can be one of the most valuable learning activities in a course.

---

## Section 5: Learning Outcome Alignment Audit

| Learning Outcome | Chapter(s) | Lab(s) | Assignment(s) | Assessed? |
|---|---|---|---|---|
| Responsive semantic HTML | 2 | 02 | 1 | Yes |
| Readable JavaScript | 3, 4, 5 | 03, 04, 05 | 2 | Yes |
| Browser DevTools / debugging | 1 | 01 | — | **Weak** – no dedicated assessment |
| DOM manipulation | 6 | 06 | 3 | Yes |
| Accessible form design | 7 | 07 | — | **Weak** – no dedicated assignment |
| Fetch / JSON / remote data | 9 | 08 | 4 | Yes |
| localStorage / state | 10 | 09 | — | **Weak** – no dedicated assignment |
| Component-based thinking | 12 | 11, 12 | 6 | Yes |
| Git / GitHub workflow | 0 | 00 | All | Yes |
| Plan, build, test, present | All | All | Projects | Yes |

**Notable gaps:** Browser DevTools, accessible forms, and localStorage each appear in learning outcomes but do not have a corresponding graded assignment (only labs, which together are worth 20%). Consider whether a lab is sufficient assessment weight for these outcomes, or whether an assignment should target them more directly.

---

## Section 6: Prioritized Recommendations

### Priority 1 — Before First Delivery

1. **Write differentiated content for all 12 textbook chapters.** Each needs chapter-specific key ideas, common mistakes, vocabulary, mini checklist, and practice prompt. The current templates must be replaced with actual instructional content.

2. **Write differentiated instructions for all 14 labs.** Each lab needs a specific scenario, named skills, concrete step-by-step tasks, and a content-specific rubric. Lab 00 must be a full environment setup guide.

3. **Differentiate the 6 assignment briefs.** Each must have unique requirements calibrated to course position. Remove the JavaScript requirement from Assignment 1.

4. **Build rubrics with performance levels.** Replace the 4-bullet "suggested rubrics" with rubrics that have at minimum three performance levels (Exemplary / Proficient / Incomplete) and descriptors per criterion.

5. **Provide starter files or project shells** for each lab so students have a concrete starting point.

### Priority 2 — First Revision Cycle

6. Add a peer code review activity at Week 8.
7. Write a debugging-focused component into Lab 03 or Lab 06.
8. Create a quiz alignment document mapping each quiz to chapters and outcomes.
9. Expand the final exam and course reflection prompts with format and scope details.
10. Replace all vocabulary lists with chapter-specific terms.
11. Replace all reflection prompts with chapter-specific questions.

### Priority 3 — Continuous Improvement

12. Evaluate Vue pacing after first delivery; consider expanding to three weeks.
13. Add a student-facing example gallery.
14. Survey students at Week 5 and Week 10 on workload, clarity, and confidence.
15. Review quiz item quality against Bloom's taxonomy — ensure questions assess application and analysis, not just recall.

---

## Section 7: Overall Assessment

| Dimension | Rating | Notes |
|---|---|---|
| Learning outcome clarity | Strong | Outcomes are action-verb, measurable, and well-scoped |
| Curriculum sequence | Strong | Logical progression; one sequencing error (Assignment 1) |
| Textbook content | Needs major work | Template content, not instructional content |
| Lab specificity | Needs major work | Identical generic tasks across all 14 labs |
| Assignment differentiation | Needs major work | Identical requirements; minimal brief-level guidance |
| Rubric quality | Needs work | Categories only, no performance descriptors |
| Assessment alignment | Adequate | Most outcomes covered; three have weak assessment weight |
| Accessibility integration | Strong | Consistent throughout materials |
| Tech stack relevance | Strong | Appropriate for 2026 front-end development |
| Portfolio integration | Strong | Live URLs and GitHub throughout |

The course concept and architecture are sound. The primary work remaining is content development — replacing the scaffolding templates with the actual instructional material they were designed to hold. That is a significant but well-defined task, and the structure provided here makes it straightforward to execute chapter by chapter, lab by lab.

---

*Report prepared March 2026. Recommendations are based on review of all source Markdown files in the repository as of the initial commit.*
