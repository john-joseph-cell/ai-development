# /brief

Run the six create prompts in order. Stop if the user must confirm levels.

# Do

- If `03-your-product/project-overview.md` still has `[placeholders]` → run `02-fill-these-prompts/01-idea.md`
- Then `02-fill-these-prompts/02-stack.md` (confirm backend names from `backend-prompt.md`)
- Then `02-fill-these-prompts/03-theme.md` (confirm frontend names from `frontend-prompt.md`)
- Then `02-fill-these-prompts/04-standards.md`
- Then `02-fill-these-prompts/05-jobs.md`
- Then `02-fill-these-prompts/06-personas.md` (copy exact selected sections into both generated persona files)
- For full-stack projects: ensure jobs are ordered feature by feature — frontend job then its backend pair — not all frontend first
- Update `03-your-product/progress-tracker.md` to Files are ready
- Tell the user the next step is **Files are ready**: create `{project-name}/`, then a GitHub repo for that folder only

# Stop

- Do not create a GitHub repo
- Do not create the project folder yet
- Do not write app code
- Do not skip stack or theme confirmation
- Do not summarize selected prompt sections
- Do not overwrite the discipline `README.md`
