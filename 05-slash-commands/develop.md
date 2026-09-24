# /develop

Build one job only.

Follow `05-slash-commands/live.md` when the job is green. Never localhost as proof.

# Need

- Job name from the user, or the first unfinished name in `03-your-product/00-build-plan.md`
- That job's recipe (`03-your-product/01-….md`)
- `01-start-here/AGENTS.md` read order and the matching persona
- Ready gate in `01-start-here/HOW-TO-BUILD.md` must already be true
- A GitHub repo and Vercel project should already exist **for the project folder** named in `03-your-product/architecture.md`
- GitHub repo URL and Vercel Project URL in Host. If missing, ask the user, write them in, then continue
- If that folder does not exist, stop and tell the user to finish **Files are ready** in `01-start-here/HOW-TO-BUILD.md`

# Do

- If the recipe is missing, stop and tell the user to run `/architect`
- Write application files only inside the project folder. Never write `package.json`, `app/`, or an app `README.md` into the discipline root
- Never overwrite the discipline `README.md`
- Implement only that recipe
- Follow `03-your-product/ui-context.md` and every selected section in `03-your-product/frontend-prompt.md` on UI
- Follow `03-your-product/architecture.md` and every selected section in `03-your-product/backend-prompt.md` on server work
- For frontend work, implement the visual thesis, signature, selected motion, responsive recomposition, complete states, and Definition of visually done—not merely valid components
- Before frontend code, map the recipe to composition, typography, surfaces, signature interaction, motion, states, and breakpoints; if the recipe cannot test those results, stop and run `/architect`
- Never substitute placeholder circles, fake terminal/data, generic hero-card grids, or repeated fade-up motion for missing art direction
- For full-stack projects: check the recipe Layer field. If this is a frontend job, the paired backend job comes next. If this is a backend job, connect it to the frontend pair
- Update `03-your-product/progress-tracker.md`
- Run lint, types, relevant tests, and the production build **inside the project folder** using commands in `03-your-product/architecture.md`
- Green → follow the push workflow in `05-slash-commands/live.md`

# Stop

- Red build → `/debug`. Do not push
- Do not start the next job
- Do not invent product behavior
- Do not use localhost as proof
