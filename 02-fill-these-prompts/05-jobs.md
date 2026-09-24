# Prompt: jobs

Use this after `03-your-product/project-overview.md` and `03-your-product/architecture.md` are real.

# You replace

`03-your-product/00-build-plan.md`

# You read

- `03-your-product/project-overview.md`
- `03-your-product/architecture.md`
- `03-your-product/ui-context.md`
- `03-your-product/code-standards.md`
- `04-always-on-rules/recipe-format.md`

# You write

Plain markdown. No extra commentary. Headings must match `03-your-product/00-build-plan.md` exactly.

# Headings you must output

- `# Build Plan`
- `## Jobs`

Then one block per job:

- `### 01-short-name`
- Layer: `frontend` | `backend` | `full-stack`
- Pair: [paired job name, if full-stack feature pair]
- Goal
- Recipe file (`03-your-product/01-short-name.md`)
- Dependencies
- Status: Pending
- Deployed commit: [ ]
- Verified URL: [ ]

# Rules

- Numbers are `01`, `02`, `03`. The name is the file name
- One visible result per job
- Do not mix UI, database, and background work in one job
- Make frontend quality and backend contract work explicit jobs or explicit recipe acceptance; do not hide them under "polish"
- If a job creates a frontend surface, its goal must name the selected visual/motion result—not only "build page"
- If a job creates backend behavior, its goal must name the contract/invariant—not only "add API"
- Job `01` is scaffold or site shell **inside the project folder** if no app exists yet. Not the whole product. Not in the discipline root
- Auth before the pages it protects
- Data model before the screens that need it
- Infra (env, Vercel notes) belongs in an early job if the app is new
- Only In Scope features from `03-your-product/project-overview.md`
- No `[Next Feature]` rows
- No `[placeholders]`
- Full-stack projects: order jobs feature by feature. Frontend job first, then its backend pair for the same feature. Not all frontend first. Example: `03-auth-pages` (frontend) → `04-auth-api` (backend, Pair: `03-auth-pages`)
- Every job must include a Layer field: `frontend`, `backend`, or `full-stack`
- Backend jobs that pair with a frontend job must include a Pair field naming the frontend job
