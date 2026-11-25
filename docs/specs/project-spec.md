# Product Specification

This document contains approved product behavior only. Unresolved details remain **TBD**.

## Product Purpose
Students upload or paste their own study notes. AI generates practice questions, flashcards, and explanations grounded in those notes.

## Accounts and Subjects
- Sign up, log in, password reset, email verification, and account deletion.
- After successful email verification, redirect the user to the dashboard.
- Users can create, rename, and delete subjects. Subjects have a color or icon.
- The dashboard includes empty-state guidance.
- An optional sample subject is offered as a choice; never create it automatically without the user's choice.
- Deleting a subject also deletes its associated files and tests.

## Notes and Uploads
- Supported inputs: digital PDF, DOCX, PPTX, TXT, and pasted text.
- Scanned PDFs, handwriting, and images are unsupported and receive a clear notice.
- Users can retry processing and delete a file.
- Generate an AI topic map.
- File-size/page limits: **TBD**.
- Extracted-text review depth and processing-status behavior: **TBD**.
- Math and diagram handling: future work.

## Test Setup
- Modes: Practice or Exam.
- Maximum 30 questions.
- Preset difficulty: Easy, Medium, Hard, AP-level.
- Formats: multiple choice, true/false, fill in the blank, matching.
- Instructions box: maximum 300 characters; may specify topics, files, or teacher-style references.
- Toggles: Notes only, grounding quote, hints, timer, confidence rating.

## Answer Checking
- Short single-answer fill-in-the-blank items use an accepted-answers bank created with the question.
- Long open-ended fill-in-the-blank answers are checked by AI in one batch at submission.
- "Mark me correct" is available for both.
- Do not add general AI short-answer grading.

## Test Experience and Results
- One question per screen; navigator, flagging, progress, autosave, submit warning, and keyboard shortcuts.
- Optional timer and hints.
- Results include score, topic breakdown, question review, and source tags.
- Actions: retry wrong answers, Explain this, Mark me correct, dispute answer, Make more like these, and Make a study guide.

## Account and App Utilities
Past tests, monthly usage and usage-limit notice, delete my data, privacy/terms pages, profile, and light/dark/system theme.

## Release 2
Progress dashboard, improvement over time, weak topics, most-missed concepts, test weak topics, study recommendations, teacher-style sample test, quick start from a topic, and optional confidence/mistake tracking.

## Release 3
Flashcards (Got it / Still learning); infinite questions in batches of about five with a daily limit; AI chat based on notes by default with a daily cap; exam countdown and suggested topics per day.

## Prospective — Not Committed
Export results, export data, report a question, daily app feedback.

## Explicitly Removed
Do not reintroduce without owner approval: image/scanned uploads, Google Drive import, custom difficulty text, short-answer format, general AI short-answer grading, multiple questions per page, bookmarks/notes, screen reader support, Explain differently, second-model verification, verified badge, quality test set, Daily 5, per-subject study tips, teacher view, shared subjects, voice reading, or language switch.

## Unresolved Details
App pages/layouts, study-mode layout, file/page limits, processing status, extracted-text review, math/diagram handling, question-bank versus history storage, spaced review, test-builder layout, pricing, and account age policy remain **TBD**.