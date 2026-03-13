# Instructional Design Review: WEB 1430

## Executive Summary

This course has a strong macro-level structure. The sequence of topics is coherent, the stated outcomes match the catalog description, and the package is organized cleanly for Canvas delivery and a GitHub-based workflow. The inclusion of an original textbook, weekly modules, labs, assignments, projects, and quizzes creates the right overall architecture for a 15-week asynchronous web development course.

The main weakness is that many of the learner-facing materials are still too generic to reliably drive learning on their own. Across modules, labs, assignments, and projects, the scaffolding often reads like a template rather than a complete instructional experience. In practice, that means students may understand the broad theme of a week without having enough specificity to know what success looks like, how work will be judged, or how each activity builds toward mastery.

From an instructional design perspective, the course is viable, but not yet fully instruction-ready. It needs a second pass focused on concrete task design, assessment quality, learner support, and maintainability.

## Findings

### 1. High severity: Many graded activities are underspecified and likely to produce inconsistent student performance.

The assignments and projects often provide only a broad build prompt plus a generic requirement list. For example, [assignments/assignment-1-responsive-content-page.md](/Users/gtuck/Documents/GitHub/web1430-new/assignments/assignment-1-responsive-content-page.md#L3) and [assignments/assignment-4-api-data-story.md](/Users/gtuck/Documents/GitHub/web1430-new/assignments/assignment-4-api-data-story.md#L3) are structurally almost identical despite addressing substantially different skills. The same pattern appears in the final project brief at [projects/final-project-campus-or-community-tool.md](/Users/gtuck/Documents/GitHub/web1430-new/projects/final-project-campus-or-community-tool.md#L3).

Problems this creates:
- Students do not have enough performance criteria to distinguish minimum passing work from strong work.
- Instructors do not have enough detail to grade consistently across sections or over time.
- Students may over-focus on deliverables like deployment and commit history while underperforming on target concepts for the week.

Recommendation:
- Rewrite each assignment/project around 4 sections: `Scenario`, `Required features`, `Constraints`, and `Evidence of learning`.
- Add assignment-specific acceptance criteria. Example for the API assignment: required loading state, required empty/error state, at least one user-controlled filter, and a short explanation of API field mapping.
- Replace "rubric highlights" with analytic criteria and performance descriptors for at least `Exemplary`, `Proficient`, `Developing`, and `Insufficient`.

### 2. High severity: Labs are too generic to function as strong practice scaffolds in an asynchronous course.

The labs appear to share the same boilerplate structure. [labs/lab08-build-an-api-powered-viewer.md](/Users/gtuck/Documents/GitHub/web1430-new/labs/lab08-build-an-api-powered-viewer.md#L3) is nearly indistinguishable in structure from other labs, and repository-wide pattern matching shows the same text repeated across the lab set. Because this is an asynchronous course, labs need to do more than name a task category; they need to model process, anticipate misconceptions, and provide bounded practice steps.

Problems this creates:
- Students may not know where to start or what sequence to follow.
- Weaker learners will struggle to bridge from lecture/theme to implementation.
- Labs are less useful as formative assessment because they do not clearly surface the intended misconception or skill checkpoint.

Recommendation:
- Redesign every lab around `Before you begin`, `Starter state`, `Steps`, `Checkpoints`, `Common bugs`, and `Submission evidence`.
- Include one concrete artifact students must produce during the lab, such as a screenshot of DevTools, a short reflection on a failed fetch state, or a brief accessibility test log.
- Add time estimates and difficulty indicators to help students manage weekly workload.

### 3. High severity: Module pages provide orientation, but not enough guidance for self-directed online learners.

The weekly overview pages are clean, but highly repetitive. Compare [modules/week-00-overview.md](/Users/gtuck/Documents/GitHub/web1430-new/modules/week-00-overview.md#L3) and [modules/week-12-overview.md](/Users/gtuck/Documents/GitHub/web1430-new/modules/week-12-overview.md#L3): both rely on the same `Success plan` and the same checkpoint question structure. That uniformity makes the course easy to scan, but it also weakens weekly presence and instructional guidance.

Problems this creates:
- Students do not get a week-specific explanation of what will be hard, what to prioritize, or what prior knowledge matters.
- Module pages do not help learners allocate time across reading, lecture, coding, and assessment.
- The weekly checkpoint question is too generic to support metacognition tied to the actual concept.

Recommendation:
- Add week-specific `Why this week matters`, `Likely sticking points`, `Estimated workload`, and `How this connects to the project`.
- Replace the generic checkpoint with a concept-specific self-test prompt.
- Include a short "If you fall behind" recovery note in each module.

### 4. Medium-high severity: Assessments over-rely on low-cognitive-demand selected response items.

Quiz and exam items are generally aligned to course content, but many are basic recall or recognition questions. [quizzes/quiz-1-browser-foundations.json](/Users/gtuck/Documents/GitHub/web1430-new/quizzes/quiz-1-browser-foundations.json#L8) and [quizzes/final-exam.json](/Users/gtuck/Documents/GitHub/web1430-new/quizzes/final-exam.json#L8) emphasize straightforward multiple choice and true/false items. That is acceptable for concept checks, but weak for demonstrating transfer, debugging, design judgment, or front-end problem solving.

Problems this creates:
- High scores may not reflect actual ability to build or troubleshoot.
- Exams may reward recognition more than application.
- Assessment coverage is thinner for higher-order outcomes like planning, testing, and presenting a polished project.

Recommendation:
- Reserve quizzes for vocabulary and core concept checks, but add applied items such as code reading, error diagnosis, UI critique, or "choose the better implementation and justify why."
- Add short-answer or file-submission components to midterm/final assessments where Canvas supports them.
- Build an outcome-to-assessment map to ensure every course outcome is measured at an appropriate cognitive level.

### 5. Medium severity: Course-level alignment is strong, but outcome-level mapping is not visible to learners or instructors.

The learning outcomes in [syllabus.md](/Users/gtuck/Documents/GitHub/web1430-new/syllabus.md#L13) and [course/learning_outcomes.md](/Users/gtuck/Documents/GitHub/web1430-new/course/learning_outcomes.md#L1) are appropriate and well scoped. The schedule in [course/schedule.md](/Users/gtuck/Documents/GitHub/web1430-new/course/schedule.md#L3) also follows a sensible progression. What is missing is explicit alignment at the activity level.

Problems this creates:
- Students may not know why a given lab or quiz matters.
- Instructors cannot easily audit whether outcomes are over- or under-assessed.
- It is harder to revise the course strategically because dependencies are implicit.

Recommendation:
- Add an outcome tag to every module, lab, assignment, quiz, and project milestone.
- Create a simple curriculum map showing where each outcome is introduced, practiced, and mastered.
- Surface the primary outcome(s) at the top of each learner-facing activity.

### 6. Medium severity: Accessibility expectations are stated, but not operationalized enough in the graded work.

The syllabus explicitly values accessibility in [syllabus.md](/Users/gtuck/Documents/GitHub/web1430-new/syllabus.md#L49), and accessibility appears repeatedly in assignment requirements. That is good. However, most materials do not define how students should test accessibility or what evidence they should submit.

Problems this creates:
- Accessibility may become a vague aspiration instead of a graded habit.
- Students may think accessibility means only color contrast or keyboard support.
- Graders may apply inconsistent expectations.

Recommendation:
- Add required accessibility evidence to major deliverables: keyboard test notes, heading structure review, form label validation, alt text audit, Lighthouse or axe results where appropriate.
- Use short accessibility checklists tied to the week’s skills instead of generic references.
- Add at least one rubric row explicitly evaluating accessibility testing, not just accessibility outcomes.

### 7. Medium severity: The course promises a GitHub workflow, but the workflow support is thin for novices.

The course requires a public or instructor-shared repository and meaningful commit history in [syllabus.md](/Users/gtuck/Documents/GitHub/web1430-new/syllabus.md#L26). The repository README also emphasizes GitHub publishing and Canvas import in [README.md](/Users/gtuck/Documents/GitHub/web1430-new/README.md#L29). That workflow is authentic and valuable, but it can become a barrier if not strongly scaffolded.

Problems this creates:
- Students new to Git may fail for workflow reasons rather than learning goals.
- Instructors may end up troubleshooting tooling instead of assessing learning.
- Public repo requirements may create privacy friction for some students.

Recommendation:
- Expand Week 00 with explicit setup checks, screenshot evidence, and a small no-stakes Git practice task.
- Provide a fallback workflow for students who need private repos or instructor-shared access.
- Include a "definition of meaningful commit history" with 2-3 examples and non-examples.

### 8. Medium severity: The textbook voice is strong, but chapters need more direct instructional apparatus.

The textbook is one of the stronger assets. [textbook/README.md](/Users/gtuck/Documents/GitHub/web1430-new/textbook/README.md#L1) shows a coherent 12-chapter progression, and sampled chapter text such as [textbook/chapters/chapter-11-modules-npm-and-vite.md](/Users/gtuck/Documents/GitHub/web1430-new/textbook/chapters/chapter-11-modules-npm-and-vite.md#L1) has a clear, student-friendly voice. However, the sampled chapter remains conceptual and reflective without much direct worked instruction.

Problems this creates:
- Students may enjoy the reading but still need more demonstration to apply the content.
- The textbook may not adequately support novice learners studying alone.

Recommendation:
- Add worked examples, annotated code snippets, mini knowledge checks, and "try this in DevTools" prompts inside each chapter.
- End each chapter with a `Can you now...` checklist tied directly to the week’s assignment or lab.

### 9. Medium severity: Course maintenance and revision workflow are fragile.

The repo positions itself as a complete rebuild with an included packaging script, but the script at [scripts/build_canvas_package.py](/Users/gtuck/Documents/GitHub/web1430-new/scripts/build_canvas_package.py#L1) is only a note pointing to an already-generated export. The import instructions in [course/import_to_canvas.md](/Users/gtuck/Documents/GitHub/web1430-new/course/import_to_canvas.md#L1) assume the package exists, but do not support future regeneration.

Problems this creates:
- The course is harder to revise systematically for future terms.
- Instructors may edit source content without a reliable way to rebuild the Canvas package.
- Version control is present, but the production workflow is not reproducible.

Recommendation:
- Restore or recreate the actual package-build pipeline.
- Document the source-of-truth workflow: which files instructors edit, how the Canvas package is regenerated, and how validation should occur before import.
- Add a release checklist for term rollovers.

## Strengths Worth Preserving

- The course sequence is coherent and appropriately scaffolded from browser foundations to DOM, APIs, state, modules, Vue, deployment, and a final project, as shown in [course/schedule.md](/Users/gtuck/Documents/GitHub/web1430-new/course/schedule.md#L3).
- The outcomes are practical, discipline-appropriate, and well matched to a client-side development course, as shown in [course/learning_outcomes.md](/Users/gtuck/Documents/GitHub/web1430-new/course/learning_outcomes.md#L1).
- The GitHub plus deployment workflow is authentic and professionally relevant.
- The textbook voice is accessible and conceptually grounded.
- The course already foregrounds accessibility, reflection, and project-based learning.

## Priority Recommendations

### First pass: make the course instruction-ready

1. Replace generic lab, assignment, and project templates with activity-specific directions and analytic rubrics.
2. Add week-specific guidance to every module page, including likely trouble spots and estimated workload.
3. Revise quizzes and exams to include more applied reasoning and debugging tasks.

### Second pass: strengthen learner support and inclusion

1. Add explicit workflow scaffolds for Git, deployment, and troubleshooting.
2. Turn accessibility from a stated value into required evidence in major deliverables.
3. Add examples, exemplars, and model submissions where appropriate.

### Third pass: improve maintainability

1. Rebuild the Canvas packaging workflow so the source materials are truly reusable.
2. Create an outcome-assessment map and use it as the basis for future revisions.
3. Add an instructor-facing course maintenance guide for term setup, grading consistency, and content updates.

## Overall Judgment

This is a well-conceived course shell with solid disciplinary alignment and good overall sequencing. Its biggest instructional design issue is not the course architecture; it is the lack of specificity inside many of the learner-facing materials. If those materials are made more concrete, measurable, and supportive, this course could become a strong asynchronous learning experience rather than a promising but still partially templated package.
