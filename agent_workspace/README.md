# Agent Workspace

Central drop zone for **files transferred between AI agents** (Claude, ChatGPT, OpenCode, Codex, GitHub Copilot, Gemini).

## What this is (and is not)

- **Is:** temporary and transferable AI-generated artifacts — handoff prompts, plans, notes, research, screenshots, attachments, and handoff logs.
- **Is not:** permanent project documentation (that belongs in `docs/`), the task tracker (that is Linear), or a place for work reports (those go to `project/reports/`).

If content here becomes a permanent decision or specification, move it into the appropriate `docs/` file (spec, ADR, or overview) and delete or archive the workspace copy. **Linear is the authoritative task tracker.** The board in `docs/task-board/` is a read-only mirror/snapshot maintained by Claude for agent visibility; it is not the source of truth. GitHub remains the authoritative source for code and version-controlled documentation.

## Folder structure

```
agent_workspace/
├── README.md            # This file
├── incoming/            # Files received from individual agents
│   ├── claude/
│   ├── chatgpt/
│   ├── opencode/
│   ├── codex/
│   ├── copilot/
│   └── gemini/
├── outgoing/            # Files being prepared for transfer (drafts)
│   ├── claude/
│   ├── chatgpt/
│   ├── opencode/
│   ├── codex/
│   ├── copilot/
│   └── gemini/
├── shared/              # Shared research, references, screenshots, attachments
├── reports/             # Handoff/transfer logs (NOT work reports)
│   └── handoff-template.md
├── tmp/                 # Scratch files, gitignored, cleared every end of day
└── archive/             # Completed or outdated handoffs, by year-month
    └── 2026-11/
```

- `incoming/<agent>/` — files **you** are expected to receive. The folder name is the **recipient**.
- `outgoing/<agent>/` — work-in-progress you are **preparing** to send. The folder name is the **sender** (you).
- `shared/` — anything more than one agent needs (research notes, reference material, screenshots, attachments).
- `reports/` — short handoff logs recording non-trivial transfers (see workflow step 5). Do **not** put assignment work reports here; those go to `project/reports/` per AGENTS.md.
- `archive/` — consumed or outdated files, kept in `YYYY-MM` subfolders for traceability.

## Naming convention

Every file is named so the **originating agent, date, and purpose** are identifiable without opening it. The recipient is implicit in the folder location.

Pattern:

```
<YYYY-MM-DD>-<from-agent>-<purpose>.<ext>
```

- Date: day the file was created or finalized (not consumed).
- `from-agent`: one of `claude`, `chatgpt`, `opencode`, `codex`, `copilot`, `gemini`.
- `purpose`: short kebab-case description; include the task ID when one applies.

Examples:

```
incoming/opencode/2026-11-24-claude-p1-01-implementation-prompt.md
incoming/codex/2026-11-24-claude-rls-policies-review-request.md
incoming/copilot/2026-11-25-opencode-p1-02-verification-notes.md
shared/2026-11-24-gemini-research-storage-quota-options.md
shared/2026-11-25-claude-screenshot-dashboard-empty-state.png
reports/2026-11-24-claude-p1-01-prompt-handoff.md
archive/2026-11/2026-11-24-claude-p1-01-implementation-prompt.md
```

Files in `shared/` add a type tag where useful: `research`, `reference`, `screenshot`, `attachment`.

## Workflow

1. **Start a session by checking your inbox.** Read `incoming/<your-agent>/` first. Nothing there? Continue as normal.
2. **Draft in your own outgoing folder.** While preparing material for another agent, keep it in `outgoing/<you>/`.
3. **Hand off by moving to the recipient's incoming folder.** When the file is final, move it to `incoming/<recipient>/` using the naming convention above. Move (do not copy) so exactly one active copy exists.
4. **Acknowledge consumption.** When the recipient has finished using a file, note the file name in their `project/reports/` work report, then move the file to `archive/<YYYY-MM>/`.
5. **Log non-trivial transfers.** If a transfer involves more than one file, contains decisions, or starts work for another agent, write a short log in `reports/` using [handoff-template.md](reports/handoff-template.md).
6. **Use `shared/` for multi-agent material.** Research findings, reference docs, and screenshots that several agents need belong here, not in one person's inbox.
7. **Clean up before the end-of-day push.** Delete `tmp/` contents, confirm no unneeded or secret files remain, and leave `incoming/` folders tidy.
8. **Claude reviews the workspace during daily planning.** Claude flags stale items for archiving and moves permanent content into `docs/`.

## Rules

### No overwrites

- Never overwrite an existing file. If the name is taken, append `-v2`, `-v3`, etc. to the purpose (e.g., `2026-11-24-claude-p1-01-prompt-v2.md`).
- This applies to `incoming/`, `outgoing/`, `shared/`, and `reports/` alike.

### No duplicates

- Exactly one active copy of a file at a time. Draft in `outgoing/`, then **move** it to `incoming/` when sending — never leave both copies active.
- If the same content is needed by several agents, place one copy in `shared/` and reference it.

### Archiving

- Move files to `archive/<YYYY-MM>/` when they have been consumed or are outdated.
- Keep archives light: delete large binaries (over ~5 MB) after handoff; if their content matters long-term, summarize it in `docs/` first.
- Never delete from `archive/` without Claude or owner review.

### Temporary files

- Scratch material goes in `tmp/` only.
- `tmp/` is gitignored and must be empty before the end-of-day push.

### Safety

- Never place secrets, API keys, populated `.env` values, or student/personal data in this workspace (mirrors AGENTS.md rule 6).
- Files here are temporary working artifacts; only files needed for handoff context should be committed.

## Repository status note

Useful handoff documents in this workspace are committed to GitHub so all agents can access them. `tmp/` and common scratch patterns (`*.tmp`, `*~`, `*.swp`, `*.bak`) are excluded via `.gitignore`.
