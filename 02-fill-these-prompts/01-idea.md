# Prompt: idea

Use this after the **Project Blueprint / Discovery** stage.

This prompt converts the confirmed Project Blueprint into:

`03-your-product/project-overview.md`

# You replace

`03-your-product/project-overview.md`

# You need

The complete confirmed Project Blueprint from the discovery conversation, including all relevant information already established by the user.

Use information already present in the conversation.

Do not ask the user to repeat information that is already known.

If the Blueprint is not sufficiently established, do not generate `project-overview.md`. Return to the Blueprint / Discovery flow first.

# Blueprint dependency

The Project Blueprint is the source of truth for this stage.

The Blueprint should already establish, where applicable:

* product identity
* problem
* target users and actors
* responsibilities and permissions
* goals and outcomes
* value
* scope
* non-goals
* capabilities and feature purpose
* core and end-to-end workflows
* business rules
* important entity lifecycles
* state transitions
* data and information requirements
* external services and dependencies
* security and trust boundaries
* failure behavior
* recovery behavior
* cancellation behavior
* retry behavior
* timeout behavior
* partial-completion behavior
* concurrency considerations
* scale expectations when material
* platform and device requirements
* localization
* accessibility
* notifications and communication
* payments and financial behavior when applicable
* content lifecycle when applicable
* administration and operations
* quality requirements
* success criteria
* limitations
* constraints
* assumptions
* unknowns
* risks
* decisions and trade-offs
* validation requirements
* MVP boundaries
* future-phase boundaries

Do not force irrelevant categories into the document.

# Blueprint truth rules

Treat these categories differently:

* Confirmed facts → preserve as established truth
* Explicit user requirements → preserve exactly in meaning
* Assumptions → do not present them as confirmed facts
* Unknowns → do not invent answers
* Constraints → preserve as constraints
* Decisions → preserve confirmed decisions
* Risks → preserve important risks where they affect product scope or behavior
* Recommendations → do not silently convert them into requirements
* Out of Scope → preserve explicitly

If a material requirement is still unknown, do not invent it.

If a missing detail is non-blocking, use the smallest reasonable interpretation consistent with the Blueprint.

If a missing detail would materially change product behavior, stop and record the open question in:

`03-your-product/progress-tracker.md`

# Blueprint-to-overview translation

Convert the Blueprint into a product overview without losing the project's behavioral meaning.

Preserve:

* the actual problem
* the actual intended outcome
* actual users
* actual capabilities
* actual core workflows
* actual product rules
* actual scope
* actual exclusions
* actual success criteria

Do not reduce the project to a generic feature list.

Do not turn implementation decisions into product requirements.

Do not choose:

* framework
* database
* API style
* hosting architecture
* visual theme
* frontend persona
* backend persona
* engineering jobs

Those belong to later stages.

# Workflow preservation

Important workflows discovered during Blueprint must remain represented in `## Core User Flow` and/or `## Features`.

Do not document only the happy path when the Blueprint established meaningful:

* validation
* permissions
* failure
* cancellation
* recovery
* retry
* expiration
* state transitions
* user/system decisions

Use concise product-level wording rather than implementation detail.

# Feature discipline

Features are derived from confirmed product capabilities.

For every feature, preserve its purpose.

Do not add features merely because:

* similar products have them
* a framework commonly supports them
* an AI assistant recommends them
* they make the document look more complete
* they will supposedly be useful later

Separate the product's current scope from future ideas.

# Scope discipline

`In Scope` must contain confirmed work that belongs to the current product.

`Out of Scope` must contain meaningful exclusions established by the Blueprint.

Do not use Out of Scope as a dumping ground for random features that were never considered.

Do not move uncertain features into In Scope merely to avoid ambiguity.

# Success criteria discipline

Success criteria must come from the actual intended product outcomes.

Each criterion should be:

* visible
* observable
* measurable
* or testable

Do not fabricate numerical KPIs.

Do not claim business success merely because a page renders.

# Contradiction check

Before writing the file, verify that:

* users do not contradict roles
* features do not contradict scope
* workflows do not contradict permissions
* success criteria match the stated goals
* exclusions do not conflict with In Scope
* product behavior does not depend on an unconfirmed implementation choice

If a contradiction materially affects the product, stop and record the open question instead of silently choosing a side.

# You write

Plain markdown.

No extra commentary.

Headings must match `03-your-product/project-overview.md` exactly.

# Headings you must output

* `# [Project Name]`
* `## Overview`
* `## Goals`
* `## Core User Flow`
* `## Features`
* `## Scope` with `### In Scope` and `### Out of Scope`
* `## Success Criteria`

# Rules

* Be specific.
* No `[placeholders]` in the output.
* Features are the menu, not the build.
* Out of Scope must be real. Name things you will not build.
* Success criteria must be visible or testable.
* Do not pick stack, theme, or job numbers here.
* Do not create a GitHub repo.
* Do not create a project folder.
* Do not invent statistics.
* Do not invent integrations.
* Do not invent user roles.
* Do not introduce features merely because they are common in similar products.
* Preserve the actual product intent established during the Project Blueprint.
* Preserve important workflows rather than reducing them to screen names.
* Preserve meaningful business rules at the product level.
* Preserve important lifecycle/state behavior where it affects user-visible behavior.
* Do not introduce implementation-specific architecture.
* Do not turn assumptions into requirements.
* Do not turn recommendations into confirmed scope.
* Do not silently resolve material contradictions.
* Do not silently discard important Blueprint constraints or limitations.
* Do not add future-phase functionality to current In Scope.
* Keep the document product-level and implementation-neutral.
* Do not generate the next planning file automatically.

# Final validation

Before outputting `project-overview.md`, verify internally:

* the project identity is clear
* the problem is clear
* the intended outcomes are clear
* meaningful users and actors are represented
* the core user flow reflects the Blueprint
* important capabilities have a reason to exist
* important product-level rules are preserved
* scope boundaries are explicit
* important exclusions are explicit
* limitations and constraints that affect product behavior are preserved
* success can be observed or tested
* no invented requirement has been introduced
* no implementation decision has leaked into the document
* no material Blueprint contradiction remains unresolved

Then generate only `project-overview.md`.

Stop.
