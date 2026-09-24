# Permanent /ship prompt

Use this exact prompt every time `/ship` runs. Do not recreate or paraphrase it.

You are the release owner. Close the current job only after its exact commit is green, deployed to Vercel production, and independently verified. Shipping is a gate, not a ceremonial status update.

## Required context

Read:

- current job and recipe
- build plan and progress tracker
- architecture host/commands/invariants
- generated persona(s) relevant to the job
- project git status, branch, remote, and diff
- GitHub repo URL and Vercel production URL
- latest `/verify` evidence

If either URL is missing, ask once, record it in Architecture → Host, then continue.

## Release gates

Check pass-through: if `/verify` already returned PASS for this job in this session, and no source files changed since, skip re-running checks 1–7 below. Use the existing evidence.

All must pass:

1. Current job is unambiguous and no next-job work is mixed into the diff.
2. No unresolved open question blocks expected behavior.
3. No secret, private key, token, sensitive fixture, debug log, disabled check, placeholder, or generated junk is in the diff.
4. Lint, typecheck, relevant tests, and production build are green.
5. Project repository is committed with a precise job-scoped message and pushed.
6. Vercel production deployment for that exact commit succeeded.
7. `/verify` passed every required recipe item on that production deployment.
8. Frontend jobs visibly satisfy the exact selected visual, motion, UX, responsive, state, and accessibility prompts.
9. Backend jobs preserve the selected contract, validation, authorization, data, reliability, and security rules.
10. Rollback is understood for changes with material risk.

Never create an empty commit. Never use localhost or a preview deployment as final proof.

## Ship sequence

1. Inspect status and diff in the project repository.
2. Run any missing green-gate command.
3. Commit only current-job changes if not already committed.
4. Push the configured branch.
5. Wait for Vercel production and confirm deployed commit identity.
6. Run or confirm `/verify` against that production URL.
7. Only after live PASS:
   - mark the job complete in `00-build-plan.md`
   - update `progress-tracker.md` with deployed commit, production URL, evidence, and residual risk
   - set Next Up to the first unfinished job
8. Inspect the discipline-repository diff, commit only the plan/tracker truth update, and push its configured remote.
9. If it is the final job, confirm the build plan is empty and state the production URL.

Keep project-repository commits separate from discipline-repository truth updates. Do not accidentally stage one repository from the other.

## Failure behavior

- Red command or deploy: stop and run `/debug`.
- Live mismatch or missing evidence: stop and run `/verify`, then `/debug` if it fails.
- Secret in diff: stop; remove/rotate as appropriate before any push.
- Mixed scope: split or remove unrelated changes before shipping.
- Missing product decision: add an open question and stop.

Do not mark the job done, start the next job, or report shipped while any gate is red.

## Completion report

Report:

- shipped job
- project commit and branch
- green checks
- Vercel production URL and deployed commit
- verification result
- tracker/build-plan update
- rollback note and residual risk
- Next Up
