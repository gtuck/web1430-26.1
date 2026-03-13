# Content Expert Analysis Report: WEB 1430 Client-Side Web Development

**Date:** March 13, 2026  
**Scope:** Course-level documents, all weekly module overviews, lecture structure, labs, assignments, projects, textbook navigation docs, and quiz/exam source files

**Status update:** The deficiencies identified in this report were addressed in a synchronization pass on March 13, 2026. The findings below are preserved as the pre-fix analysis.

## Executive Summary

WEB 1430 is instructionally strong. The course covers all stated learning outcomes, the conceptual sequence is coherent, and the weekly materials use a consistent scaffold that should help students move from browser fundamentals through semantic HTML/CSS, JavaScript, DOM work, async/state, modular tooling, Vue, and final project delivery.

The main risk is not missing content. The main risk is **publication drift**: several high-visibility documents disagree about due dates, assessment scope, point totals, and even how many textbook chapters exist. In other words, the teaching design is solid, but the course package is not yet fully synchronized.

**Bottom line:** Learning objectives are met, and the intended flow is smooth. The course should still receive a documentation/alignment cleanup pass before delivery.

## Method

- Reviewed core planning docs: `course/learning_outcomes.md`, `course/schedule.md`, `syllabus.md`, `course/syllabus.md`, `home.md`, `README.md`, `textbook-table-of-contents.md`, `textbook/README.md`
- Audited structure across all `modules/`, `lectures/`, `labs/`, `assignments/`, and `projects/`
- Spot-checked representative lecture and lab content at transition points: Weeks 01, 04, 06, 08, 09, 11, 12, 13, 14, and 15
- Compared weekly schedule/module deliverables against the individual assignment and project briefs
- Compared `course/quiz-alignment.md` against the actual JSON assessment source files in `quizzes/`

## Overall Judgement

### What is working well

1. **The instructional arc is clear and professionally sequenced.**  
   Students move from platform/browser mental models to semantic markup, then into JavaScript logic, then into DOM/event work, then async/state/tooling, then framework thinking and capstone integration.

2. **The course uses a highly consistent weekly pattern.**  
   Module overviews all follow the same structure (`This week`, `Success plan`, `Resources`, `Checkpoint question`). Lecture notes consistently include `Weekly focus`, `Why this matters`, `Learning targets`, `Core concepts`, `Common mistakes`, `Accessibility connection`, `Demo walkthrough`, `Practice prompt`, and `Bridge`. That consistency supports flow.

3. **Labs, assignments, and projects reinforce the right skills at the right level.**  
   Labs are practice-oriented and procedural. Assignments ask for transfer and synthesis. Projects require planning, deployment, rationale writing, and sustained workflow.

4. **Accessibility is not isolated to one week.**  
   It appears in early semantic instruction, dedicated forms work, Chapter 13 synthesis, Week 14 Lighthouse/audit work, and the final project requirements. That is a strong curricular choice.

5. **Projects are authentic rather than decorative.**  
   The course repeatedly asks for deployable work, Git/GitHub workflow, rationales, and commit history. That supports the final learning outcome well.

### Learning outcome coverage

| Learning Outcome | Primary Instruction | Primary Practice / Assessment | Status |
|---|---|---|---|
| Responsive, semantic HTML/CSS | Week 02 lecture, Chapter 2 | Lab 02, Assignment 1, Project 1, Final Project | Met |
| Readable JavaScript | Weeks 03-05, 11 | Labs 03-05, 10; Assignments 2 and 5 | Met |
| Browser DevTools | Week 01 lecture, Lab 01 | Quiz 1, reinforced in Quiz 2 | Met |
| DOM manipulation | Weeks 06-07 | Lab 06, Assignment 3, Project 1 | Met |
| Accessible forms and feedback | Week 07, Chapter 13 | Lab 07, Assignment 2, Assignment 6 | Met |
| Fetch API / JSON | Week 09 | Lab 08, Assignment 4, Project 2, Final Project | Met |
| Client-side state persistence | Week 10 | Lab 09, Project 2, Final Project | Met |
| Introductory component thinking | Weeks 12-13 | Labs 11-12, Assignment 6, optional Vue use in Final Project | Met |
| Git/GitHub workflow | Week 00 plus repeated submission expectations | Lab 00, commit history requirements, repo-based submissions | Met |
| Plan, build, test, and present a polished project | Project milestones, Week 14 QA/deployment, Week 15 reflection | Projects 1-2, Final Project, Lab 13, reflection work | Met |

## Flow Analysis

### Where the flow is especially smooth

- **Week 00 to Week 02:** workflow, browser model, and semantic structure are introduced before students are asked to build independent HTML/CSS work.
- **Weeks 03 to 05:** JavaScript starts with values and expressions, then advances to control flow, then to arrays/objects/JSON. This is the right order.
- **Weeks 06 to 08:** DOM and event-driven interaction culminate in Project 1 and the midterm integration week. The Week 08 refactoring emphasis is a strong bridge into more complex later work.
- **Weeks 09 to 11:** async work, state, and modules build naturally into Project 2.
- **Weeks 11 to 13:** modules before Vue is the right sequence; students encounter component thinking after they already understand import boundaries and Vite.
- **Weeks 14 to 15:** QA, Lighthouse, deployment, and reflection provide a good finish to the capstone.

### Important nuance

Some assignments preview small amounts of DOM work before the formal DOM week. That does **not** appear to create a prerequisite violation, because Week 04 lab instructions already teach basic value-reading and rendering patterns. The issue is not the pedagogy. The issue is that the published due-date documents are inconsistent enough to blur the intended pacing.

## Findings

### 1. High: There is no single authoritative due-date schedule

The course-level schedule and module overviews agree with each other, but several individual assignment/project briefs disagree with them.

| Item | Schedule / Module Deliverable | Individual Brief |
|---|---|---|
| Assignment 2 | Week 04 | `assignments/assignment-2-interactive-calculator.md` says **End of Week 5** |
| Assignment 3 | Week 06 | `assignments/assignment-3-dom-pattern-library.md` says **End of Week 8** |
| Assignment 4 | Week 09 | `assignments/assignment-4-api-data-story.md` says **End of Week 10** |
| Assignment 5 | Week 11 | `assignments/assignment-5-modular-refactor.md` says **End of Week 12** |
| Assignment 6 | Week 13 | `assignments/assignment-6-reactive-form-workflow.md` says **End of Week 14** |
| Project 2 final | Week 14 | `projects/project-2-data-driven-micro-app.md` says **End of Week 12** |

**Why this matters:**  
This is the biggest flow problem in the repository. A student or instructor could follow the schedule, the module, or the brief and get different answers. Even if the pedagogy is sound, contradictory deadlines break pacing, planning, and trust.

### 2. High: Assessment planning documents do not match the actual assessment source files

`course/quiz-alignment.md` describes a much larger assessment set than the JSON files currently contain.

Examples:

- The alignment doc says most quizzes are **10 MC/TF + 2 application** questions, but the JSON files contain only **5-8** questions per quiz.
- The alignment doc says the **Midterm** is **30 MC/TF + 5 application** questions, but `quizzes/midterm-exam.json` contains **15** questions.
- The alignment doc says the **Final Exam** is **40 MC/TF + 8 application** questions, but `quizzes/final-exam.json` contains **17** questions.
- The alignment doc says the Final covers **Chapters 1-12**, weighted toward **9-12**, but the live materials now include Chapters **13 and 14**, and the final exam JSON includes late-course topics such as `.gitignore` and Lighthouse-related performance work.
- The alignment doc still says Git/GitHub workflow is **not directly quizzed**, but `quizzes/final-exam.json` includes a `.gitignore` question.

There is also an internal metadata mismatch inside the JSON files:

| Assessment | Declared `points` | Sum of `questions[].points_possible` |
|---|---:|---:|
| Quiz 1 | 10 | 7 |
| Quiz 2 | 10 | 8 |
| Quiz 3 | 10 | 7 |
| Quiz 4 | 10 | 5 |
| Quiz 5 | 10 | 7 |
| Quiz 6 | 10 | 7 |
| Quiz 7 | 10 | 7 |
| Quiz 8 | 10 | 7 |
| Midterm | 50 | 15 |
| Final | 60 | 17 |

**Why this matters:**  
At minimum, this is a maintenance/documentation problem. Potentially, it is also a grading/import problem, depending on how the Canvas build pipeline interprets those fields. Either way, the assessment layer is not currently self-consistent.

### 3. Medium: The course still advertises a 12-chapter textbook even though Weeks 13-14 use Chapters 13 and 14

These documents still present the textbook as 12 chapters:

- `home.md`
- `README.md`
- `textbook-table-of-contents.md`
- `textbook/README.md`

But the repository clearly includes:

- `textbook/chapters/chapter-13-accessibility-synthesis.md`
- `textbook/chapters/chapter-14-performance-testing-and-deployment.md`

And the late-course modules explicitly assign those chapters:

- `modules/week-13-overview.md`
- `modules/week-14-overview.md`

**Why this matters:**  
This is a navigation and expectation problem. Students and instructors using the course map or textbook TOC can reasonably conclude the book ends at Chapter 12, even though the last two weeks rely on later chapters.

## What This Means for the Course

### Pedagogical quality

Strong. The course objectives are met, and the underlying teaching sequence is coherent and professionally designed.

### Operational readiness

Not fully synchronized yet. The late-stage drift between schedules, briefs, and assessments is large enough that I would not call the package publication-ready until those contradictions are reconciled.

## Recommended Next Actions

1. **Choose one source of truth for deadlines and update everything else to match.**  
   The fastest fix is to reconcile `course/schedule.md`, the `modules/week-*.md` deliverables, and the assignment/project `**Due:**` lines in one pass.

2. **Decide whether the assessment JSON files or `course/quiz-alignment.md` reflect the intended assessment model.**  
   Then update the other side. Right now they describe different courses.

3. **Normalize assessment point metadata before the next Canvas export.**  
   Verify whether the `points` field or the per-question totals are authoritative, and make them agree.

4. **Update all course-inventory docs from 12 chapters to 14 chapters.**  
   The home page, README, and textbook TOC should all reflect the current content set.

5. **Rebuild and re-verify the Canvas package after the cleanup pass.**  
   The repository contains both source content and a built export; they should not drift.

## Final Verdict

If the question is, "Does this course teach what it promises, and is the instructional flow fundamentally sound?" the answer is **yes**.

If the question is, "Can this package be published exactly as-is without confusing students or instructors?" the answer is **no**.

The course does not need a pedagogical redesign. It needs a synchronization pass.
