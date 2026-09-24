# /architect

Write one recipe. No app code.

# Need

- The job name from the user, or the first unfinished name in `03-your-product/00-build-plan.md`
- `03-your-product/project-overview.md`, `03-your-product/architecture.md`, `03-your-product/ui-context.md`
- Matching generated `frontend-prompt.md` and/or `backend-prompt.md`
- `04-always-on-rules/recipe-format.md`

# Do

- Write `03-your-product/[nn]-[name].md` using only the headings in `04-always-on-rules/recipe-format.md`
- Set the Layer field: `frontend`, `backend`, or `full-stack`
- For full-stack projects: if this is a backend job for a feature that already has a frontend job, set Pair to the frontend job name. If this is the frontend job, note that the backend pair comes next
- Stay inside that job
- Name blast radius and rollback
- Include Verify checkboxes the user can see on the Vercel URL. Never localhost
- For frontend jobs, make selected visual direction, signature, motion, states, breakpoints, and accessibility testable
- For backend jobs, make contracts, validation, authorization, failure behavior, and reliability testable
- If product behavior is missing, add an open question in `03-your-product/progress-tracker.md` and stop

# Stop

- Do not invent features
- Do not write application source
- Do not start `/develop`
- Do not create a GitHub repo
