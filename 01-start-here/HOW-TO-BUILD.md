# How to develop

# Folders (open in this order)

* `01-start-here` — you are here
* `02-fill-these-prompts` — discover and write the project blueprint, then write the product truth
* `03-your-product` — files you replace
* `04-always-on-rules` — one frontend prompt library, one backend prompt library, recipe format
* `05-slash-commands` — slash commands (live proof is Vercel, never localhost)
* `{project-name}/` — the app, created after files are ready
* `IMPROVE.md` — paste later upgrades. Follow **New feature later**

# Where are you?

Pick one heading below. Ignore the rest.

* No idea yet → **Start from nothing**
* Project Blueprint is being discovered → **Project Blueprint**
* Files in `03-your-product` are filled → **Files are ready**
* GitHub and Vercel already exist, you are building → **Next job**
* Lint, types, or `npm run build` is red → **Build error**
* Vercel deploy failed → **Vercel failed**
* URL is live but the page is wrong → **Live page is wrong**
* You want a new feature, or `IMPROVE.md` has new text → **New feature later**
* Bug or tidy, no new feature → **Fix or clean**

# Project Blueprint

Before stack selection, theme selection, code standards, build planning, repository creation, or application development, establish the complete enough **Project Blueprint** for the project.

The Blueprint is the project's product-level source of truth before implementation-specific decisions.

It must establish, where applicable:

* product identity
* problem
* target users and actors
* responsibilities and permissions
* goals and outcomes
* value
* scope
* non-goals
* capabilities and feature purpose
* end-to-end workflows
* business rules
* entity lifecycles
* important state transitions
* data and information requirements
* external systems and dependencies
* security and trust boundaries
* failure behavior
* recovery behavior
* cancellation behavior
* retry behavior
* timeout behavior
* partial-completion behavior
* concurrency considerations
* scale expectations when material
* platform and device requirements
* localization
* accessibility
* notifications and communication
* payments and financial behavior when applicable
* content lifecycle when applicable
* administration and operations
* quality requirements
* success criteria
* limitations
* constraints
* assumptions
* unknowns
* risks and mitigations
* important decisions and trade-offs
* validation and acceptance requirements
* MVP boundaries
* future-phase boundaries

The Blueprint must distinguish:

* confirmed facts
* user requirements
* assumptions
* unknowns
* constraints
* decisions
* risks
* recommendations
* out-of-scope work

Do not invent missing requirements.

Do not select technologies during product discovery unless the user explicitly mandates one.

Do not force irrelevant blueprint categories onto a small or simple product.

The Blueprint is complete enough when downstream decisions can be made without guessing about material product behavior.

# Blueprint workflow

For a new project:

1. Capture the user's raw idea and all context already provided.
2. Identify the product problem, users, outcomes, scope, and major capabilities.
3. Identify complete workflows rather than only screens or features.
4. Identify business rules, permissions, lifecycle states, and important transitions.
5. Identify required data and external dependencies.
6. Identify important security, reliability, failure, and recovery behavior.
7. Identify meaningful limitations and constraints.
8. Identify assumptions and unknowns.
9. Identify significant risks and trade-offs.
10. Establish observable or testable success criteria.
11. Resolve contradictions.
12. Determine whether remaining unknowns are blocking or non-blocking.
13. Produce the confirmed project understanding.
14. Only then begin the six-file product-truth pipeline.

When a missing fact is non-blocking:

* label the assumption clearly
* continue

When a missing fact is blocking:

* add it to `03-your-product/progress-tracker.md` under Open Questions
* stop the affected decision
* do not invent the answer

# Blueprint quality gate

Do not leave Blueprint discovery until:

* the problem is understood
* the intended outcome is understood
* meaningful users and actors are identified
* important permissions are understood
* scope and non-goals are explicit
* major capabilities have a reason to exist
* important workflows are understood
* important business rules are identified
* important states and transitions are understood
* required data is identified
* required dependencies are identified
* important security boundaries are understood
* important failure and recovery paths are understood
* meaningful constraints and limitations are visible
* assumptions and unknowns are visible
* significant risks are identified
* success can be observed or tested

Do not demand unnecessary detail merely to satisfy a checklist.

# Ready gate

Do not create a repo. Do not create a project folder. Do not run `/develop`. Not until all of this is true.

`/brief` and `02-fill-these-prompts/01-idea.md` never create a GitHub repo. `/ship` never creates a GitHub repo. The repo is created only under **Files are ready**.

The Project Blueprint must already be sufficiently established.

Then:

* `03-your-product/project-overview.md` is real. No `[placeholders]`
* `03-your-product/architecture.md` is real. Backend selections are written
* `03-your-product/ui-context.md` is real. Frontend selections are written
* `03-your-product/code-standards.md` is real
* `03-your-product/00-build-plan.md` has real jobs (`01-…`, `02-…`)
* `03-your-product/frontend-prompt.md` is real
* `03-your-product/backend-prompt.md` is real
* Generated frontend prompt contains exact selected sections from `04-always-on-rules/frontend-prompt.md`
* Generated backend prompt contains exact selected sections from `04-always-on-rules/backend-prompt.md`

# Start from nothing

First establish the **Project Blueprint**.

* Run `Idea-Prompt` → conduct the complete blueprint/discovery flow
* Use the user's idea and all already-provided context
* Do not ask the user to repeat information already known
* Ask only materially important questions
* Use clearly labeled assumptions for non-blocking unknowns
* Record blocking unknowns in `03-your-product/progress-tracker.md`
* Resolve material contradictions before downstream generation

After the Blueprint is sufficiently complete:

* Run `02-fill-these-prompts/01-idea.md` → convert the confirmed blueprint into `03-your-product/project-overview.md`
* Run `02-fill-these-prompts/02-stack.md` → choose backend prompt names → replace `03-your-product/architecture.md`
* Run `02-fill-these-prompts/03-theme.md` → choose frontend prompt names → replace `03-your-product/ui-context.md`
* Run `02-fill-these-prompts/04-standards.md` → replace `03-your-product/code-standards.md`
* Run `02-fill-these-prompts/05-jobs.md` → replace `03-your-product/00-build-plan.md`
* Run `02-fill-these-prompts/06-personas.md` → copy exact selected sections into both generated persona files
* Or run `/brief` (`05-slash-commands/brief.md`) to execute the product-truth pipeline

The Project Blueprint comes before these six files. It does not replace them.

Then go to **Files are ready**.

# Files are ready

This is when the app folder and GitHub repo are created. Not during Blueprint discovery. Not during `/ship`.

* Ask the AI for a kebab-case folder name from `03-your-product/project-overview.md` (example `raja-portfolio`)
* Create `{project-name}/` in the discipline root. App source, the app `README.md`, and `IMPROVE.md` live only there
* Never overwrite the discipline `README.md`
* Write the folder name into `03-your-product/architecture.md` under Host → Project folder
* You create a **new** GitHub repo for **that folder only**. Do not `git init` the discipline clone
* Import **that** repo into Vercel. Secrets in Vercel env. Write GitHub repo URL and Vercel Project URL into `03-your-product/architecture.md` Host
* Then go to **Next job**

# Next job

* Open `03-your-product/00-build-plan.md`
* Copy the first unfinished name. That is the only job
* No recipe file (example: `03-your-product/01-site-shell.md` missing) → `/architect` that name (`05-slash-commands/architect.md`)
* `/develop` that name only (`05-slash-commands/develop.md`). Code only in the project folder
* Check in the project folder: lint, types, tests, production build
* Red → go to **Build error**
* Green → one commit in the project folder → push that repo → wait for Vercel
* Vercel fails → go to **Vercel failed**
* Missing GitHub or Vercel URL → ask the user, write it in Host, then continue
* `/verify` on the Vercel production URL. Never localhost
* FAIL → `/debug`, deploy, `/verify` again
* PASS → `/ship`; only `/ship` marks the job done
* Repeat this heading until every row in `03-your-product/00-build-plan.md` is done

# Build error

* `/debug` (runs the permanent prompt through `05-slash-commands/debug.md`)
* Do not push while red
* Do not start the next job
* When the full green gate passes → commit in the project folder → push → `/verify` on the Vercel URL

# Vercel failed

* Open the Vercel log
* `/debug` and paste that log
* Push only when `npm run build` is green
* Open the Vercel URL again

# Live page is wrong

* `/debug` what you see on the Vercel URL vs the recipe in `03-your-product` (`01-….md` for this job)
* Check: lint, types, tests, production build
* Green → push the project folder repo
* Open the Vercel URL again, then `/verify`. Never localhost

# New feature later

If the project already exists, paste the request into `IMPROVE.md` or `{project-name}/IMPROVE.md`.

Do not restart discovery from zero.

First reconcile the requested change against the existing Project Blueprint and product truth.

Determine:

* what is changing
* what remains unchanged
* which users/actors are affected
* which workflows are affected
* which business rules are affected
* which states are affected
* which data or dependencies are affected
* whether architecture is affected
* whether UI behavior is affected
* whether existing limitations or constraints change
* whether new risks are introduced

Then:

* Add the feature to In Scope in `03-your-product/project-overview.md`
* Update the affected Blueprint/product-truth information before implementation
* Change `03-your-product/architecture.md` only if stack, data, auth, or host change
* Change `03-your-product/ui-context.md` only if visual rules change
* Run `02-fill-these-prompts/05-jobs.md` or add the next number by hand in `03-your-product/00-build-plan.md`
* Write app code only in the project folder. Do not create a new GitHub repo
* Go to **Next job**

Do not silently add a feature to the build plan while its product behavior is materially undefined.

# Git workflow

Follow this exact sequence every time you push code. All commands follow this automatically.

1. `git pull origin main` — sync before coding
2. `git status` — see what changed
3. `git add <specific-files>` or `git add -u` — stage explicitly, never blind `git add .`
4. `git commit -m "feat: precise imperative message"` — commit with intent
5. `git pull origin main` — safety pull before push
6. `git push origin main` — push clean history

* Never `git push --force`
* Never leave uncommitted changes while pulling. Commit or `git stash` first
* Never commit secrets, `.env` files, or debug artifacts

# Full-stack project

If the project has both frontend and backend, work feature by feature.

The Blueprint must already define the feature's important user flow and behavior before implementation.

1. `/architect` → frontend recipe for the feature (e.g., authentication pages)
2. `/develop` → build the frontend
3. `/debug` → only if red
4. `/verify` → prove frontend on Vercel. Marks recipe done
5. `/architect` → backend recipe for the same feature (e.g., auth API + connect to frontend)
6. `/develop` → build the backend and connect
7. `/debug` → only if red
8. `/verify` → prove backend on Vercel. Marks recipe done. Generates manual test checklist in `03-your-product/progress-tracker.md`
9. Manually test every item in the checklist on the live Vercel URL
10. Issue found → `/debug` with the issue description
11. All clear → `/ship` the feature pair
12. Repeat for the next feature

Frontend-only projects skip this and follow **Next job** directly.

# Fix or clean

* Bug → `/debug`
* Small change → `/develop` and name the files it may touch (`05-slash-commands/develop.md`)
* Check in the project folder: lint, types, tests, production build
* Green → push that repo
* `/verify` on the Vercel URL. Never localhost
* Do not add a new row to `03-your-product/00-build-plan.md`

# Blueprint preservation rule

The Project Blueprint remains the reference model throughout development.

Whenever implementation reveals:

* a missing requirement
* a missing workflow
* an undefined state
* an incorrect assumption
* a new constraint
* a new dependency
* a new limitation
* a new significant risk
* a contradiction in product truth

do not silently invent or ignore it.

Record the issue in `03-your-product/progress-tracker.md`.

Reconcile the affected product-truth documents before continuing when the issue materially changes expected behavior.

The Blueprint evolves with verified project knowledge; it does not become irrelevant after the initial planning stage.
