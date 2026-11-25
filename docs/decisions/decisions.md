# Decision Log

Owner-approved decisions. Add only meaningful decisions; do not turn suggestions into requirements.

| Date | Decision | Reason |
|---|---|---|
| 2026-11-24 | Use Supabase free tier for Auth, Postgres, and Storage during development. | Keep development within the free-tier constraint. |
| 2026-11-24 | Use a separate AI API key owned by the project owner. | Owner controls AI billing and key ownership. |
| 2026-11-24 | Accept digital documents only; no scans, handwriting, or images. | Keep inputs extractable without OCR/image processing. |
| 2026-11-24 | Use an accepted-answer bank for short single-answer blanks; batch-check long open-ended blanks with AI at submission. | Balance deterministic checking and longer response evaluation. |
| 2026-11-24 | Show one question per screen. | Approved test interaction. |
| 2026-11-24 | Use preset difficulty only: Easy, Medium, Hard, AP-level. | Keep difficulty bounded. |
| 2026-11-24 | Do not run a second-model verification pass. | Avoid extra cost and complexity. |
| 2026-11-24 | Do not support Google Drive import. | Outside approved scope. |
| 2026-11-24 | Sample subject is optional and offered as a user choice. | Do not create unwanted sample content. |
| 2026-11-24 | Deleting a subject also deletes its associated files and tests. | Keep subject deletion behavior consistent. |
| 2026-11-24 | After email verification, redirect to the dashboard. | Provide a clear post-verification destination. |
| 2026-11-24 | Claude coordinates daily work; agents submit reports to `project/reports/`. | Preserve progress and support daily planning. |
| 2026-11-24 | GitHub Copilot performs the end-of-day review, commit, and push; the owner runs it at day's end. | Centralize daily integration and pushing. |

## Governance
- The owner is the final product decision-maker.
- Claude coordinates work and the task board.
- The repository is the source of truth.
- Each substantial task has one implementation owner.
- Product and architecture TBDs must not be resolved by assumption.