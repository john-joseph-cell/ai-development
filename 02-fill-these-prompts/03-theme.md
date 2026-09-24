# Prompt: theme

Use this after `project-overview.md` and `architecture.md` are real.

# You replace

`03-your-product/ui-context.md`

# You read

- `03-your-product/project-overview.md`
- `03-your-product/architecture.md`
- `04-always-on-rules/frontend-prompt.md` — the only frontend prompt source

# You ask (names only, then stop)

Recommend from the Recommendation law in `frontend-prompt.md`. Ask only:

- Visual: Google | Awwwards | Apple | Dribbble | E-commerce | SaaS | Linear | Vercel | Stripe | Shopify | Master
- Motion: Apple | Stripe | Awwwards | Linear
- Product UX: Raycast | Tabular | E-commerce CRO | SaaS dashboard | Shopify store
- Engineering: Production AA

Mark one recommendation per group and give one short reason. Do not paste or summarize the prompt sections. Wait for confirmation.

# You write

Plain markdown. No extra commentary. Use exactly these headings:

- `# UI Context`
- `## Selected prompts` — exact confirmed names
- `## Theme` — project-specific application of the selected visual prompt
- `## Signature` — visual thesis and one memorable element
- `## Colors` — semantic CSS variables and values
- `## Typography` — display, body, label, metadata, numeric roles
- `## Spacing and radius`
- `## Surfaces and borders`
- `## Layout and breakpoints`
- `## Components and icons`
- `## Motion` — timings, curves/springs, route behavior, reduced motion
- `## Data, tables, and pagination`
- `## States`
- `## Accessibility and performance`
- `## Anti-patterns`

# Rules

- Derive every decision from the exact selected sections in `frontend-prompt.md`
- Use semantic tokens; components do not invent local visual values
- Match the confirmed stack in `architecture.md`
- Production AA remains selected unless the user waives it in writing
- Do not invent content, features, fake statistics, placeholder media, or decorative widgets
- Never output the failed generic portfolio pattern described in Universal foundation
