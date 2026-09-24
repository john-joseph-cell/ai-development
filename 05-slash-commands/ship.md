# /ship

Run the permanent release gate prompt.

# Read

- `05-slash-commands/ship-prompt.md`
- `05-slash-commands/live.md`
- current recipe, verification evidence, and generated persona(s)

# Do

- Follow `ship-prompt.md` exactly
- If `/verify` already returned PASS for this job in this session, skip re-running checks and re-verifying. Use the existing evidence
- Mark done only after its complete release gate passes
- For full-stack features: confirm the manual test checklist in `progress-tracker.md` is complete and all items pass before shipping the feature pair
- Report deployed commit, live URL, proof, and Next Up

# Never

- Generate a replacement ship prompt
- Ship red, unverified, mixed-scope, or secret-bearing work
- Mark a job done before production PASS
- Create a repository or start the next job
