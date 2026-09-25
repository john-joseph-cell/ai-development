# Live check

Proof is the Vercel production URL. Never localhost. Never `npm run dev` as evidence.

Production proof must establish all of the following when a code change is being released:

* the intended project repository
* the intended current branch
* the intended release commit
* successful production deployment of that commit
* the production URL serving that deployment
* live behavior observed on that production URL

A URL that happens to load is not sufficient proof that the current change is deployed.

---

# Need

From `03-your-product/architecture.md` under Host:

* GitHub repo URL
* Vercel production URL (Project URL)

Also use:

* project folder named under Host
* configured production branch
* repository/branch information documented in Architecture
* current job identity when this command is called from `/develop`, `/debug`, `/verify`, `/audit`, or `/ship`

If either GitHub or Vercel URL is missing, stop and ask the user once. Write the answer into Host. Then continue.

Work only in the project folder named under Host.

Never run project Git commands from the discipline root when the project repository is a separate repository.

Never stage or commit discipline files together with project source.

---

# Repository identity

Before changing Git state, confirm:

* current directory is the project folder
* the expected Git repository is active
* the expected remote exists
* the expected remote URL matches `Architecture → GitHub repo`
* the expected production branch is being used
* the current branch is the branch documented for production
* the working tree is understood

Do not silently switch repositories.

Do not silently switch branches.

Do not silently change the configured production branch.

If repository identity disagrees with Architecture, stop and report the mismatch rather than guessing.

---

# Working-tree safety

Before any pull, merge, stage, commit, or push:

1. Run `git status --short --branch`.
2. Inspect the current working tree.
3. Determine whether every local change belongs to the current job.
4. Identify untracked files.
5. Identify modified tracked files.
6. Identify deleted files.
7. Identify suspicious/generated/debug files.
8. Check for secrets or environment files.
9. Check that no unrelated user work is present.

Never destroy, reset, discard, overwrite, or silently absorb unrelated local work.

Never use destructive commands such as:

* `git reset --hard`
* `git clean -fd`
* `git checkout -- .`
* `git restore .`

as a shortcut for making the working tree clean.

If unrelated uncommitted work exists, stop and preserve it.

If current-job changes are intended to be released, they must be deliberately staged and committed before synchronization with a remote branch when the working tree cannot safely be updated otherwise.

---

# Scope safety

Before staging:

* confirm the current job
* confirm the current recipe
* confirm the expected project folder
* confirm changed files belong to the current job
* exclude unrelated feature work
* exclude temporary/debug artifacts
* exclude generated junk unless explicitly required
* exclude secrets
* exclude `.env` files unless a project explicitly and safely tracks a non-secret example file

Do not widen scope during the push workflow.

Do not use Git cleanup operations to hide scope violations.

If unrelated changes are mixed into the working tree, separate them before committing or stop and report the problem.

---

# Pre-push security check

Before any project commit or push, inspect the change for:

* API keys
* access tokens
* private keys
* credentials
* `.env` files
* production secrets
* database dumps
* customer data
* sensitive fixtures
* personal data
* debug exports
* local configuration that should not be committed
* authentication bypasses
* disabled security checks
* accidentally exposed internal URLs or credentials

If a secret or sensitive artifact is present:

* stop
* do not push it
* remove it from the staged change
* rotate/revoke it when appropriate
* preserve evidence of the issue without exposing the secret in the report

Never push first and clean the secret later.

---

# Synchronization policy

Use Git synchronization deliberately.

Preferred principle:

`inspect → synchronize safely → inspect again → stage → inspect staged diff → commit → verify → push → verify remote → verify Vercel`

Do not assume the local branch is current merely because the last command succeeded.

Use fast-forward-only synchronization when bringing `main` into the local branch.

Prefer:

`git pull --ff-only origin main`

over an unrestricted pull.

`--ff-only` prevents Git from silently integrating divergent history through an automatic merge/rebase choice.

If the local branch and `origin/main` have diverged:

* do not force-push
* do not silently merge
* do not silently rebase
* do not discard local commits
* do not overwrite remote history

Stop and report the divergence so it can be resolved deliberately.

If the local branch is simply behind and a fast-forward is possible, synchronize safely.

If synchronization changes source/configuration files after the previous green checks, those checks are no longer automatically reusable. Re-run the appropriate green gate before pushing.

---

# Push

Follow this controlled sequence.

## Phase 1 — Inspect before synchronization

1. `git status --short --branch`
2. `git remote -v`
3. confirm the expected remote URL
4. confirm the expected branch
5. inspect the current diff
6. inspect untracked files
7. confirm only current-job changes are present

Do not pull while the working tree contains unexplained changes.

If the current job's intended changes are not yet committed, continue to the staging/commit phase below rather than blindly pulling.

---

## Phase 2 — Stage intentionally

Use:

`git add <specific-files>`

or another explicitly scoped staging command.

Never use blind:

`git add .`

Prefer exact paths.

`git add -u` may be used only when you have already confirmed that every intended change is to an already-tracked file and there are no intended new files.

Do not assume `git add -u` captures new files.

Always inspect staged state after staging.

Run:

* `git status`
* `git diff --cached --stat`
* `git diff --cached`

Confirm:

* only intended files are staged
* no secret is staged
* no unrelated feature is staged
* no debug artifact is staged
* no generated junk is staged
* no disabled-check workaround is staged
* no accidental deletion is staged

If the staged diff is wrong, unstage/re-stage intentionally.

---

## Phase 3 — Commit

Create a precise current-job commit:

`git commit -m "feat: precise imperative message"`

The message must describe the actual job/change.

Examples:

* `feat: add workspace invitation flow`
* `fix: preserve checkout state on payment retry`
* `feat: add document ingestion status`
* `fix: prevent duplicate webhook processing`

Do not create:

* empty commits
* meaningless commits
* broad catch-all messages
* unrelated mixed-scope commits

Before committing, confirm the staged diff represents the intended release.

---

## Phase 4 — Re-synchronize safely

After the intended change is committed:

1. inspect Git status
2. fetch/synchronize `main` safely
3. ensure the local branch is not unexpectedly divergent
4. use fast-forward-only behavior where applicable
5. do not silently merge or rebase divergent history

If the remote `main` advanced while this work was being prepared:

* fast-forward safely if the local branch can do so without divergence
* if histories diverged, stop
* do not force-push
* do not rewrite history to make the push succeed

If a synchronization step changes project source/configuration after the calling command's last green checks, those checks must be treated as stale.

Return to the calling command's verification/green gate before pushing.

---

## Phase 5 — Final pre-push inspection

Before pushing, verify:

* current branch is correct
* remote is correct
* working tree has no unintended changes
* intended commit exists
* commit contains only current-job work
* no secret is present
* no unrelated work is included
* required checks are green or have valid same-session evidence
* deployment is expected to use this branch/commit

Record the release commit SHA.

That SHA becomes the identity of the release being pushed and later verified.

---

## Phase 6 — Push

Push the configured production branch:

`git push origin main`

Never:

`git push --force`

Never:

`git push --force-with-lease`

unless an explicit repository recovery procedure outside this discipline has been approved and requires it.

This discipline must not bypass repository protection or rewrite shared production history.

If GitHub rejects the push because of:

* branch protection
* required checks
* review requirements
* deployment requirements
* repository rules
* permissions
* current branch restrictions

do not bypass the protection.

Follow the repository's configured integration path or stop and report the exact blocker.

Do not weaken repository rules merely to get the command to finish.

---

# Remote verification

After a successful push:

1. confirm the push succeeded
2. confirm the expected remote branch advanced
3. confirm the remote branch points to the intended release commit
4. confirm no unexpected additional commit replaced or superseded it
5. confirm the repository state is clean

Do not treat:

> "git push succeeded"

as proof that the production deployment uses that commit.

The release commit and deployment commit must be correlated separately.

---

# Vercel deployment verification

Do not assume push equals production deployment success.

After pushing:

1. identify the production deployment triggered by the release
2. confirm deployment completed successfully
3. confirm the deployed commit corresponds to the intended release commit
4. confirm the production deployment is actually serving the expected project
5. obtain the Vercel production URL
6. open the production URL
7. verify the live product behavior relevant to the current command

Do not accept:

* a preview deployment
* an unrelated deployment
* an older deployment
* a stale browser page
* a local development server

as proof of the current release.

If the deployed commit does not match the intended release commit:

* do not report success
* identify the deployment mismatch
* inspect the deployment history/trigger
* route to the appropriate verification/debugging process

---

# Production proof

The Vercel production URL is the final product proof.

Never use:

* localhost
* `npm run dev`
* a local browser
* a local screenshot
* a preview deployment
* a build log alone
* a GitHub commit alone

as final live proof.

For a current-job release, prove:

`release commit`
→ `production deployment`
→ `production URL`
→ `observed live behavior`

For frontend work, inspect the actual deployed UI.

For backend work, exercise the relevant production-safe behavior or inspect appropriate production evidence.

For full-stack work, verify the complete user-visible flow when safely possible.

---

# Frontend live proof

When the command concerns frontend work, inspect the production URL at representative widths.

At minimum, where applicable:

* mobile
* tablet
* desktop
* wide desktop

Verify:

* affected route loads
* normal navigation works
* direct route access works
* responsive composition works
* selected visual direction is present
* signature element is present
* selected motion works
* interaction states work
* keyboard focus works
* reduced-motion behavior works
* no horizontal overflow
* no obvious layout shift
* images load correctly
* critical fonts/assets load correctly
* no broken navigation
* no dead buttons
* no obvious console/runtime errors

Do not treat a screenshot as sufficient proof by itself.

The page must be interactively observed on the production deployment.

---

# Backend live proof

When the command concerns backend behavior, verify safely:

* expected request/result
* validation
* authentication
* authorization
* ownership/tenant boundary
* pagination/bounded data
* safe error response
* no secret/stack leakage
* appropriate retry/idempotency behavior
* relevant integration behavior
* relevant production runtime evidence

Never use destructive production actions merely to prove a test.

Do not mutate:

* real customer data
* real financial records
* real payment state
* irreversible production resources

solely for verification.

Use safe fixtures or non-destructive paths where possible.

---

# Full-stack live proof

When the job is full-stack, verify the feature as a complete system:

`UI action`
→ `request`
→ `backend behavior`
→ `data/result`
→ `UI state`
→ `success/error/recovery`

Where appropriate verify:

* loading
* success
* empty
* error
* retry
* validation
* permission rejection
* refresh behavior
* direct-link behavior
* persistence
* recovery

Do not verify frontend and backend independently when the recipe requires them to work together.

---

# Evidence freshness

Production evidence is commit-sensitive.

Do not reuse previous production evidence after the deployed commit changes.

If source changes after verification:

* invalidate the affected previous evidence
* re-run the necessary checks
* re-confirm the relevant production behavior

A screenshot, browser result, or verification from an older deployment does not prove a newer commit.

---

# Failure handling

If Git fails:

* inspect the exact failure
* do not force the operation
* do not destroy local work
* do not silently rewrite history
* report the blocking condition

If Vercel deployment fails:

* do not report shipped
* preserve the release commit
* capture the deployment failure
* route to `/debug` where appropriate

If deployment succeeds but live behavior is wrong:

* do not rewrite truth files to match the defect
* route to `/verify` or `/debug` as appropriate

If the live URL is unreachable:

* distinguish deployment failure from application failure from network/access limitation
* do not claim PASS without evidence

---

# No-empty-push rule

Do not create an empty commit.

Do not push when:

* no project file changed
* no intended release commit exists
* only unrelated changes exist
* only generated noise changed
* only local metadata changed without a legitimate reason

If the desired result already exists in the remote production deployment and no project files changed, report that no push was necessary.

---

# Commit scope rule

One release operation should correspond to the current job.

Do not combine:

* current job
* next job
* unrelated refactor
* unrelated dependency upgrade
* unrelated cleanup
* unrelated design redesign

into one push.

If the working tree contains mixed work, split it or stop.

---

# Discipline repository separation

The project repository and discipline repository are separate systems.

When a command updates:

`03-your-product`

those truth-file changes belong to the discipline repository, not the project repository, when the discipline architecture defines them that way.

Never accidentally:

* stage discipline files in the project repository
* commit project source in the discipline repository
* push one repository's changes to the other
* copy project credentials into the discipline repository

When updating discipline truth after a command:

1. inspect the discipline repository separately
2. stage only the intended truth files
3. inspect its diff
4. commit only the truth update
5. push only its configured remote
6. do not mix that commit with application source

---

# Pass-through rule

If the previous command in this session already:

* committed the intended project change
* pushed it
* confirmed the corresponding Vercel production deployment
* confirmed the deployed commit
* and no project source/configuration files changed afterward

do not repeat the entire push/deployment sequence.

Use the existing evidence.

However, if:

* the deployed commit changed
* source/configuration changed
* the branch advanced
* deployment status changed
* evidence is stale
* the production URL changed
* or a relevant truth file changed

revalidate the affected release state.

---

# Production URL rule

After:

* `/develop`
* `/debug`
* `/verify`
* `/audit`
* `/ship`

open the Vercel production URL when the command's purpose requires live proof.

Cite/report the exact production URL used.

Never report a different URL merely because it is easier to access.

---

# Deployment identity rule

Whenever reporting a successful release, report all applicable identities:

* job
* branch
* project repository
* release commit
* Vercel deployment
* production URL

Do not collapse these into a vague:

> "deployed successfully"

statement.

---

# Rollback awareness

For any release with material risk, know how the deployment can be rolled back.

Where the platform supports deployment promotion/rollback, identify the known-good deployment or commit that would be used.

Do not claim that rollback is understood merely because Git history exists.

A rollback must consider:

* application code
* database migrations
* environment/configuration changes
* external integrations
* irreversible data changes
* background jobs
* compatibility

A code rollback does not automatically undo an irreversible data mutation.

---

# Live-check completion report

Report:

* project folder
* current branch
* GitHub repo URL
* release commit
* push result
* Vercel deployment result
* deployed commit
* Vercel production URL
* live proof performed
* any checks reused through pass-through
* any blocker or residual risk

If something could not be verified, say exactly what remains unproven.

Do not convert missing evidence into PASS.

---

# Never

* Never use localhost as production evidence
* Never use `npm run dev` as production evidence
* Never use a preview URL as production proof
* Never force-push
* Never rewrite shared production history
* Never blindly `git add .`
* Never assume `git add -u` captures new files
* Never pull blindly over unexplained local changes
* Never silently merge divergent production history
* Never silently rebase shared production history
* Never discard unrelated user work
* Never commit secrets
* Never commit `.env` secrets
* Never mix project and discipline repositories
* Never create an empty commit
* Never push red work
* Never report a deployment without verifying the deployment
* Never report a deployment as the current release without matching its commit
* Never treat an old screenshot as proof of a newer deployment
* Never mark live behavior as verified from localhost
* Never change product truth files merely to make broken behavior appear correct
* Never bypass GitHub branch protections or required checks
* Never weaken repository or deployment controls to force a release
* Never claim production success without production evidence

---

# Core principle

The purpose of `/live` is not merely to push code.

It is to establish a trustworthy chain:

`Correct project`
→ `Correct job`
→ `Correct files`
→ `Correct commit`
→ `Correct remote branch`
→ `Correct Vercel deployment`
→ `Correct production URL`
→ `Correct live behavior`

Break the chain whenever evidence is missing.

Do not guess.

Do not silently repair the evidence.

Do not call the release live until the live system itself proves it.
