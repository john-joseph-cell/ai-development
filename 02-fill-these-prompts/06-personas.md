# Prompt: personas

Run only after overview, architecture, UI context, and standards are real.

# You replace

- `03-your-product/frontend-prompt.md`
- `03-your-product/backend-prompt.md`

# You read

- give every file info present in `03-your-product` to AI model, then generate frontend prompt.
- then give same info to AI model and generate backend prompt.

# Selection

Read exact confirmed frontend names from `ui-context.md` and backend names from `architecture.md`.

If a name is missing or invalid, ask only for the missing name using the options in the authoritative prompt library. Give one recommendation and one short reason. Stop and wait.

Do not ask the user to confirm the same complete selection twice.
