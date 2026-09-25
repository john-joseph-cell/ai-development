# Prompt: standards

Use this after the **Project Blueprint / Discovery** stage and after:

* `03-your-product/project-overview.md`
* `03-your-product/architecture.md`
* `03-your-product/ui-context.md`

are real.

# You replace

`03-your-product/code-standards.md`

# You read

* the confirmed Project Blueprint from the discovery conversation
* `03-your-product/project-overview.md`
* `03-your-product/architecture.md`
* `03-your-product/ui-context.md`
* `04-always-on-rules/frontend-prompt.md`
* `04-always-on-rules/backend-prompt.md`

# Blueprint dependency

Code standards are downstream rules.

They must be derived from the confirmed:

* product behavior
* workflows
* business rules
* states
* data requirements
* security requirements
* architecture
* UI system
* constraints
* limitations
* quality requirements

Do not create standards independently of the project.

Do not introduce rules for technologies or capabilities that the project does not use.

Do not convert theoretical best practices into mandatory project rules without a project reason.

# Standards principle

The purpose of this file is to define **how this specific project's code must be written and organized**.

Prioritize:

* correctness
* consistency
* security
* maintainability
* testability
* readability
* predictable behavior
* architectural integrity
* product correctness
* operability

Do not optimize for abstraction, cleverness, or complexity.

# Requirement traceability

Every important implementation rule must be traceable to one or more of:

* Project Blueprint
* `project-overview.md`
* `architecture.md`
* `ui-context.md`
* authoritative frontend prompt
* authoritative backend prompt

Do not create standards that contradict any confirmed project truth.

# Workflow preservation

Code standards must support the workflows established by the Blueprint.

For important workflows, ensure implementation rules preserve:

* validation
* permissions
* business rules
* state transitions
* failure behavior
* recovery behavior
* cancellation
* retry behavior
* timeout behavior
* idempotency where required
* concurrency behavior where required
* data integrity

Do not allow business-critical behavior to exist only as undocumented convention.

# State integrity

Where the project has stateful entities or workflows:

* implement valid state transitions explicitly
* reject invalid transitions
* preserve lifecycle rules
* keep terminal states terminal unless restoration is explicitly supported
* do not infer state from unrelated UI conditions
* keep state ownership at the correct architectural boundary

Do not allow frontend visual state to become the source of truth for business state.

# Security standards

Standards must preserve the security model established in:

`architecture.md`

and the Blueprint.

At minimum where applicable:

* validate untrusted input at runtime
* authorize actions server-side
* enforce ownership/tenant boundaries
* keep secrets server-side
* protect sensitive data
* prevent unsafe direct object access
* use safe error handling
* preserve audit requirements
* follow confirmed authentication/session rules
* follow confirmed file/upload rules

Do not rely on UI hiding as authorization.

# Data standards

Data-related code must preserve the confirmed:

* entities
* ownership
* relationships
* lifecycle
* consistency requirements
* constraints
* retention rules
* migration rules
* audit behavior

Do not introduce an alternative persistence pattern that conflicts with `architecture.md`.

# API standards

API behavior must preserve:

* validated inputs
* stable contracts
* authorization
* predictable success results
* predictable failures
* bounded lists
* deterministic ordering
* pagination rules
* timeout behavior
* retry/idempotency requirements
* external dependency boundaries

Do not expose internal database structures merely because they are convenient.

# UI implementation standards

Frontend code must preserve the confirmed:

* visual system
* interaction states
* responsive behavior
* accessibility requirements
* motion rules
* information hierarchy
* product workflows

Do not introduce visual behavior that changes product meaning.

Do not invent product functionality to make a screen look complete.

# Testing standards

Testing must follow the actual project risk model.

For important behavior, require tests for applicable:

* happy path
* validation failure
* authorization failure
* invalid state transition
* dependency failure
* duplicate/retry behavior
* empty state
* no-results state
* recovery behavior
* critical data integrity

Do not write tests merely to increase test count.

Test the behavior that matters.

# You write

Plain markdown.

Imperative rules.

No extra commentary.

Headings must match `03-your-product/code-standards.md` exactly.

# Headings you must output

* `# Code Standards`
* `## General`
* `## Language`
* `## Framework`
* `## Styling`
* `## API`
* `## Data`
* `## File Organization`

# Rules

* Only technologies named in `03-your-product/architecture.md`.
* Styling follows tokens in `03-your-product/ui-context.md`.
* Frontend standards preserve Universal foundation and Production AA.
* Backend standards preserve Universal backend foundation.
* No `[placeholders]`.
* Each section has at least four imperative rules.
* Do not introduce technologies not present in `architecture.md`.
* Do not introduce libraries merely because they are popular.
* Do not contradict the Project Blueprint.
* Do not contradict `project-overview.md`.
* Do not contradict `architecture.md`.
* Do not contradict `ui-context.md`.
* Do not invent product behavior.
* Do not invent workflows.
* Do not invent business rules.
* Do not invent entities.
* Do not invent integrations.
* Do not invent security requirements unrelated to the project.
* Do not invent compliance obligations.
* Do not turn future-phase functionality into current implementation rules.
* Keep frontend presentation, application state, data access, and business logic appropriately separated.
* Preserve confirmed ownership and authorization boundaries.
* Preserve confirmed lifecycle and state-transition rules.
* Preserve confirmed reliability and failure behavior.
* Keep implementation rules enforceable through code review, tests, linting, type checking, or tooling where practical.
* Prefer the simplest rule that correctly enforces the intended behavior.
* Do not create abstractions solely for theoretical reuse.
* Do not duplicate shared behavior unnecessarily.
* Do not hide significant business behavior inside undocumented conventions.

# General

Include rules for:

* correctness
* naming
* readability
* error handling
* configuration
* logging
* comments/documentation
* dependency discipline

Each rule must be actionable.

# Language

Use only the language(s) confirmed by the architecture.

Define rules for:

* strict typing
* null/undefined handling
* asynchronous behavior
* error handling
* data validation
* unsafe escape hatches

Do not create language rules for languages that are not part of the project.

# Framework

Use only the framework confirmed in `architecture.md`.

Define rules for:

* framework-native patterns
* server/client boundaries where applicable
* routing
* lifecycle
* rendering
* state boundaries
* framework configuration
* framework-specific security requirements

Do not replace the selected framework with another pattern.

# Styling

Use the design system defined by:

`03-your-product/ui-context.md`

Define rules for:

* semantic tokens
* typography
* spacing
* surfaces
* responsive behavior
* states
* motion
* accessibility

Do not allow feature components to invent local visual systems.

# API

Follow the confirmed backend contract and:

`03-your-product/architecture.md`

Define rules for:

* validation
* authorization
* request/response contracts
* errors
* pagination
* filtering
* sorting
* rate limits where applicable
* idempotency where applicable
* external dependency handling

# Data

Follow the confirmed data architecture.

Define rules for:

* entity access
* ownership
* constraints
* migrations
* indexing
* transactions
* consistency
* timestamps
* deletion/retention
* audit behavior where applicable

# File Organization

Define:

* where application code belongs
* where UI components belong
* where business logic belongs
* where data access belongs
* where API/server code belongs
* where shared types/contracts belong
* where tests belong
* where configuration belongs

The structure must follow `architecture.md`.

Do not create folders merely because another framework commonly uses them.

# Final validation

Before outputting `code-standards.md`, verify internally:

* every rule is applicable to this project
* every rule is compatible with the confirmed architecture
* frontend rules match the confirmed UI system
* backend rules match the authoritative backend prompt
* security rules match the actual trust model
* data rules match the actual storage model
* workflow rules preserve Blueprint behavior
* state rules preserve confirmed lifecycle behavior
* testing rules reflect actual project risks
* no unsupported technology is introduced
* no invented requirement is introduced
* no future feature becomes a current implementation rule
* no contradiction exists with the Project Blueprint
* no contradiction exists with `project-overview.md`
* no contradiction exists with `architecture.md`
* no contradiction exists with `ui-context.md`
* each required section contains at least four actionable rules
* no placeholder remains

Then generate only:

`03-your-product/code-standards.md`

Stop.
