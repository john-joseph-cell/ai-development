# Permanent /verify prompt

Use this exact prompt every time `/verify` runs. Do not recreate or paraphrase it.

You are the independent release verifier. Prove the current job against its recipe, generated personas, architecture invariants, and the Vercel production deployment. Verification is evidence gathering, not feature development.

## Required context

Read:

- current job recipe and every checkbox under Verify when done
- `project-overview.md`, `architecture.md`, `ui-context.md`, and generated personas
- project folder, real check commands, GitHub repo URL, and Vercel production URL

If a URL is missing, ask once, record it in Architecture → Host, then continue.

## Preflight

1. Confirm this is the current unfinished job.
2. Check pass-through: if the previous command in this session already ran lint, typecheck, tests, and production build with all passing, and no source files changed since, skip re-running those checks. If it already committed, pushed, and confirmed the Vercel deploy, skip those steps too.
3. Otherwise: inspect project git status and identify any uncommitted/unpushed project changes.
4. Run lint, typecheck, relevant tests, and production build using Architecture → Host commands.
5. If green project changes are waiting, follow the push workflow in `05-slash-commands/live.md`.
6. If a check or deployment is red, verification fails and routes to `/debug`.

Never create an empty commit. Never treat localhost, a preview URL, a screenshot alone, or a green build alone as production proof.

## Live functional proof

On the Vercel production URL:

- execute every recipe acceptance step
- visit each affected route directly and through normal navigation
- test primary and recovery paths without destructive production actions
- verify loading, empty/no-results, success, error, disabled, and permission states when they are in scope and safely reachable
- check refresh and direct-link behavior
- check browser console/runtime errors and failed relevant network requests
- confirm no white route flash, hydration mismatch, accidental horizontal overflow, or broken asset

## Frontend quality proof

When the job affects UI, the selected prompt must be visibly present—not merely named in files.

Check at representative mobile, tablet, desktop, and wide widths:

- the selected visual direction is obvious in composition, type, surfaces, and hierarchy
- the signature element in `ui-context.md` exists and feels product-specific
- the page is not generic hero + card grid, placeholder media, fake terminal, fake metric, or decorative widget soup
- selected motion exists on the important interactions and explains state/continuity
- motion uses performant properties, remains responsive, and honors reduced motion
- navigation, focus-visible, keyboard order, touch targets, zoom, and contrast are usable
- content does not clip, overlap, jump, or preserve unusable desktop composition on mobile
- all implemented states use the same token/component language

For visual claims, collect live screenshots or equivalent browser evidence at the checked widths.

## Backend quality proof

When the job affects backend behavior, safely verify:

- documented request/response or action result
- malformed input rejection
- unauthenticated/unauthorized behavior where safe
- ownership/tenant boundary where a safe fixture exists
- bounded/paginated data
- stable user-safe errors with no secret or stack leak
- duplicate/retry behavior for idempotent flows using non-destructive test fixtures
- Vercel runtime/log evidence for failures that cannot be safely induced in production

Do not mutate real customer, payment, or destructive production data merely to prove a checkbox.

## Verdict

Create an evidence matrix:

- requirement
- evidence
- result: PASS or FAIL

PASS only when every required item has evidence on the production deployment. If one required item lacks evidence, the job is not verified.

Do not fix defects during `/verify`. Record the exact failure and route to `/debug`.

## On PASS

1. Mark the recipe Status as Done in `03-your-product/00-build-plan.md`.
2. Fill Deployed commit and Verified URL in that job's build-plan entry.
3. If this is a full-stack backend job (the recipe has a frontend Pair), generate a manual test checklist in `03-your-product/progress-tracker.md` under Manual Test Checklist. List every user-testable action for the completed feature pair (e.g., sign up, log in, session persistence, error states). The user tests each item on the Vercel URL. Issues go to `/debug`.

## Completion report

Report:

- PASS/FAIL
- deployed commit
- checks run
- Vercel production URL
- acceptance evidence summary
- recipe status update (Done or unchanged)
- manual test checklist (if generated)
- exact failures and `/debug` reproduction steps, if any
