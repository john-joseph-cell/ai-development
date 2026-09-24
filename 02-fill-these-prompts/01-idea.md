# Prompt: idea

Use this when the product is not written yet.

# You replace

`03-your-product/project-overview.md`

# You need

The user's idea in chat. Ask only what you cannot infer.

# You write

Plain markdown. No extra commentary. Headings must match `03-your-product/project-overview.md` exactly.

# Headings you must output

- `# [Project Name]`
- `## Overview`
- `## Goals`
- `## Core User Flow`
- `## Features`
- `## Scope` with `### In Scope` and `### Out of Scope`
- `## Success Criteria`

# Rules

- Be specific. No `[placeholders]` in the output
- Features are the menu, not the build
- Out of Scope must be real. Name things you will not build
- Success criteria must be visible or testable
- Do not pick stack, theme, or job numbers here
- Do not create a GitHub repo
- Do not create a project folder
