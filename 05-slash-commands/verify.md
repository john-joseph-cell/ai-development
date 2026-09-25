# /verify

Run the permanent independent verification prompt.

Verification is evidence gathering, not feature development.

The current job is the only verification target.

Do not verify a different job merely because it is now the first unfinished job.

---

# Read

* `05-slash-commands/verify-prompt.md`
* `05-slash-commands/live.md`
* current job recipe
* `03-your-product/00-build-plan.md`
* `03-your-product/project-overview.md`
* `03-your-product/architecture.md`
* `03-your-product/ui-context.md` when UI is in scope
* `03-your-product/progress-tracker.md`
* generated `frontend-prompt.md` when frontend is in scope
* generated `backend-prompt.md` when backend is in scope
* relevant current project state

---

# Do

* Follow `verify-prompt.md` exactly
* Establish the exact current job before testing
* Use the current recipe as the acceptance contract
* Verify every required recipe item
* Produce its evidence matrix
* Use the Vercel production deployment as final live proof
* Confirm the production deployment corresponds to the intended release commit
* Confirm verification evidence belongs to the current deployment
* If the previous command in this session already ran lint, typecheck, tests, and production build with all passing, and no source/configuration files changed since, skip re-running unchanged checks
* If valid deployment evidence already exists for the same commit and no relevant project state changed, use the pass-through rule from `verify-prompt.md`
* Perform frontend quality proof when the job affects UI
* Perform backend quality proof when the job affects backend behavior
* Perform complete full-stack proof when the recipe is a full-stack feature
* Distinguish PASS, FAIL, and UNPROVEN evidence
* Return PASS only when every required item has sufficient evidence on the correct production deployment
* On PASS: mark the recipe Status as Done in `03-your-product/00-build-plan.md`
* On PASS: fill `Deployed commit` and `Verified URL`
* On PASS for a full-stack backend job with a frontend Pair: generate the required manual test checklist in `03-your-product/progress-tracker.md` under `Manual Test Checklist`
* Ensure the manual checklist contains user-testable actions for the completed feature pair
* Route failed or unproven implementation behavior to `/debug`
* Route undefined/blocking product behavior to the appropriate planning/decision workflow
* Preserve the distinction between verification and final release closure

---

# Job identity rule

The job being verified must be:

* explicitly requested by the user, or
* the active job established by the command workflow

Do not infer a new target merely because:

* `/verify` previously marked another job Done
* the build plan's first unfinished job changed
* another recipe is available
* another deployment exists

If the current job cannot be determined reliably, stop and resolve job identity before verification.

---

# Production proof rule

Final verification must use the Vercel production deployment.

Never use as final production proof:

* localhost
* `npm run dev`
* local browser behavior
* preview deployment
* screenshot alone
* build output alone
* GitHub commit alone

The final chain must be:

`Recipe`
→ `Checks`
→ `Release Commit`
→ `Vercel Deployment`
→ `Production URL`
→ `Observed Production Behavior`

---

# Evidence freshness rule

Do not reuse production evidence from an older release.

Invalidate affected evidence when:

* source changes
* configuration changes
* dependencies change
* lockfile changes
* relevant environment behavior changes
* deployment changes
* deployed commit changes
* recipe changes materially
* selected persona changes materially

A previous PASS is not proof of a later source state.

---

# No-fix rule

Do not:

* fix defects
* write feature code
* redesign UI
* modify backend behavior
* weaken the recipe
* modify personas to hide mismatches
* invent product behavior

Verification must not repair the thing it is verifying.

If a defect is found, record the exact evidence and route it to `/debug`.

---

# No-scope-expansion rule

Verify only the current job and the related acceptance scope.

Do not turn verification into:

* general refactoring
* architecture redesign
* unrelated accessibility work
* unrelated SEO work
* unrelated performance optimization
* unrelated dependency cleanup
* future-feature testing

Check adjacent behavior only when the current job's change could reasonably affect it.

---

# Production-safety rule

Never use destructive production actions merely to prove a verification item.

Do not intentionally:

* delete real customer data
* modify real financial state
* issue real refunds
* corrupt production data
* disable security
* revoke real users
* trigger dangerous external actions

Use safe fixtures, non-destructive paths, logs, runtime evidence, or appropriate non-production tests when necessary.

---

# PASS rule

Return PASS only when:

* the correct job was verified
* the correct recipe was used
* all required recipe items have sufficient evidence
* the evidence belongs to the correct release/deployment
* required engineering checks are green or validly passed through
* applicable frontend/backend requirements are proven
* applicable production behavior is proven
* no required item is merely assumed
* no required item is only UNPROVEN

A green build does not automatically produce PASS.

A successful deployment does not automatically produce PASS.

A visually correct page does not automatically produce PASS if backend behavior is required.

---

# FAIL / UNPROVEN rule

### FAIL

The observed system contradicts the requirement.

### UNPROVEN

The requirement could not be sufficiently established.

Both prevent PASS when the item is required.

Do not downgrade UNPROVEN into PASS merely because there is no evidence of failure.

---

# On FAIL

When verification fails:

* leave the job incomplete
* do not mark it verified
* do not modify application source
* record the exact failed requirement
* record production URL
* record deployed commit
* record expected behavior
* record observed behavior
* record reproduction steps
* route to `/debug`

---

# On PASS

When verification passes:

1. Record PASS.
2. Confirm deployed commit.
3. Confirm production URL.
4. Mark recipe Status as Done in `03-your-product/00-build-plan.md`.
5. Fill `Deployed commit`.
6. Fill `Verified URL`.
7. Update required progress/truth information.
8. For a full-stack backend job whose recipe has a frontend Pair:

   * generate the manual test checklist in `03-your-product/progress-tracker.md`
   * include every relevant user-testable action for the completed feature pair
9. Do not mark unrelated jobs Done.
10. Do not start the next job.

---

# Verify → Ship handoff

A successful `/verify` proves the current job.

It does not perform final release closure.

After PASS:

`/ship`

is responsible for the final release gate and job closure workflow.

`/ship` must continue to target the same verified job and must not blindly replace it with a newly first-unfinished job.

---

# Never

* Never generate a replacement verify prompt
* Never fix defects during verification
* Never verify a different job
* Never use localhost as production proof
* Never use preview as production proof
* Never use a screenshot alone as production proof
* Never treat a green build as sufficient proof
* Never treat a successful push as sufficient proof
* Never treat deployment success as behavioral proof
* Never reuse stale evidence
* Never mark UNPROVEN as PASS
* Never modify application code during verification
* Never weaken a recipe to make it pass
* Never change personas to hide a mismatch
* Never invent product behavior
* Never perform destructive production testing
* Never mark a different job complete because the build-plan pointer changed
* Never start the next job
* Never close the release in place of `/ship`

---

# Completion report

Return:

* PASS or FAIL
* current job
* recipe path
* Layer
* Pair when applicable
* project repository
* branch
* deployed commit
* Vercel production URL
* checks run
* checks reused through valid pass-through
* acceptance evidence summary
* frontend evidence when applicable
* backend evidence when applicable
* evidence matrix
* recipe status update
* manual test checklist when generated
* exact failures and `/debug` reproduction steps when applicable
* evidence gaps when applicable
* residual risk/uncertainty when applicable
* next command

Do not say only:

> Verified.

State what was actually proven.

---

# Core principle

`/verify` independently proves the current job.

It must be possible to trace every PASS to evidence:

`Requirement`
→ `Expected Result`
→ `Action`
→ `Production Observation`
→ `Evidence`
→ `PASS`

No evidence means no PASS.
