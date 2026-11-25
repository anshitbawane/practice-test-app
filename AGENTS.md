<!-- BEGIN:nextjs-agent-rules -->

## This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` (resolved from this file's directory; in monorepos the `next` package may not be visible from the repo root) before writing any code. Heed deprecation notices.

This block is written and re-added by `next dev` — verify at `node_modules/next/dist/server/lib/generate-agent-files.js`. Removing it from a diff only re-creates the uncommitted change; committing it with your work keeps the tree clean.

<!-- END:nextjs-agent-rules -->

---

# Shared Agent Rules

All agents must follow these rules:

1. Work only on assigned tasks; each substantial task has one implementation owner.
2. Read relevant Next.js docs in `node_modules/next/dist/docs/` before changing Next.js code.
3. Do not modify unrelated files or make unapproved product, AI, design, or UX decisions.
4. Flag uncertainty and conflicts; never guess unresolved requirements.
5. Verify acceptance criteria before reporting completion.
6. Never commit secrets, credentials, private keys, or populated environment files.
7. Do not add paid services or recurring costs without owner approval.
8. At the end of every assignment, add a report to `project/reports/<YYYY-MM-DD>/` named `<TASK-ID>-<AGENT>.md`.
9. Reports must include: work completed, files changed, checks and results, setbacks/blockers, unfinished work, and next steps.
10. The repository and approved project docs are the source of truth.

## Agent Roles

- **Claude:** Project manager; inspects repository progress, reads reports, maintains tasks, plans daily work, and prepares agent prompts. **Claude coordinates work but cannot independently authorize implementation assignments or change task owners, priorities, scope, or features. Owner approval is required for all such changes.**
- **OpenCode:** Primary implementation agent.
- **Codex:** Complex bugs, difficult technical problems, and independent code/security reviews.
- **GitHub Copilot:** Small scoped tasks when assigned; always performs the end-of-day review, commit, and push.
- **Gemini:** Optional research and design feedback. Assume no repository access; provide relevant context or screenshots manually.
- **ChatGPT:** Technical planning, architecture feedback, and backup coordination.

Use agents selectively. Do not assign every agent work every day. Avoid overlapping edits.

## Task Board Authority

**Linear is the authoritative task tracker.** The board in `docs/task-board/` is a read-only mirror/snapshot maintained by Claude for agent visibility; it is not the source of truth. Claude's authority below applies to the mirrored board state, not to Linear.

Claude may move Backlog → In Progress, In Progress → Awaiting Review, and tasks → Blocked (with a reason). Claude may mark Awaiting Review → Completed only after verifying acceptance criteria.

**Claude may not change task owners, priorities, scope, or approved features without explicit owner approval.** Owner approval is required for changes to task priority, scope, implementation owner, or approved features.

## End-of-Day Git Workflow

The owner runs GitHub Copilot at the end of each development day. Before then, agents must submit reports and Claude must update project status and tasks.

**Copilot's end-of-day push to `main` is an explicit exception to the general no-push rule.** No other agent should push routine work. Do not push outside this end-of-day workflow.

Before pushing, Copilot **must verify**:
- Repository identity (correct remote/origin)
- Current branch is `main`
- Remote is reachable and correct
- Staged changes are verified, in-scope, and complete
- All checks pass (lint, build, tests)
- No secrets or populated environment files are included
- No unrelated or unfinished work is included

If any verification fails, conflicts exist, or a safe push cannot be confirmed, Copilot must not push; it must report the reason and leave changes unpushed.

---

# Agent Instructions

## Project Documentation

All project documentation is in the `docs/` directory at the repository root:

- **Project Overview**: `docs/project-overview.md`
- **Product Specification**: `docs/specs/project-spec.md`
- **Architecture**: `docs/architecture/overview.md`
- **Decisions (ADRs)**: `docs/decisions/decisions.md`
- **Task Board**: `docs/task-board/board.md` and `docs/task-board/tasks.md`

## Report Submission

**Every agent must submit exactly one work report per assignment, before handoff.** Milestone and session updates are included in that single report.

### Where to Submit

Create a day folder and report file: `project/reports/<YYYY-MM-DD>/<TASK-ID>-<AGENT>.md`

- `<YYYY-MM-DD>`: The assignment completion date (folder name)
- `<TASK-ID>`: The task ID (e.g., `P1-01`)
- `<AGENT>`: Your agent identifier (e.g., `opencode`, `codex`, `copilot`)

### Report Format

Use the template at: `project/reports/report-template.md`

Your report must include:
1. **Work Completed** - Checklist of tasks done
2. **Files Changed** - Table of modified files with descriptions
3. **Tests/Checks and Results** - Status of all verification steps
4. **Setbacks and Blockers** - Any issues encountered
5. **Unfinished Work** - Incomplete items with reasons
6. **Suggested Next Steps** - Prioritized recommendations

### When to Submit

- **Once per assignment, before handing off to another agent or marking the task complete**
- Milestone/session updates during the assignment are appended to the same report
- Do not create multiple reports for the same assignment

## Development Guidelines

### Code Standards
- TypeScript strict mode enabled
- ESLint with Next.js config
- Follow existing code patterns in the codebase

### Git Workflow
- Push rules: see "End-of-Day Git Workflow" above (Copilot-only exception to `main`)
- Create descriptive commit messages
- Reference task IDs (e.g., `P1-01`)

### Testing
- Run `npm run lint` before submitting
- Run `npm run build` to verify production build
- Test in dev server (`npm run dev`) for UI changes

## Project Structure Reference

```
practice-test-app/        # Repository root
├── src/
│   ├── app/              # Next.js App Router pages
│   ├── lib/supabase/     # Supabase clients
│   └── middleware.ts     # Auth middleware
├── docs/                 # Project documentation
│   ├── project-overview.md
│   ├── specs/
│   ├── architecture/
│   ├── decisions/
│   └── task-board/
├── project/reports/      # Agent work reports (organized by day)
│   ├── README.md
│   ├── report-template.md
│   └── <YYYY-MM-DD>/
│       └── <TASK-ID>-<AGENT>.md
├── agent_workspace/      # AI agent handoff files (see agent_workspace/README.md)
│   ├── incoming/         # Files received from agents (by recipient)
│   ├── outgoing/         # Files being prepared for transfer (by sender)
│   ├── shared/           # Shared research, references, screenshots
│   ├── reports/          # Handoff logs (not work reports)
│   ├── tmp/              # Scratch files (gitignored, cleared daily)
│   └── archive/          # Completed/outdated handoffs (by YYYY-MM)
└── AGENTS.md            # This file
```

## Agent Workspace (Handoff Files)

A centralized `agent_workspace/` directory exists for files transferred between AI agents (Claude, ChatGPT, OpenCode, Codex, Copilot, Gemini).

- **Purpose**: Temporary and transferable AI-generated artifacts — handoff prompts, plans, notes, research, screenshots, attachments, and handoff logs.
- **Not for**: Permanent project documentation (`docs/`), task tracking (Linear), or assignment work reports (`project/reports/`).
- **Full conventions**: See `agent_workspace/README.md` for folder structure, naming (`<YYYY-MM-DD>-<from-agent>-<purpose>.<ext>`), workflow, and rules (no overwrites, no duplicates, archive when consumed, `tmp/` gitignored and cleared daily).
- **Key workflow**:
  1. Check your `incoming/<your-agent>/` at session start.
  2. Draft in `outgoing/<you>/`, then **move** to recipient's `incoming/<recipient>/` when ready.
  3. Log non-trivial transfers in `agent_workspace/reports/` using `handoff-template.md`.
  4. Archive consumed files to `archive/<YYYY-MM>/` and note in your `project/reports/` work report.
  5. Clean `tmp/` before end-of-day push; no secrets anywhere.

## Key Commands

```bash
npm run dev      # Development server
npm run build    # Production build
npm run start    # Production server
npm run lint     # Run ESLint
```

## Environment

Required `.env.local` variables:
- `NEXT_PUBLIC_SUPABASE_URL`
- `NEXT_PUBLIC_SUPABASE_ANON_KEY`