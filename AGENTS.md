# Law

Read `01-start-here/AGENTS.md` and follow it.

How to develop: `01-start-here/HOW-TO-BUILD.md`.

If `IMPROVE.md` has new paste text, follow **New feature later**. Do not start from idea.

Live proof is the Vercel URL. Never localhost. See `05-slash-commands/live.md`.

Frontend prompt source: `04-always-on-rules/frontend-prompt.md`.
Backend prompt source: `04-always-on-rules/backend-prompt.md`.
Do not create competing prompt catalogs.

# Project Blueprint Law

For a new project, the AI must establish a complete enough **Project Blueprint** before making downstream implementation decisions.

The Project Blueprint is the product-level understanding that connects the user's raw idea to the product-truth files in `03-your-product`.

The blueprint must establish, where applicable:

* product identity
* problem and intended outcome
* target users and actors
* responsibilities and permissions
* goals and value
* scope and non-goals
* capabilities and feature purpose
* complete end-to-end workflows
* business rules
* entity lifecycles and important state transitions
* data and information requirements
* external systems and dependencies
* security and trust boundaries
* failure, recovery, cancellation, retry, timeout, and partial-completion behavior
* scale and usage expectations when they materially affect the project
* platform and device requirements
* localization requirements
* accessibility requirements
* notifications and communication behavior
* payments and financial behavior when applicable
* content lifecycle when applicable
* administration and operational requirements
* quality requirements
* measurable or testable success criteria
* limitations and constraints
* assumptions and unknowns
* risks and mitigation
* important decisions and trade-offs
* validation and acceptance requirements
* MVP and later-phase boundaries

The AI must distinguish:

* confirmed facts
* assumptions
* unknowns
* constraints
* decisions
* risks
* recommendations
* out-of-scope work

Do not silently convert assumptions into requirements.

Do not invent product behavior to make the blueprint appear complete.

Do not select technologies, visual directions, libraries, vendors, or implementation patterns merely because they are common for similar products.

The blueprint must be driven by the actual project.

# Blueprint Gate

Before generating or confirming downstream project-truth files, verify that the blueprint is sufficiently understood.

At minimum:

* the problem is clear
* the intended outcome is clear
* meaningful users/actors are identified
* scope and non-goals are explicit
* important workflows are understood
* important business rules are identified
* important states and lifecycle transitions are understood
* required data and dependencies are identified
* important security boundaries are understood
* important failure/recovery behavior is understood
* limitations and constraints are visible
* assumptions and unknowns are visible
* significant risks are identified
* success can be observed or tested

Do not require unnecessary detail for a small project.

"Complete enough" means the project can move into downstream decisions without guessing about material product behavior.

# Blueprint → Product Truth

`02-fill-these-prompts/01-idea.md` must convert the confirmed Project Blueprint into:

`03-your-product/project-overview.md`

It must not replace the blueprint with a generic feature list.

The resulting product overview must preserve the confirmed:

* product intent
* users
* outcomes
* workflows
* business rules
* scope
* exclusions
* success criteria
* constraints
* limitations

If a material blueprint requirement cannot be represented correctly in the current project-overview structure, do not silently discard it.

Record the issue as an open question or identify the required discipline-file update before proceeding.

# Blueprint → Architecture

Architecture must be derived from the confirmed product truth.

Do not introduce a database, queue, cache, external API, authentication model, AI layer, separate service, or other infrastructure unless the confirmed product behavior requires it or the user explicitly mandates it.

Architecture decisions must have a product or technical reason.

The architecture must support the important workflows, business rules, state transitions, data ownership, security boundaries, and reliability requirements established by the blueprint.

# Blueprint → Theme

Visual decisions must come after product understanding.

Do not let a visual direction redefine product scope, workflow, permissions, business rules, or information architecture.

User-provided design direction remains a constraint unless the user explicitly changes it.

# Blueprint → Standards

Implementation standards must reflect the confirmed architecture and product behavior.

Do not create standards for technologies or capabilities that are not actually part of the confirmed project.

# Blueprint → Build Plan

Jobs must be derived from confirmed in-scope work.

Do not create jobs merely because a technology, framework, pattern, or "best practice" exists.

Important workflows and dependencies from the blueprint must be respected when ordering jobs.

A job must not silently introduce behavior that was never established in the product truth.

# Blueprint and Existing Projects

If the project already exists, do not restart discovery from zero.

First reconcile:

* existing product behavior
* existing product truth
* current architecture
* current workflows
* current states
* current data
* existing integrations
* known limitations
* requested change
* what must remain unchanged

For an existing project, the blueprint is an **evolving product model**, not necessarily a brand-new discovery exercise.

Do not redesign or replace working behavior merely to make the documents appear newer.

# Blueprint Change Control

When new information changes the project:

* update the relevant product truth
* identify affected workflows
* identify affected business rules
* identify affected states
* identify affected architecture
* identify affected jobs
* identify affected risks and constraints
* identify downstream documents that may now be stale

Do not silently propagate a material change through the entire project.

Preserve valid existing decisions.

Do not modify unrelated project truth.

# Non-Blocking vs Blocking Unknowns

When information is missing:

**Blocking unknown**

Materially affects product behavior, scope, architecture, security, data, workflow, or another important decision.

→ Record the open question and stop the affected decision.

**Non-blocking unknown**

Does not materially affect the current decision.

→ Use a clearly labeled assumption and continue.

Never invent a blocking answer.

# Absolute Principle

The project must move through this conceptual order:

`IDEA`

↓

`DISCOVERY`

↓

`PROJECT BLUEPRINT`

↓

`PRODUCT TRUTH`

↓

`ARCHITECTURE`

↓

`THEME`

↓

`STANDARDS`

↓

`BUILD PLAN`

↓

`PERSONAS`

↓

`FILES READY`

↓

`IMPLEMENTATION`

↓

`VERIFICATION`

↓

`SHIP`

Do not bypass the Project Blueprint merely because the requested feature sounds simple.

Do not confuse the Blueprint with frontend design, backend design, or code.

The Blueprint explains **what the complete project is, how it behaves, why it exists, what constrains it, and what can go wrong** before implementation-specific decisions are made.
