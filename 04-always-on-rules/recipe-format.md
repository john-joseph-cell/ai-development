# Recipe format

Every job file in `03-your-product` (`01-….md`, `02-….md`) must use these headings only.

Every recipe must implement one already-approved job from `03-your-product/00-build-plan.md`.

Every recipe is downstream of the confirmed Project Blueprint / Discovery truth.

The recipe must never become a place to invent product behavior, scope, entities, workflows, states, integrations, or requirements.

# Unit 01: [short name]

# Layer

* `frontend` | `backend` | `full-stack`
* Pair: [paired job name, if this backend job pairs with a frontend job]

# Goal

* One or two sentences.
* Describe what visibly or behaviorally exists when this job is done.
* State the actual product result, not merely the implementation activity.
* The result must remain inside the approved job scope.

# Blueprint Traceability

* Blueprint capability/workflow/rule/state/data/dependency/risk this job implements
* Include the relevant product requirement or workflow being satisfied
* Do not introduce requirements that do not exist in the confirmed Blueprint or downstream product truth

# Design

* Visual or API choices for this job only
* Follow `03-your-product/ui-context.md` and `03-your-product/architecture.md`
* Follow the applicable generated frontend and/or backend prompt sections
* Preserve confirmed product behavior and workflow
* Preserve relevant state, validation, permissions, and failure behavior
* Blast radius: what must not break
* Rollback: how to undo
* Do not introduce a new visual, interaction, API, data, or architectural system unless required by this job and already supported by product truth
* Do not use design decisions to redefine product scope

# Implementation

* Ordered steps
* Packages installed only in the job that first needs them
* Implement only the approved job
* Follow `03-your-product/code-standards.md`
* Respect architecture boundaries
* Preserve ownership, authorization, and data integrity
* Preserve valid state transitions
* Implement required validation and error handling
* Implement required failure, recovery, retry, timeout, concurrency, or idempotency behavior where confirmed
* Keep business-critical behavior explicit and testable
* Do not hide unrelated work inside the job
* Do not add speculative features or infrastructure

# Dependencies

* Jobs or services that must exist first
* Name the actual prerequisite job where applicable
* Include required external services, data foundations, authentication, environment configuration, migrations, or other confirmed dependencies
* Do not list invented dependencies
* A dependency must be completed before this job can be implemented correctly

# Verify when done

* Checkboxes a human can see on the Vercel URL. Never localhost
* Required lint, type, test, and build commands pass
* Selected frontend-prompt acceptance items that apply to this job
* Selected backend-prompt acceptance items that apply to this job
* Confirm the primary visible/behavioral result exists
* Confirm the relevant product workflow works as specified
* Confirm required success, loading, empty, error, disabled, permission, and recovery states where applicable
* Confirm relevant authorization and ownership behavior
* Confirm relevant state transitions and business rules
* Confirm relevant data integrity
* Confirm required external dependency behavior
* Confirm no unrelated product behavior was introduced
* Confirm the production deployment reflects the intended commit
* Verification is incomplete until the Vercel production result has been inspected

# Recipe laws

* One recipe = one Build Plan job
* One recipe must not implement another job
* One job must have one coherent result
* Stay inside the named Layer
* Preserve Pair rules for full-stack feature pairs
* Follow the Build Plan dependency order
* Preserve the feature-by-feature frontend → backend sequence where applicable
* Do not skip a required prerequisite simply because the current job is visually ready
* Do not invent missing product behavior
* Do not silently resolve unresolved product decisions
* Do not implement future-phase features
* Do not convert generic best practices into product requirements
* Do not create duplicate implementations of existing confirmed behavior
* Do not redefine the architecture inside the recipe
* Do not redefine the UI system inside the recipe
* Do not create a competing prompt system
* Do not mark the job complete inside the recipe
* Production proof is required before the job can be considered done
* Localhost is not production proof

# Blueprint preservation law

Every implementation decision must preserve confirmed:

* product behavior
* workflows
* business rules
* roles and permissions
* data relationships
* lifecycle and state transitions
* security boundaries
* integration behavior
* failure and recovery behavior
* constraints and limitations
* explicit exclusions

When a technical implementation detail is not specified, choose the simplest implementation consistent with the confirmed product truth and architecture.

Do not use an implementation gap as permission to invent product requirements.

# Scope law

The recipe may implement:

* the approved Build Plan job
* its explicitly required technical dependencies
* necessary implementation details supported by the architecture and standards
* required acceptance and verification work

The recipe may not implement:

* an unapproved feature
* a future feature
* a new user role
* a new workflow
* an unrelated refactor
* an unrelated integration
* an unrelated infrastructure layer
* speculative analytics
* speculative AI
* speculative commerce
* speculative notifications
* speculative search
* any other capability not supported by product truth

# State integrity law

When the job changes a stateful entity or workflow:

* use only confirmed states
* allow only confirmed valid transitions
* validate transitions at the correct architectural boundary
* preserve terminal-state behavior
* preserve cancellation, retry, recovery, or restoration rules where confirmed
* do not derive business state from temporary frontend presentation state
* do not allow the UI to bypass backend state rules

# Failure integrity law

When the job participates in a failure-prone workflow:

* implement the confirmed failure conditions
* provide the confirmed user/system outcome
* preserve retry behavior where required
* preserve timeout behavior where required
* preserve idempotency where required
* prevent duplicate side effects where required
* preserve recovery behavior
* do not replace required failure handling with silent fallback behavior

# Security integrity law

When the job touches protected behavior:

* validate runtime input
* authorize server-side
* enforce ownership or tenant boundaries where applicable
* keep secrets out of client-visible code
* protect sensitive data
* prevent unsafe direct-object access
* return safe errors
* never rely on hidden UI controls as the security boundary

# Full-stack pairing law

For a full-stack feature pair:

* frontend job and backend job must represent the same confirmed feature
* frontend job comes first where technically valid
* backend pair must name the frontend job in `Pair`
* backend job must not silently expand the frontend feature
* frontend job must not fake behavior that requires the backend pair
* verification must prove the real end-to-end workflow when the pair is complete

Where a backend foundation must exist before the frontend feature can work, that prerequisite is allowed before the pair.

# Verification law

Verification must prove the actual job, not merely prove that the application builds.

At minimum, verification should establish:

* production deployment is reachable
* intended route/surface/API behavior exists
* intended workflow behaves correctly
* relevant state and error behavior works
* required quality gates pass
* no obvious regression in the job's declared blast radius

For jobs with security, data, payment, integration, or other critical behavior, verify the corresponding critical path explicitly.

# Rollback law

Every recipe must state how to undo the change.

Rollback must reflect the actual blast radius.

When the job includes:

* data migration
* schema change
* external configuration
* destructive operation
* irreversible state change

the rollback approach must address that specific risk rather than saying only "revert the commit".

# Output law

Recipe files must contain the required headings above and remain focused on the single job.

Do not add unrelated sections.

Do not write explanatory essays outside the recipe structure.

Do not use `[placeholders]` in a completed recipe.

# Completion rule

A recipe describes the work.

A successful implementation executes the recipe.

A successful verification proves the result.

Only after production verification may the corresponding Build Plan job move from `Pending` to completed state.
