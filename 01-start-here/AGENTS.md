# Law

Read `01-start-here/HOW-TO-BUILD.md` if the user asks how to develop.

Before any code or architecture change, read in order:

- `03-your-product/project-overview.md`
- `03-your-product/architecture.md`
- `03-your-product/ui-context.md`
- `03-your-product/code-standards.md`
- `03-your-product/progress-tracker.md`
- `03-your-product/00-build-plan.md`

Then read the matching persona:

- Frontend work → `03-your-product/frontend-prompt.md`
- Backend work → `03-your-product/backend-prompt.md`
- Both → read both

# Hard rules

- One job at a time. The job is the first unfinished name in `03-your-product/00-build-plan.md`
- Do not invent product behavior. Missing fact → open question in `03-your-product/progress-tracker.md` and stop
- Do not push a red build. Lint, types, relevant tests, and the production build must be green
- Do not commit secrets. Env lives on Vercel
- Live proof is the Vercel production URL. Never localhost. Follow `05-slash-commands/live.md`. If GitHub repo URL or Vercel URL is missing, ask the user and write it into `03-your-product/architecture.md` Host
- `/debug`, `/verify`, `/audit`, and `/ship` always use their permanent `*-prompt.md`. Do not generate replacements
- Commands push only authorized green project changes, never red or empty commits; live proof then comes from Vercel
- All frontend prompt law lives in `04-always-on-rules/frontend-prompt.md`; generated frontend work follows `03-your-product/frontend-prompt.md`
- All backend prompt law lives in `04-always-on-rules/backend-prompt.md`; generated backend work follows `03-your-product/backend-prompt.md`
- Do not replace this file or the root `AGENTS.md` with a stack dump
- App source lives only in the project folder named in `03-your-product/architecture.md` (Host → Project folder). Never write the app into the discipline root. Never overwrite the discipline `README.md`
- If `IMPROVE.md` or `{project-name}/IMPROVE.md` has new paste text, follow **New feature later** in `01-start-here/HOW-TO-BUILD.md`. Do not start from idea again
- `/brief` and the idea prompt never create a GitHub repo. `/ship` never creates a GitHub repo. The repo is created only after `03-your-product` is real, for the project folder only
- Git workflow: pull → status → stage explicitly → commit with intent → safety pull → push. Never `git push --force`. Never leave uncommitted changes while pulling. Never commit secrets. See `01-start-here/HOW-TO-BUILD.md` → Git workflow
- Check pass-through: if the previous command in this session already ran lint, typecheck, tests, and production build with all passing, and no source files changed since, the next command skips re-running those checks. Same for git status and push
- `/verify` marks the recipe status as Done in `03-your-product/00-build-plan.md` and fills deployed commit and verified URL when it returns PASS
- Full-stack feature pairing: if the project has both frontend and backend, work one feature at a time. Frontend job first (all commands through `/verify`), then backend job for the same feature (all commands through `/verify`), then a manual test checklist is generated in `progress-tracker.md`. User tests on the Vercel URL. Issue → `/debug`. All clear → `/ship`. Frontend-only projects skip this rule

# Commands

When the user types a slash command, read that file and do only what it says.

- `/brief` → `05-slash-commands/brief.md`
- `/architect` → `05-slash-commands/architect.md`
- `/develop` → `05-slash-commands/develop.md`
- `/verify` → `05-slash-commands/verify.md`
- `/debug` → `05-slash-commands/debug.md`
- `/audit` → `05-slash-commands/audit.md`
- `/ship` → `05-slash-commands/ship.md`
- Live URL and push rules → `05-slash-commands/live.md`

The command routers call these permanent prompts:

- `/debug` → `debug-prompt.md`
- `/verify` → `verify-prompt.md`
- `/audit` → `audit-prompt.md`
- `/ship` → `ship-prompt.md`

# After each job

- Update `03-your-product/progress-tracker.md`
- If stack, UI, or scope changed, update that file in `03-your-product` before the next job
- For full-stack features: after both frontend and backend jobs are verified, ensure the manual test checklist in `progress-tracker.md` is complete before `/ship`
