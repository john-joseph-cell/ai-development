# How to develop

# Folders (open in this order)

- `01-start-here` — you are here
- `02-fill-these-prompts` — write the product
- `03-your-product` — files you replace
- `04-always-on-rules` — one frontend prompt library, one backend prompt library, recipe format
- `05-slash-commands` — slash commands (live proof is Vercel, never localhost)
- `{project-name}/` — the app, created after files are ready
- `IMPROVE.md` — paste later upgrades. Follow **New feature later**

# Where are you?

Pick one heading below. Ignore the rest.

- No idea yet → **Start from nothing**
- Files in `03-your-product` are filled → **Files are ready**
- GitHub and Vercel already exist, you are building → **Next job**
- Lint, types, or `npm run build` is red → **Build error**
- Vercel deploy failed → **Vercel failed**
- URL is live but the page is wrong → **Live page is wrong**
- You want a new feature, or `IMPROVE.md` has new text → **New feature later**
- Bug or tidy, no new feature → **Fix or clean**

# Ready gate

Do not create a repo. Do not create a project folder. Do not run `/develop`. Not until all of this is true.

`/brief` and `02-fill-these-prompts/01-idea.md` never create a GitHub repo. `/ship` never creates a GitHub repo. The repo is created only under **Files are ready**.

- `03-your-product/project-overview.md` is real. No `[placeholders]`
- `03-your-product/architecture.md` is real. Backend selections are written
- `03-your-product/ui-context.md` is real. Frontend selections are written
- `03-your-product/code-standards.md` is real
- `03-your-product/00-build-plan.md` has real jobs (`01-…`, `02-…`)
- `03-your-product/frontend-prompt.md` is real
- `03-your-product/backend-prompt.md` is real
- Generated frontend prompt contains exact selected sections from `04-always-on-rules/frontend-prompt.md`
- Generated backend prompt contains exact selected sections from `04-always-on-rules/backend-prompt.md`

# Start from nothing

- Run `02-fill-these-prompts/01-idea.md` → replace `03-your-product/project-overview.md`
- Run `02-fill-these-prompts/02-stack.md` → choose backend prompt names → replace `03-your-product/architecture.md`
- Run `02-fill-these-prompts/03-theme.md` → choose frontend prompt names → replace `03-your-product/ui-context.md`
- Run `02-fill-these-prompts/04-standards.md` → replace `03-your-product/code-standards.md`
- Run `02-fill-these-prompts/05-jobs.md` → replace `03-your-product/00-build-plan.md`
- Run `02-fill-these-prompts/06-personas.md` → copy exact selected sections into both generated persona files
- Or run `/brief` (`05-slash-commands/brief.md`) to do those six in order
- Then go to **Files are ready**

# Files are ready

This is when the app folder and GitHub repo are created. Not during idea. Not during `/ship`.

- Ask the AI for a kebab-case folder name from `03-your-product/project-overview.md` (example `raja-portfolio`)
- Create `{project-name}/` in the discipline root. App source, the app `README.md`, and `IMPROVE.md` live only there
- Never overwrite the discipline `README.md`
- Write the folder name into `03-your-product/architecture.md` under Host → Project folder
- You create a **new** GitHub repo for **that folder only**. Do not `git init` the discipline clone
- Import **that** repo into Vercel. Secrets in Vercel env. Write GitHub repo URL and Vercel Project URL into `03-your-product/architecture.md` Host
- Then go to **Next job**

# Next job

- Open `03-your-product/00-build-plan.md`
- Copy the first unfinished name. That is the only job
- No recipe file (example: `03-your-product/01-site-shell.md` missing) → `/architect` that name (`05-slash-commands/architect.md`)
- `/develop` that name only (`05-slash-commands/develop.md`). Code only in the project folder
- Check in the project folder: lint, types, tests, production build
- Red → go to **Build error**
- Green → one commit in the project folder → push that repo → wait for Vercel
- Vercel fails → go to **Vercel failed**
- Missing GitHub or Vercel URL → ask, write into Host, then continue
- `/verify` on the Vercel production URL. Never localhost
- FAIL → `/debug`, deploy, `/verify` again
- PASS → `/ship`; only `/ship` marks the job done
- Repeat this heading until every row in `03-your-product/00-build-plan.md` is done

# Build error

- `/debug` (runs the permanent prompt through `05-slash-commands/debug.md`)
- Do not push while red
- Do not start the next job
- When the full green gate passes → commit in the project folder → push → `/verify` on the Vercel URL

# Vercel failed

- Open the Vercel log
- `/debug` and paste that log
- Push only when `npm run build` is green
- Open the Vercel URL again

# Live page is wrong

- `/debug` what you see on the Vercel URL vs the recipe in `03-your-product` (`01-….md` for this job)
- Check: lint, types, tests, production build
- Green → push the project folder repo
- Open the Vercel URL again, then `/verify`. Never localhost

# New feature later

If the project already exists, paste the request into `IMPROVE.md` or `{project-name}/IMPROVE.md`. Then:

- Add the feature to In Scope in `03-your-product/project-overview.md`
- Change `03-your-product/architecture.md` only if stack, data, auth, or host change
- Change `03-your-product/ui-context.md` only if visual rules change
- Run `02-fill-these-prompts/05-jobs.md` or add the next number by hand in `03-your-product/00-build-plan.md`
- Write app code only in the project folder. Do not create a new GitHub repo
- Go to **Next job**

# Git workflow

Follow this exact sequence every time you push code. All commands follow this automatically.

1. `git pull origin main` — sync before coding
2. `git status` — see what changed
3. `git add <specific-files>` or `git add -u` — stage explicitly, never blind `git add .`
4. `git commit -m "feat: precise imperative message"` — commit with intent
5. `git pull origin main` — safety pull before push
6. `git push origin main` — push clean history

- Never `git push --force`
- Never leave uncommitted changes while pulling. Commit or `git stash` first
- Never commit secrets, `.env` files, or debug artifacts

# Full-stack project

If the project has both frontend and backend, work feature by feature.

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

- Bug → `/debug`
- Small change → `/develop` and name the files it may touch (`05-slash-commands/develop.md`)
- Check in the project folder: lint, types, tests, production build
- Green → push that repo
- `/verify` on the Vercel URL. Never localhost
- Do not add a new row to `03-your-product/00-build-plan.md`
