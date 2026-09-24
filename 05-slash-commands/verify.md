# /verify

Run the permanent independent verification prompt.

# Read

- `05-slash-commands/verify-prompt.md`
- `05-slash-commands/live.md`
- current recipe and generated persona(s)

# Do

- Follow `verify-prompt.md` exactly
- If the previous command in this session already ran lint, typecheck, tests, and production build with all passing, and no source files changed since, skip re-running those checks
- Produce its evidence matrix
- Return PASS only when every required item has production evidence
- On PASS: mark the recipe Status as Done in `03-your-product/00-build-plan.md`, fill Deployed commit and Verified URL
- On PASS for a full-stack backend job (has a frontend pair): generate a manual test checklist in `03-your-product/progress-tracker.md` under Manual Test Checklist. The user tests each item on the Vercel URL. Issues go to `/debug`

# Never

- Generate a replacement verify prompt
- Fix defects during verification
- Treat localhost, preview, build output, or screenshots alone as production proof
- Mark failed or unproven work complete
