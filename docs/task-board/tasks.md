# Task Board

Only Phase 1 tasks are listed. Later phases should be added only when coordinated by Claude and approved by the owner.

## BACKLOG

### P1-01 — Implement authentication flows
- **Objective:** Implement sign-up, login, password reset, email verification, and account deletion with Supabase Auth.
- **Owner:** OpenCode
- **Priority:** High
- **Dependencies:** Required environment variables and any unresolved auth details.
- **Acceptance criteria:**
  - Approved auth flows work end to end.
  - Successful email verification redirects to the dashboard.
  - Session and authenticated/unauthenticated access behavior are verified.
  - No secrets are committed and no AI key reaches the client.
  - Tests, checks, and unresolved issues are reported.
- **Status:** Backlog

### P1-02 — Implement subjects
- **Objective:** Create, rename, and delete subjects; support subject color or icon.
- **Owner:** OpenCode
- **Priority:** High
- **Dependencies:** Approved schema and RLS rules; subject deletion behavior is approved.
- **Acceptance criteria:**
  - Users can manage only their own subjects.
  - The optional sample subject is offered as a choice, never auto-created without consent.
  - Deleting a subject also deletes its associated files and tests.
  - Empty/error states are handled.
  - Tests verify ownership and deletion behavior; report unresolved implementation details.
- **Status:** Backlog

### P1-03 — Implement dashboard foundation
- **Objective:** Build the initial authenticated dashboard with empty-state guidance and subject entry points.
- **Owner:** OpenCode
- **Priority:** Medium
- **Dependencies:** P1-02 and owner approval of dashboard content/layout.
- **Acceptance criteria:**
  - Authenticated users reach the dashboard.
  - Empty-state guidance appears when no subjects exist.
  - Existing subjects are shown and can be opened.
  - No unapproved dashboard features are added.
  - Tests/checks and unresolved issues are reported.
- **Status:** Backlog

## IN PROGRESS
_No tasks currently in progress._

## AWAITING REVIEW
_No tasks awaiting review._

## COMPLETED
_No Phase 1 tasks completed._

## BLOCKED

### P1-04 — Establish and verify RLS policies
- **Objective:** Define and apply RLS for the approved Phase 1 data model.
- **Owner:** OpenCode
- **Priority:** High
- **Dependencies:** Owner-approved tables, relationships, and access rules.
- **Acceptance criteria:** All user-owned records are protected; cross-user access tests pass; policies/migrations are reviewable; no TBD schema or policy is invented.
- **Status:** Blocked — schema and RLS rules are TBD.

### P1-05 — Verify deployment
- **Objective:** Confirm the foundation deploys to the intended Vercel project.
- **Owner:** GitHub Copilot (end-of-day execution)
- **Priority:** Medium
- **Dependencies:** Phase 1 foundation and confirmed Vercel environment.
- **Acceptance criteria:** Production build and deployment succeed; smoke check passes; no secrets are committed; deployment URL and issues are reported.
- **Status:** Blocked — depends on Phase 1 implementation and deployment configuration.