# Project Overview

## Product
An AI practice-test app where students provide digital study notes and receive practice questions, flashcards, and explanations grounded in those notes. The owner decides product behavior, AI behavior, design, and UX.

## Current Stage
Planning / foundation setup. The repository has a Next.js starter and Supabase helpers; student-facing features are not yet implemented.

## Stack and Constraints
- Next.js App Router, TypeScript, Tailwind CSS, and Vercel.
- Supabase Auth, Postgres, and Storage.
- Separate AI API key owned by the project owner.
- Keep Vercel and Supabase on free tiers during development. Any additional paid service requires owner approval.

## Existing Setup
- Repository: `anshitbawane/practice-test-app`.
- Supabase helpers: `src/lib/supabase/client.ts` and `src/lib/supabase/server.ts`.
- Session-refresh middleware: `src/middleware.ts`.
- These are setup artifacts, not completed product features.

## Roadmap
1. **Phase 1 — Foundation:** auth, subjects, dashboard, RLS, deployment check.
2. **Phase 2 — Uploads:** storage, extraction, topic map, processing status, delete/retry.
3. **Phase 3 — Question generation:** test menu, AI module, answer keys, answer checking.
4. **Phase 4 — Test experience and results.**
5. **Phase 5 — Hardening and beta.**
6. **Later releases:** Release 2 and Release 3 features in [Product Specification](specs/project-spec.md).

Only Phase 1 tasks belong on the active task board until coordinated by Claude and the owner.

## Coordination
- Claude manages daily planning, task coordination, project status, and agent prompts.
- Every agent writes an end-of-assignment report to `project/reports/`.
- GitHub Copilot performs the end-of-day review, commit, and push. The owner runs Copilot at the end of each development day.
- Gemini is optional and has no assumed repository access.
- ChatGPT is the technical-planning and backup coordinator.

## Current Blockers
- Database schema and RLS rules remain TBD.
- Auth, subjects, and dashboard need implementation.
- Deployment configuration and a successful deployment check need verification.
- Detailed acceptance tests need to be established with implementation.