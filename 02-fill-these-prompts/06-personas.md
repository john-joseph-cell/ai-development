# Prompt: personas

Run only after overview, architecture, UI context, and standards are real.

# You replace

- `03-your-product/frontend-prompt.md`
- `03-your-product/backend-prompt.md`

# You read

- every real file in `03-your-product`
- `04-always-on-rules/frontend-prompt.md`
- `04-always-on-rules/backend-prompt.md`

# Selection

Read exact confirmed frontend names from `ui-context.md` and backend names from `architecture.md`.

If a name is missing or invalid, ask only for the missing name using the options in the authoritative prompt library. Give one recommendation and one short reason. Stop and wait.

Do not ask the user to confirm the same complete selection twice.

# You write frontend

Follow `Selection law` in `04-always-on-rules/frontend-prompt.md`.

- Copy Universal foundation verbatim
- Copy exactly one confirmed Visual section verbatim
- Copy exactly one confirmed Motion section verbatim
- Copy exactly one confirmed Product UX section verbatim
- Copy Production AA engineering verbatim unless explicitly waived
- Add Project contract using only real project facts

Do not summarize, rewrite, merge, “improve,” or omit the selected prompt text.

# You write backend

Follow `Selection law` in `04-always-on-rules/backend-prompt.md`.

- Copy Universal backend foundation verbatim
- Copy the exact confirmed Shape, API, Data, Auth, Runtime, Reliability, and AI sections verbatim
- Include Webhooks or Queues only when confirmed
- Add Project backend contract using only real project facts

Do not summarize, rewrite, merge, “improve,” or omit the selected prompt text.

# Output rules

- Generated files contain only the selected prompts plus project contract, not the option catalog
- No `[placeholders]`
- No generic “10+ years” persona paragraph replacing the real rules
- No invented routes, roles, data, content, assets, providers, or features
- If the product has no backend, generate the exact minimal selected backend prompt (normally Content + Data None + Auth None + AI None); do not invent backend work
