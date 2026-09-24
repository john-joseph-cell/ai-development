# Recipe format

Every job file in `03-your-product` (`01-….md`, `02-….md`) must use these headings only.

# Unit 01: [short name]

# Layer

- `frontend` | `backend` | `full-stack`
- Pair: [paired job name, if this backend job pairs with a frontend job]

# Goal

- One or two sentences. What exists when this job is done

# Design

- Visual or API choices for this job only
- Follow `03-your-product/ui-context.md` and `03-your-product/architecture.md`
- Blast radius: what must not break
- Rollback: how to undo

# Implementation

- Ordered steps
- Packages installed only in the job that first needs them

# Dependencies

- Jobs or services that must exist first

# Verify when done

- Checkboxes a human can see on the Vercel URL. Never localhost
- Required lint, type, test, and build commands pass
- Selected frontend-prompt acceptance items that apply to this job
- Selected backend-prompt acceptance items that apply to this job
