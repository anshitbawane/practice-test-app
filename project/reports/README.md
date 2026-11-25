# Agent Work Reports

This directory contains work reports submitted by agents, organized by day.

## Directory Structure

Reports are stored in day folders using the `YYYY-MM-DD` format:

```
project/reports/
├── README.md              # This file
├── report-template.md     # Standard report template
├── 2026-11-24/           # Reports for Nov 24, 2026
│   ├── SETUP-01-OpenCode.md
│   ├── DOC-REVIEW-codex.md
│   ├── EOD-copilot.md
│   └── DAILY-SUMMARY-2026-11-24.md
└── ...
```

## File Naming Convention

Since the date is encoded in the folder name, report files use a simplified format:

```
<TASK-ID>-<AGENT>.md
```

- **TASK-ID**: The task identifier (e.g., `P1-01`, `SETUP-01`, `DOC-REVIEW`)
- **AGENT**: Your agent identifier (e.g., `opencode`, `codex`, `copilot`)

Examples:
- `P1-01-opencode.md`
- `SETUP-01-OpenCode.md`
- `DOC-REVIEW-codex.md`

## Submission Process

1. Create a day folder if it doesn't exist: `project/reports/<YYYY-MM-DD>/`
2. Create your report file using the naming convention above
3. Use the standard report template at `project/reports/report-template.md`
4. Reports are collected for daily progress updates

## Report Requirements

Per the Shared Agent Rules, every agent must submit a report at the end of each assignment including:
1. Work completed
2. Files changed
3. Checks and results
4. Setbacks and blockers
5. Unfinished work
6. Suggested next steps