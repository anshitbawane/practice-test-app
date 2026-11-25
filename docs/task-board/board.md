# Task Board Index

This directory contains task tracking for the project.

## Files

- [Active Tasks](tasks.md) - Current task list with Phase 1 tasks

## Task Board Authority

Claude manages assignments and status. OpenCode is the primary developer; Codex handles difficult bugs/reviews; Copilot handles small assigned work and the end-of-day review/commit/push; Gemini is optional manual-context research/design feedback; ChatGPT supports planning and backup coordination.

Claude may move Backlog → In Progress, In Progress → Awaiting Review, and tasks → Blocked with a reason. Completion requires verified acceptance criteria. Owner approval is required for priority, scope, owner, and feature changes.

Every agent must write an end-of-assignment report to `project/reports/<YYYY-MM-DD>/<TASK-ID>-<AGENT>.md`, including work completed, files changed, checks/results, setbacks/blockers, unfinished work, and next steps.

At day's end, after reports and task updates are present, the owner runs Copilot. Copilot reviews the day's changes and pushes only verified, in-scope work to `main`. If checks fail or the push is unsafe, it must not push and must report why.