# AI Developer Playbook

One product truth. One job at a time. Green build. Push. Prove it on Vercel.

---

# Project from scratch

No idea yet. Starting fresh.

## Project Blueprint

Before choosing the stack, theme, coding standards, or build jobs, establish the complete project blueprint.

The blueprint is the project's product-level source of truth. It must understand the project before implementation decisions are made.

The blueprint flow establishes:

1. Product identity and problem
2. Target users, actors, and responsibilities
3. Goals, outcomes, and value
4. Scope and explicit non-goals
5. Core capabilities and feature purpose
6. Complete end-to-end workflows
7. Business rules and permissions
8. Entity lifecycles and important state transitions
9. Data and information requirements
10. External services and dependencies
11. Security and trust boundaries
12. Failure, recovery, cancellation, retry, timeout, and partial-completion behavior
13. Scale and usage expectations where they materially affect the project
14. Platform, device, localization, and accessibility requirements
15. Notifications and communication behavior
16. Payments and financial behavior when applicable
17. Content lifecycle when applicable
18. Administration and operational requirements
19. Quality requirements and measurable success criteria
20. Known limitations and constraints
21. Assumptions and unknowns
22. Risks and mitigation
23. Important architectural/product decisions and trade-offs
24. Validation and acceptance requirements
25. MVP, later phases, and explicit future scope

The blueprint must distinguish:

- confirmed facts
- assumptions
- unknowns
- constraints
- decisions
- risks
- recommendations
- out-of-scope work

Do not jump from an idea directly to code.

Do not invent missing requirements.

Do not select technologies during product discovery unless explicitly required.

When the blueprint is sufficiently complete, use it to generate the six product-truth files below.

## Files to fill (in order)

The six files are generated only after the Project Blueprint has been established.

1. `02-fill-these-prompts/01-idea.md` → converts the confirmed blueprint into `03-your-product/project-overview.md`
2. `02-fill-these-prompts/02-stack.md` → choose backend names → replaces `03-your-product/architecture.md`
3. `02-fill-these-prompts/03-theme.md` → choose frontend names → replaces `03-your-product/ui-context.md`
4. `02-fill-these-prompts/04-standards.md` → replaces `03-your-product/code-standards.md`
5. `02-fill-these-prompts/05-jobs.md` → converts the product truth into `03-your-product/00-build-plan.md`
6. `02-fill-these-prompts/06-personas.md` → copies selected sections into `03-your-product/frontend-prompt.md` and `03-your-product/backend-prompt.md`

### Blueprint rule

`02-fill-these-prompts/01-idea.md` is not a shortcut around project discovery.

It must use the complete Project Blueprint established during discovery.

The resulting `project-overview.md` must preserve the blueprint's actual product intent, scope, workflows, rules, constraints, limitations, assumptions, and success criteria without inventing missing facts.

Or paste `Idea-Prompt` to run the complete blueprint/discovery flow, or run `/brief` to execute the product-truth pipeline.

Or paste `Idea-Prompt` to run the full interview, or run `/brief` to do all six in order.

# Blueprint completion gate

Do not move into architecture, theme, standards, jobs, repository setup, or application development until the blueprint is sufficiently understood.

At minimum, verify:

- problem and intended outcome are clear
- meaningful users/actors are identified
- scope and non-goals are explicit
- core workflows are understood
- important business rules are identified
- important states and lifecycle transitions are understood
- required data and dependencies are identified
- security and trust boundaries are understood
- important failure and recovery behavior is identified
- limitations and constraints are explicit
- assumptions and unknowns are visible
- major risks are identified
- success is observable or testable

Do not require every possible detail for a small project. The blueprint must be complete enough for responsible downstream decisions without forcing unnecessary complexity.


## After files are filled

1. Verify every file in `03-your-product` is real — no `[placeholders]`
2. Create `{project-name}/` folder inside this playbook root
3. Create a GitHub repo for that folder only
4. Import that repo into Vercel
5. Write the GitHub URL, Vercel URL, and project folder into `03-your-product/architecture.md` → Host

## Commands to follow

1. `/architect` — write the recipe for the first unfinished job
2. `/develop` — implement that recipe, green gate, push, wait for Vercel
3. `/debug` — only if build is red or Vercel fails
4. `/verify` — prove the job on the Vercel URL, marks recipe done
5. `/ship` — final release gate, updates tracker, names Next Up
6. Repeat from step 1 for the next job

---

# Improve existing project

Product already built. You want to add or change something.

## Where to paste

Paste your request into `IMPROVE.md` (root) or `{project-name}/IMPROVE.md`

## Steps

1. Add the feature to In Scope in `03-your-product/project-overview.md`
2. Change `03-your-product/architecture.md` only if stack, data, auth, or host change
3. Change `03-your-product/ui-context.md` only if visual rules change
4. Add new numbered jobs in `03-your-product/00-build-plan.md` (use `02-fill-these-prompts/05-jobs.md` or add by hand)
5. Clear the paste area in `IMPROVE.md` after jobs are queued

## Commands to follow

1. `/architect` — write the recipe for the new job
2. `/develop` — implement that recipe
3. `/debug` — only if red
4. `/verify` — prove on Vercel, marks recipe done
5. `/ship` — close the job
6. Repeat for each new job

---

# Error in project

Something is broken on the live Vercel URL or the build is red.

## Command

- `/debug` — paste the error, log, screenshot, or describe what is wrong
- It finds root cause, makes the smallest fix, runs green checks, pushes, and proves on Vercel
- If still wrong after deploy → `/debug` again
- Once fixed → `/verify` to confirm

---

# Full-stack project

If your project has both frontend and backend, work feature by feature — not all frontend first.

## Pattern per feature

1. `/architect` → write the frontend recipe for the feature (e.g., authentication pages)
2. `/develop` → build the frontend
3. `/debug` → only if red
4. `/verify` → prove frontend on Vercel, marks recipe done
5. `/architect` → write the backend recipe for the same feature (e.g., auth API + connect to frontend)
6. `/develop` → build the backend and connect it
7. `/debug` → only if red
8. `/verify` → prove backend on Vercel, marks recipe done, generates a manual test checklist
9. Manually test every item in the checklist on the live Vercel URL
10. Issue found → `/debug` with the issue description
11. All clear → `/ship` the feature pair
12. Repeat for the next feature

## Manual test checklist

After both frontend and backend jobs for a feature are verified, `/verify` generates a manual test checklist in `03-your-product/progress-tracker.md`. Test each item on the live Vercel URL. Report issues to `/debug`.

If the project is frontend-only, skip this pattern and follow the normal job sequence.

---

# Files already filled

If all files in `03-your-product` are real (no `[placeholders]`), the project folder exists, and GitHub/Vercel are set up:

## Commands to follow

1. Open `03-your-product/00-build-plan.md` — the first unfinished job is the only current job
2. `/architect` — write the recipe if it does not exist
3. `/develop` — implement that recipe only
4. `/debug` — only if build or deploy fails
5. `/verify` — prove on Vercel, marks recipe done
6. `/ship` — close the job, name Next Up
7. Repeat for the next unfinished job

---

# Git workflow

Follow this exact sequence every time you push code. All commands follow this automatically.

1. `git pull origin main` — sync before coding
2. `git status` — see what changed
3. `git add <specific-files>` or `git add -u` — stage explicitly, never blind `git add .`
4. `git commit -m "feat: precise imperative message"` — commit with intent
5. `git pull origin main` — safety pull before push
6. `git push origin main` — push clean history

## Rules

- Never `git push --force`
- Never leave uncommitted changes while pulling — commit or `git stash` first
- Never commit secrets, `.env` files, or debug artifacts
- Keep `.gitignore` updated before tracking any files

---

# Check pass-through

If a previous command in the same session already ran lint, typecheck, tests, and production build with all passing — and no source files changed since — the next command skips re-running those checks. Same for git status and push operations.

---

# Slash commands

| Command | Purpose |
|---------|---------|
| `/brief` | Create all product truth; no app code or repo |
| `/architect` | Write one job recipe; no app code |
| `/develop` | Implement one recipe, green gate, push, inspect Vercel |
| `/debug` | Fix production issues |
| `/verify` | Prove the job on Vercel, mark recipe done |
| `/audit` | Reconcile truth vs code vs live deployment |
| `/ship` | Final release gate |

Permanent command prompts (`debug-prompt.md`, `verify-prompt.md`, `audit-prompt.md`, `ship-prompt.md`) are used exactly. The AI must not generate replacements.

---

# Frontend result gate

A green build does not mean frontend work is done.

The Vercel production result must visibly prove:

- selected art direction, not a generic template
- product-specific signature composition
- selected motion on important interactions and state changes
- deliberate mobile, tablet, desktop, and wide compositions
- complete interaction and data states
- keyboard, focus, touch, zoom, contrast, and reduced motion
- no placeholders, fake statistics, fake terminals, card-grid filler, white route flash, or accidental layout shift

`/verify` fails frontend work that compiles but does not implement the selected prompt.

---

# Backend result gate

Backend work must prove the selected contract, not only a happy path:

- runtime input validation
- authentication and resource authorization
- ownership/tenant isolation
- bounded and deterministic lists
- typed safe errors
- transaction/idempotency behavior where required
- timeout and dependency failure behavior
- no secret or sensitive-data leak
- migration and rollback/roll-forward safety

---

# The folders

| Folder | Purpose |
|--------|---------|
| `01-start-here/` | Law and detailed workflow |
| `Idea-Prompt` | Optional interview that fills the six files |
| `02-fill-these-prompts/` | Six prompts that create product truth |
| `03-your-product/` | Current product, plan, recipes, and generated personas |
| `04-always-on-rules/frontend-prompt.md` | The **only** frontend prompt library |
| `04-always-on-rules/backend-prompt.md` | The **only** backend prompt library |
| `04-always-on-rules/recipe-format.md` | Required job-recipe shape |
| `05-slash-commands/` | Command routers and permanent command prompts |
| `{project-name}/` | Application source and its own Git repository |

Never put app source in the playbook root. Never overwrite this README with the app README.
