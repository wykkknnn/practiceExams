---
name: practice-exams
description: Generate ethical practice exam papers, answer keys, marking rubrics, and revision diagnostics from lecture slides, notes, readings, labs, assignments, past quizzes, practice exam papers, or other course materials. Use when a student, tutor, instructor, or study group wants sample exams, mock tests, default-format exams from arbitrary materials, new papers matching the format of an input practice paper, topic-balanced question sets, exam-style practice, worked solutions, grading criteria, or study plans while avoiding reproduction of real unreleased exam content.
---

# Practice Exams

## Overview

Create original, course-aligned practice exams from learning materials. Emphasize learning value, topic coverage, difficulty calibration, transparent assumptions, and academic integrity.

## Input Modes

Support two main modes:

1. **Materials-to-default-exam mode**
   - Use when the user provides lecture slides, notes, readings, labs, assignments, or other learning materials.
   - Extract the course map and generate a default practice exam unless the user specifies a format.
   - Default to the format in **First Response** when no exam structure is available.

2. **Practice-paper-template mode**
   - Use when the user provides an existing practice exam paper and asks for a new paper in the same style or format.
   - Extract the paper's structure, sections, question types, mark allocation, timing, wording style, answer expectations, and difficulty profile.
   - Generate a new original paper that mirrors the format, not the exact questions.
   - If the user also provides lecture materials, use the practice paper for format and the lecture materials for content coverage.
   - If the user only provides a practice paper, infer topics from that paper and state that content coverage is limited to the provided sample.

## First Response

Ask for missing essentials only when they are required to proceed:

- Course or subject name.
- Source materials or paths to files.
- Whether any provided exam paper should be treated as a format template, source material, or both.
- Target exam format, if known: duration, open/closed book, allowed aids, question types, number of marks, and difficulty.
- Whether the user wants only questions, questions plus answers, or a full marking rubric.

If the user supplies enough materials but no exam format, proceed with a reasonable default and state it briefly.

Default format:

- 2 hour exam.
- 100 marks.
- Mix of conceptual, applied, calculation/problem-solving, and synthesis questions.
- Include answer key and rubric unless the user requests questions only.

## Academic Integrity

Use `references/integrity.md` when the task involves real past papers, restricted materials, take-home exams, current assessments, or requests that sound like evasion.

Follow these boundaries:

- Generate original practice questions from concepts and learning objectives.
- Do not reproduce, predict, or reconstruct confidential or unreleased exam questions.
- Do not answer an active assessment for submission.
- If the user provides a past paper, use it only to infer public-facing style, coverage, difficulty, and mark allocation unless they explicitly own or are allowed to use it.
- If the user provides a practice paper as a template, mirror its structure and assessment style without copying question wording, scenarios, numbers, datasets, or answer text.
- Prefer "similar skill tested in a new scenario" over "same question with changed numbers."

## Workflow

1. Inventory the materials.
   - Identify file types and extract usable text, figures, tables, equations, examples, learning objectives, weekly topics, and assessment hints.
   - For slides, capture titles, section headings, repeated definitions, diagrams, worked examples, and emphasized terms.
   - For readings, distinguish core claims, methods, models, cases, and named frameworks.
   - For practice exam papers, separate reusable format signals from content signals.

2. Build a course map.
   - Group content into topics or weeks.
   - Mark each topic's apparent weight using frequency, emphasis, assignment coverage, and stated learning outcomes.
   - Note dependencies between topics.
   - Flag thin or missing coverage instead of inventing unsupported detail.

3. Choose an exam blueprint.
   - If the user supplied a format or a practice paper template, mirror it.
   - Otherwise select a balanced blueprint from `references/question-blueprints.md`.
   - Allocate marks by topic weight and cognitive demand.

4. Draft original questions.
   - Use the user's course terminology.
   - Vary question stems, contexts, and difficulty.
   - Include enough data, diagrams described in text, or assumptions for each question to be answerable without the original slides unless the user asked for open-book practice.
   - Avoid trivia unless the course clearly assesses recall.

5. Produce answers and marking guidance.
   - Give model answers calibrated to the expected depth.
   - Provide point-by-point marking rubrics for long answer, essay, design, proof, or case questions.
   - For quantitative problems, show the solution path and common partial-credit points.

6. Run a quality check.
   - Confirm total marks and timing add up.
   - Check topic coverage against the course map.
   - Check every question is answerable from the supplied material.
   - Remove duplicated questions and accidental leakage from source assessments.
   - If using a practice paper template, compare only format-level similarity, not question-level similarity.
   - Identify overrepresented or underrepresented topics.

## Practice Paper Template Extraction

When the user provides a practice paper to imitate, extract:

- Total marks, duration, allowed aids, and exam conditions.
- Section names and order.
- Number of questions per section.
- Marks per question and subquestion.
- Question types: definition, explanation, derivation, calculation, proof, case analysis, essay, algorithm trace, design, critique, or comparison.
- Expected answer length and style.
- Difficulty progression.
- Use of datasets, tables, diagrams, equations, or prompts.
- Marking rubric style if available.

Then generate a "format blueprint" before drafting the new paper. Keep topic coverage grounded in the user's course materials where available.

## Output Format

Prefer this structure unless the user asks for something else:

1. Exam assumptions
2. Coverage blueprint
3. Practice exam paper
4. Answer key
5. Marking rubric
6. Revision diagnostics

For each exam question include:

- Question number.
- Topic or week.
- Marks.
- Estimated time.
- Difficulty: easy, medium, hard, or challenge.
- Learning objective tested.

For revision diagnostics include:

- Topics most heavily tested.
- Skills the student should practice.
- Common mistakes to watch for.
- A short follow-up study plan.

## Question Design

Use `references/question-blueprints.md` for domain-neutral question patterns.

Aim for a spread across cognitive levels:

- Recall and comprehension: definitions, interpretation, conceptual distinctions.
- Application: solve a new case, compute a result, classify an example, use a method.
- Analysis: compare approaches, debug reasoning, interpret evidence, critique assumptions.
- Synthesis: design, recommend, prove, model, or integrate multiple topics.

For university-level work, include multi-step questions that require connections across lectures. Keep the wording precise and fair.

## Handling Thin Inputs

If materials are sparse, generate a smaller diagnostic quiz first and state what additional material would improve the exam. Do not pretend to know a course's hidden priorities.

If the user only names a course without materials, ask for lecture slides, syllabus, weekly topic list, readings, assignments, or learning outcomes.

If files cannot be read, explain what failed and ask the user to provide the text or a compatible file.

## Variants

Use these variants when helpful:

- `exam-paper-only`: questions without answers for self-testing.
- `worked-solutions`: full solutions and rubrics.
- `topic-drill`: many short questions for one topic.
- `adaptive-diagnostic`: start with broad questions, then recommend weaker areas.
- `instructor-version`: include marking guide, learning outcomes, and moderation notes.
