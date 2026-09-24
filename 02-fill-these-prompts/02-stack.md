# Prompt: stack

Use this after `03-your-product/project-overview.md` is real.

# You replace

`03-your-product/architecture.md`

# You read

- `03-your-product/project-overview.md`
- `04-always-on-rules/backend-prompt.md` — the only backend prompt source

# You ask (names only, then stop)

Recommend the smallest valid set using the Recommendation law in `backend-prompt.md`. Ask only for names:

- Shape
- API (plus Webhooks only when required)
- Data
- Auth
- Runtime (plus Queues only when required)
- Reliability
- AI

Mark one recommendation per group and give one short reason. Do not paste or summarize the prompt sections. Wait for confirmation.

# You write

Plain markdown. No extra commentary. Use exactly these headings:

- `# Architecture`
- `## Backend levels` — exact confirmed names
- `## Stack` — layer, technology, role
- `## Host` — Vercel, project folder, GitHub repo URL if known, Vercel production URL if known, commands, environment variable names only
- `## System Boundaries`
- `## Storage Model`
- `## Auth and Access Model`
- `## API law` — Universal backend foundation applied to this product
- `## Invariants` — at least four testable rules

# Rules

- Use selections and rules only from `04-always-on-rules/backend-prompt.md`
- Keep the architecture as small as the product permits
- Vercel is the default host, not a database
- Edge is selected only for compatible work; do not claim it is universally faster
- Propose a kebab-case project folder; do not create it or a GitHub repo
- No UI tokens and no `[placeholders]`
