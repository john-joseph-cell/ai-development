# Permanent /ship prompt

Use this exact prompt every time `/ship` runs. Do not recreate or paraphrase it.

You are the release owner. Close the current job only after its exact commit is green, deployed to Vercel production, and independently verified. Shipping is a gate, not a ceremonial status update.

Your responsibility is to establish a trustworthy release chain:

`Current Job → Exact Scope → Green Checks → Exact Commit → Remote Branch → Vercel Deployment → Production URL → Independent Verification → Release Closure`

Do not skip a link merely because another link is green.

---

## Required context

Read:

* current job identity
* current job recipe
* build plan
* progress tracker
* project overview
* architecture host/commands/invariants
* UI context when relevant
* generated `frontend-prompt.md` when frontend behavior is in scope
* generated `backend-prompt.md` when backend behavior is in scope
* project git status
* current branch
* remote
* relevant diff/history
* GitHub repo URL
* Vercel production URL
* latest `/verify` evidence
* current Vercel deployment corresponding to the intended release commit

If either URL is missing, ask once, record it in `Architecture → Host`, then continue.

If the current job is ambiguous, do not infer it from an unrelated future job. Resolve the active job from the command context, current recipe, and build-plan state before continuing.

---

# Current-job identity

Establish exactly:

* job name
* recipe path
* job Layer
* Pair when applicable
* project folder
* production branch
* project repository
* intended release commit
* selected frontend persona when applicable
* selected backend persona when applicable

The ship target must be the job that was actually verified.

Do not blindly select:

> "the first unfinished job"

after `/verify` has already updated the build plan.

If `/verify` marked the verified job Done, `/ship` must still identify that same verified job from the current command context and its recorded verification evidence.

Never ship a different job merely because it now appears first in the unfinished list.

---

# Release identity

A release consists of:

* one current job
* one job-scoped project change set
* one intended project commit
* one configured branch
* one corresponding Vercel production deployment
* one production URL

These identities must remain consistent.

Do not collapse them into the generic statement:

> "The feature is deployed."

Before closing the job, establish:

`Job`
→ `Commit`
→ `Remote`
→ `Vercel deployment`
→ `Production URL`

---

# Release gates

Check pass-through: if `/verify` already returned PASS for this job in this session, and no source/configuration files changed since, skip re-running checks and reuse the existing evidence where it remains valid.

All applicable gates must pass:

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

Also verify:

11. The deployed production commit matches the intended release commit.
12. The production URL being inspected is serving the expected project/deployment.
13. `/verify` evidence belongs to the same release deployment or remains valid under the pass-through rules.
14. No relevant source/configuration change occurred after the last successful verification.
15. No uncommitted intended project changes remain outside the released commit.
16. No unrelated project changes were accidentally included.
17. The current branch and remote correspond to the configured production workflow.
18. Any required repository/branch protections or deployment checks were respected.
19. Any required migration/configuration/environment transition is compatible with the deployed application.
20. Any material residual risk is recorded before closure.

Never create an empty commit.

Never use localhost as final proof.

Never use a preview deployment as final proof.

Never use a previous deployment as proof for a newer commit.

Never mark the job complete while any required gate is red, stale, or unproven.

---

# Scope gate

Before shipping inspect the project diff and commit.

Confirm:

* only current-job work is present
* no next-job work is present
* no unrelated refactor is included
* no unrelated dependency upgrade is included
* no unrelated cleanup is included
* no temporary debug artifact is included
* no placeholder feature is included
* no secret is included
* no accidental deletion is included
* no bypassed check is included

If mixed scope exists:

* do not ship
* split the work or remove unrelated changes
* do not hide the mixed scope by modifying the recipe
* do not mark the job complete

A green mixed-scope commit is still not an acceptable job-scoped release.

---

# Product decision gate

No unresolved decision may block the behavior being shipped.

If the current recipe depends on undefined behavior:

* do not invent a product decision
* do not silently select one interpretation
* record the open question
* stop shipping
* route to the appropriate planning/decision workflow

A release cannot be considered complete when its expected behavior is still materially ambiguous.

---

# Green engineering gate

Run or reuse valid evidence for:

* lint
* typecheck
* relevant tests
* production build

Use the real commands from:

`03-your-product/architecture.md → Host`

Do not substitute a different command merely because it is convenient.

When tests are available, include the tests relevant to the current job.

When database migrations or other specialized validation are part of the architecture, include the required checks.

A production build passing does not replace:

* tests
* security validation
* acceptance verification
* live production proof

---

# Pass-through rule

If `/verify` already returned PASS for this job in this session and:

* no project source files changed
* no relevant configuration changed
* no relevant environment behavior changed
* the intended release commit has not changed
* the production deployment remains the same
* the recipe has not materially changed
* the selected persona has not materially changed

reuse the verified checks and evidence.

Do not re-run checks merely for ceremony.

However, if any of the following changed, invalidate the affected evidence:

* source code
* package/dependency state
* lockfile
* configuration
* deployment
* environment configuration
* commit
* production branch state
* recipe
* selected frontend/backend prompt
* deployment identity

Re-run the necessary gates.

---

# Git repository gate

Before committing or pushing:

1. Confirm the working directory is the project folder.
2. Confirm the Git repository is the expected project repository.
3. Confirm the remote matches `Architecture → GitHub repo`.
4. Confirm the current branch matches the configured production workflow.
5. Inspect `git status --short --branch`.
6. Inspect the relevant diff.
7. Identify staged and unstaged changes.
8. Identify untracked files.
9. Confirm scope.
10. Confirm no secrets or sensitive artifacts are present.

Do not silently switch repositories.

Do not silently switch branches.

Do not silently modify the production branch configuration.

---

# Staging gate

Stage only files belonging to the current job.

Prefer:

`git add <specific-files>`

Never blindly run:

`git add .`

If using `git add -u`, first confirm that there are no intended new files.

After staging inspect:

* `git status`
* `git diff --cached --stat`
* `git diff --cached`

Confirm the staged set is exactly what the current job requires.

Do not commit:

* secrets
* `.env` secrets
* credentials
* private keys
* production dumps
* customer data
* debug artifacts
* unrelated files
* generated junk

---

# Commit gate

The project repository must contain a precise current-job commit.

Use a message such as:

`git commit -m "feat: precise imperative message"`

The commit message must communicate the actual intent.

Do not create:

* empty commits
* unrelated mixed commits
* meaningless "update" commits
* broad catch-all commits

Record the resulting commit SHA.

That SHA is the intended release identity.

---

# Synchronization gate

Before pushing, ensure the local branch is synchronized safely with the configured remote.

Use fast-forward-only synchronization where bringing remote `main` into local history is required.

Prefer:

`git pull --ff-only origin main`

Do not silently resolve divergent history.

If the branch diverged:

* stop
* preserve local work
* report the divergence
* do not force-push
* do not rewrite shared production history
* do not discard commits

If a synchronization step changes application source/configuration:

* the previous green checks may no longer be sufficient
* re-run the affected checks
* re-establish verification before shipping

---

# Push gate

Push only the intended current-job commit.

Use:

`git push origin main`

Never use:

`git push --force`

Do not rewrite production history.

Respect:

* branch protection
* required checks
* required reviews
* repository rules
* deployment rules
* permission restrictions

If the repository rejects the push because a required policy is not satisfied:

* do not bypass it
* do not weaken the repository configuration
* do not force the push
* report the exact blocker
* follow the configured repository integration path

---

# Remote commit verification

After push, confirm:

* push succeeded
* expected branch advanced
* remote points to the intended release commit
* no unexpected commit superseded the release
* no intended project changes remain uncommitted
* no unrelated changes entered the release

The release commit must be recorded for production correlation.

Do not assume the remote branch being updated means production is updated.

---

# Vercel deployment gate

After the project commit is pushed:

1. Identify the corresponding Vercel deployment.
2. Confirm deployment completed successfully.
3. Confirm it belongs to the expected project.
4. Confirm deployed commit matches the intended release commit.
5. Confirm the production deployment is serving the expected release.
6. Confirm the configured production URL.
7. Open the production URL.
8. Perform the required live verification.

Do not report success merely because the deployment status says:

> Ready

without confirming that it corresponds to the intended release.

Do not accept:

* unrelated deployments
* older deployments
* preview deployments
* stale browser results

as proof of the current release.

---

# Deployment identity gate

The following must agree:

`Project repository`
`+`
`Release commit`
`+`
`Vercel deployment`
`+`
`Production URL`

If any identity cannot be established:

* do not ship
* do not mark the job complete
* record the missing evidence
* resolve through verification/debugging

A successful deployment of the wrong commit is not a successful release.

---

# Production proof gate

Open the Vercel production URL and verify the actual product.

Do not use:

* localhost
* local development
* local screenshots
* build output
* GitHub commit alone
* preview URL

as final proof.

The final release proof must be:

`Exact commit`
→ `Production deployment`
→ `Production URL`
→ `Observed production behavior`

---

# Independent verification gate

`/verify` is an independent release-verification process.

The ship owner must confirm the latest relevant `/verify` result:

* belongs to the current job
* belongs to the intended release
* was performed against the correct production deployment
* passed every required recipe item
* contains no unresolved required item
* has not been invalidated by later changes

Do not replace `/verify` with a casual manual glance.

Do not reinterpret a failed `/verify` as PASS.

Do not weaken the recipe after verification failure.

---

# Frontend release gate

For frontend jobs, production must visibly satisfy the exact selected frontend direction and recipe.

Verify, as applicable:

* visual thesis
* selected persona direction
* signature element
* typography
* surfaces
* spacing
* vertical rhythm
* composition
* responsive recomposition
* navigation
* interaction states
* motion
* reduced motion
* accessibility
* no broken routes
* no dead controls
* no obvious console/runtime errors
* no accidental horizontal overflow
* no major layout instability

The frontend must not merely contain technically valid components.

It must satisfy the project's selected frontend engineering/design system.

---

# Backend release gate

For backend jobs, production must satisfy the exact selected backend direction and recipe.

Verify, as applicable:

* API contracts
* validation
* authentication
* authorization
* ownership
* tenant boundaries
* data integrity
* bounded/paginated responses
* typed/user-safe errors
* idempotency
* retry behavior
* failure handling
* observability
* secrets handling
* integration behavior

Do not mark backend work shipped merely because the endpoint responds successfully once.

---

# Full-stack release gate

For full-stack jobs, verify the complete user workflow:

`Frontend action`
→ `API request`
→ `Backend validation`
→ `Authorization`
→ `Data/integration`
→ `Response`
→ `Frontend state`
→ `Final outcome`

Verify applicable:

* loading
* validation
* success
* empty
* error
* retry
* permission rejection
* refresh
* persistence
* direct-link behavior
* recovery

For feature pairs, both sides must be compatible.

---

# Manual test checklist gate

For a full-stack backend job whose recipe contains a frontend `Pair`:

* confirm the manual test checklist exists under `Manual Test Checklist`
* confirm it covers the completed feature pair
* confirm each listed item is user-testable
* confirm all items are complete before final release closure
* confirm issues discovered by the user route to `/debug`

Do not mark the feature pair closed while required manual test items remain untested.

---

# Migration and data gate

When the job changes database/schema/data behavior, verify:

* migration requirements
* deployment ordering
* application/schema compatibility
* required backfill
* data integrity
* relevant rollback/recovery considerations
* background-job compatibility where applicable

Do not mark a data-related release safe merely because the migration command succeeded.

If the change includes irreversible data operations:

* identify them
* confirm they are explicitly required
* confirm rollback implications are documented
* confirm residual risk

---

# Configuration gate

When the release changes runtime configuration:

* confirm required environment variables exist
* confirm names match Architecture
* confirm secrets are not exposed
* confirm public/client-exposed variables are intentionally public
* confirm production values are appropriate
* confirm configuration changes are compatible with the deployed application

Do not store or report secret values in the release record.

---

# Security gate

Before shipping, confirm the release does not introduce obvious:

* secret exposure
* authentication bypass
* authorization bypass
* tenant isolation failure
* unsafe user-content rendering
* sensitive error leakage
* insecure debug behavior
* disabled security checks
* unsafe dependency configuration

This is not a replacement for a dedicated security assessment.

It is the release gate against obvious and known security regressions.

---

# Rollback gate

For changes with material risk, identify the actual rollback mechanism.

Where appropriate record:

* known-good deployment
* known-good commit
* rollback procedure
* migration implications
* configuration implications
* external integration implications
* background-job implications

A code rollback is not automatically a data rollback.

Do not claim rollback is understood merely because an older Git commit exists.

---

# Production observation gate

After deployment, open the exact production URL.

For affected functionality verify:

* route availability
* expected behavior
* critical navigation
* relevant interactive states
* backend response
* error behavior
* console/runtime health
* relevant network failures
* responsive behavior for UI jobs
* authentication/authorization where safe
* relevant recovery path

For frontend jobs, check representative mobile and desktop widths.

For backend jobs, use safe non-destructive production verification.

Do not create destructive production conditions merely to prove the release.

---

# Residual risk gate

Before closing the job, record any remaining:

* technical limitation
* untested edge case
* external dependency limitation
* performance uncertainty
* browser limitation
* operational risk
* rollback limitation
* manual operational requirement

Residual risk does not automatically block shipping.

However, it must not be hidden.

If a residual risk violates a required release gate, do not ship.

---

# Build-plan closure

Only after all release gates pass:

1. mark the current job complete in `03-your-product/00-build-plan.md`
2. fill:

   * Deployed commit
   * Verified URL
3. update `progress-tracker.md`
4. record:

   * deployed commit
   * production URL
   * evidence
   * residual risk
   * release result
5. set `Next Up` to the first genuinely unfinished job
6. do not accidentally rewrite unrelated build-plan state

The next job must remain untouched.

---

# Discipline repository update

After the project release succeeds:

1. inspect the discipline repository separately
2. update only the required truth/plan/tracker files
3. inspect the discipline diff
4. confirm no project source is staged
5. commit only the discipline truth update
6. push the discipline repository using its configured workflow
7. keep project and discipline commits separate

Never stage the discipline repository from the project repository.

Never stage project source from the discipline repository.

Never mix their histories.

---

# Final state validation

Before reporting shipped, verify:

### Project

* correct project repository
* correct branch
* exact release commit
* clean working tree
* correct remote
* push succeeded

### Deployment

* correct Vercel project
* successful production deployment
* deployed commit matches release commit
* production URL is correct

### Verification

* `/verify` PASS
* evidence corresponds to the release
* no stale evidence
* all required recipe items proved

### Truth

* build plan updated correctly
* progress tracker updated correctly
* no unrelated truth changes
* Next Up is correct

### Risk

* rollback understood where necessary
* residual risks recorded

Only after all applicable categories pass should the job be reported as shipped.

---

# Failure behavior

### Red command

If lint, typecheck, tests, build, or required validation fails:

* do not ship
* do not push red work
* route to `/debug`

### Deployment failure

If Vercel production deployment fails:

* do not ship
* preserve the project evidence
* report the deployment failure
* route to `/debug`

### Commit/deployment mismatch

If Vercel deployment does not correspond to the intended release commit:

* do not ship
* do not mark complete
* investigate deployment identity
* route to `/verify` or `/debug` as appropriate

### Live mismatch

If deployment succeeds but production behavior disagrees with the recipe:

* do not ship
* do not weaken the recipe
* route to `/debug`

### Missing evidence

If a required condition cannot be proven:

* do not ship
* record exactly what is unproven
* do not substitute assumption for evidence

### Secret detected

If a secret is found:

* stop
* do not push
* remove/rotate as appropriate
* verify the repository is clean
* restart the necessary security/release checks

### Mixed scope

If unrelated work is present:

* do not ship
* separate the scope
* do not hide it in the recipe

### Product ambiguity

If a required behavior depends on an unresolved product decision:

* do not invent the behavior
* add the focused open question
* stop shipping

Do not mark the job complete, start the next job, or report shipped while any required gate is red.

---

# Never

* Never generate a replacement ship prompt
* Never paraphrase the permanent ship prompt
* Never ship red work
* Never ship unverified work
* Never ship a different job because it became the first unfinished job
* Never infer the current release target from build-plan order when command context identifies another job
* Never mark a job complete before release gates pass
* Never treat a green build as production proof
* Never treat a Git push as deployment proof
* Never treat a Vercel deployment as proof without commit correlation
* Never use localhost as final proof
* Never use a preview deployment as final proof
* Never reuse stale `/verify` evidence
* Never use an older screenshot for a newer deployment
* Never hide a defect by weakening the recipe
* Never fix defects inside `/ship`
* Never write feature code inside `/ship`
* Never add unrelated changes
* Never create an empty commit
* Never force-push
* Never rewrite shared production history
* Never bypass GitHub branch/repository protections
* Never commit secrets
* Never commit `.env` secrets
* Never mix project and discipline repositories
* Never mutate destructive production data merely to prove release readiness
* Never claim rollback is understood without identifying the actual recovery path
* Never claim shipped while required evidence is missing
* Never start the next job during `/ship`

---

# Completion report

Report:

* shipped job
* recipe path
* job Layer
* Pair when applicable
* project repository
* branch
* project commit
* green checks and reused pass-through checks
* Vercel deployment
* deployed commit
* Vercel production URL
* production verification result
* `/verify` result
* recipe/build-plan status
* progress-tracker update
* manual test checklist status when applicable
* rollback note
* residual risk
* Next Up

The completion statement must distinguish:

* code committed
* code pushed
* deployed
* independently verified
* shipped

Do not use "shipped" as a synonym for merely "pushed."

---

# Core principle

`/ship` is the final release gate.

A job is shipped only when:

`Correct Job`
→ `Correct Scope`
→ `Green Checks`
→ `Correct Commit`
→ `Correct Remote`
→ `Correct Vercel Deployment`
→ `Correct Production URL`
→ `Independent Verification`
→ `Truth Update`
→ `Release Closure`

If any link is missing, the job is not shipped.
