# Architecture

Record known technical direction only. Unapproved implementation details remain **TBD**.

## Frontend and Hosting
- Next.js App Router, TypeScript, Tailwind CSS.
- Hosted on Vercel.
- Current repository began with the default starter page and layout.
- App pages, screen layouts, and study-mode layout: **TBD**.

## Backend and Authentication
- Supabase provides Auth, Postgres, and Storage.
- Existing helpers: `src/lib/supabase/client.ts`, `src/lib/supabase/server.ts`; session refresh at `src/middleware.ts`.
- Required flows: sign-up, login, password reset, email verification, account deletion.
- After email verification, redirect to the dashboard.
- Exact server/client boundaries, route/server-action design, and detailed auth behavior: **TBD**.

## Database and Authorization
- Supabase Postgres; RLS is required.
- Tables, relationships, and RLS policies: **TBD**. Do not invent schema to fill a TBD.
- Product behavior: deleting a subject also deletes its associated files and tests. The database/storage implementation for this behavior remains to be designed and verified.
- Question bank versus question history storage: **TBD**.

## Storage and Documents
- Supabase Storage for user documents.
- Supported: digital PDF, DOCX, PPTX, TXT, and pasted text.
- Scanned PDFs, handwriting, and images are unsupported.
- Bucket names, access rules, retention, size/page limits: **TBD**.
- Extraction pipeline, background processing, retry semantics, status model, extracted-text review, and math/diagram handling: **TBD**.

## AI Integration
- Separate AI API key owned by the project owner.
- Provider/model, key storage details, rate controls, and error handling: **TBD**.
- Keep AI requests on a server-controlled boundary; never expose the key to the browser or commit it.
- No second-model verification pass.

## High-Level Data Flow
1. Student authenticates with Supabase.
2. Student creates or selects a subject.
3. Student uploads a supported document or pastes notes.
4. Source files are stored and text is processed; exact workflow **TBD**.
5. Relevant notes and approved settings are sent to the selected AI service through a server-controlled boundary.
6. Questions, answers, results, and usage are presented/persisted; exact persistence design **TBD**.

## Cost Constraints
Keep Vercel and Supabase on free tiers during development. AI usage is the only planned paid operating cost. Any additional paid service requires owner approval.