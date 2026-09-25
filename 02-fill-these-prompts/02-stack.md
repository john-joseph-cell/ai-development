# Prompt: stack

Use this after the Project Blueprint / Discovery stage and after:

`03-your-product/project-overview.md`

is real.

# You replace

`03-your-product/architecture.md`

# You read

* `03-your-product/project-overview.md`
* `04-always-on-rules/backend-prompt.md` — the only backend prompt source
* the confirmed Project Blueprint from the discovery conversation

# Blueprint dependency

The Project Blueprint is an upstream requirement for architecture.

Before recommending any stack, use the Blueprint and `project-overview.md` to understand:

* required capabilities
* important workflows
* actors and permissions
* important state transitions
* data requirements
* external dependencies
* security requirements
* reliability requirements
* meaningful scale requirements
* limitations
* constraints
* explicit exclusions
* confirmed product decisions

Do not choose technology independently of this information.

Architecture exists to support the product. The product does not exist to justify the architecture.

# Architecture principles

Recommend the **smallest valid architecture** that correctly supports the confirmed product.

Prioritize:

* correctness
* security
* predictable behavior
* operational simplicity
* maintainability
* testability
* reliability
* appropriate scalability
* clear ownership
* reversible decisions where practical

Do not optimize for:

* architectural fashion
* maximum infrastructure
* unnecessary microservices
* theoretical future scale
* unnecessary AI infrastructure
* vendor count
* technology novelty

Do not add infrastructure merely because a similar product might use it.

# You ask

Recommend the smallest valid set using the Recommendation law in `backend-prompt.md`.

Ask only for names:

* Shape
* API
* Webhooks only when required
* Data
* Auth
* Runtime
* Queues only when required
* Reliability
* AI

Mark one recommendation per group and give one short reason.

Do not paste or summarize the backend prompt.

Wait for confirmation.

# Technology decision rules

Every recommendation must be justified by confirmed product requirements.

For each selected technology or architecture level, verify:

* which product requirement it satisfies
* which workflow depends on it
* which data behavior requires it
* which reliability/security requirement requires it
* what constraint it addresses
* what complexity it introduces

If a component has no clear product or technical reason, do not recommend it.

Do not introduce:

* a database when durable storage is unnecessary
* a queue when work does not need durable asynchronous processing
* a cache when correctness does not require caching and performance has not justified it
* microservices when a simpler architecture is sufficient
* AI infrastructure when the product does not require AI
* a separate API when the product can be correctly served without one
* advanced runtime infrastructure merely for theoretical scale

# Architecture dependency check

Before asking for confirmation, verify internally that the proposed selections can support:

### Product behavior

* major features
* important workflows
* lifecycle/state transitions
* business rules
* actor permissions

### Data behavior

* required entities
* relationships
* ownership
* consistency
* retention
* history/audit needs

### Integration behavior

* external APIs
* webhooks
* provider failures
* retries
* timeouts
* reconciliation where applicable

### Security behavior

* authentication
* authorization
* ownership
* tenant isolation
* sensitive data
* secrets

### Reliability behavior

* transactions
* idempotency
* failure handling
* recovery
* asynchronous work where required

### Scale behavior

Only when material:

* expected users
* concurrency
* content volume
* transaction volume
* geographic distribution
* growth expectations

Do not invent numerical scale requirements.

# Architecture selection law

Use the recommendation rules from:

`04-always-on-rules/backend-prompt.md`

Do not override them with personal framework preferences.

When the product does not clearly require an advanced architecture, prefer the simpler valid option.

If two options are both valid, prefer the option with:

* fewer moving parts
* lower operational burden
* clearer ownership
* easier testing
* easier debugging
* easier rollback
* better fit with confirmed constraints

# Blocking architecture conflicts

If the confirmed product requirements cannot be supported by the available architecture choices:

Do not silently invent a new architecture level.

Explain the conflict briefly.

Record the required decision as an open question in:

`03-your-product/progress-tracker.md`

Stop until the conflict is resolved.

# Confirmation gate

Do not generate `architecture.md` until the user confirms the recommended selections.

Do not infer confirmation from:

* silence
* unrelated messages
* continuing the conversation
* asking another question
* requesting implementation

Confirmation must apply to the architecture selections.

# You write

After confirmation, replace:

`03-your-product/architecture.md`

Use plain markdown.

No extra commentary.

Use exactly:

# Architecture

## Backend levels

Use exact confirmed names.

## Stack

Use:

| Layer | Technology | Role |
| ----- | ---------- | ---- |

Include only confirmed technologies.

## Host

Include:

* Vercel
* project folder
* GitHub repository URL if known
* Vercel production URL if known
* commands
* environment variable names only

Do not invent URLs.

Do not include secret values.

## System Boundaries

Describe the responsibility of each major system boundary.

The boundaries must reflect the actual product workflows and ownership established by the Blueprint.

## Storage Model

Describe where each category of data belongs and the ownership/relationship model.

Preserve the data requirements established by the Blueprint.

Do not invent entities that the product does not require.

## Auth and Access Model

Describe:

* authentication
* authorization
* roles
* ownership
* tenant boundaries
* resource access
* important permission rules

These must reflect the confirmed actors and permissions from the Blueprint.

## API law

Apply the Universal backend foundation from:

`04-always-on-rules/backend-prompt.md`

in project-specific words.

The API model must reflect the actual workflows and contracts required by the product.

## Invariants

Include at least four concrete, testable invariants derived from the confirmed product behavior.

Prefer invariants that protect:

* ownership
* permissions
* data integrity
* financial correctness
* state transitions
* idempotency
* tenant isolation
* workflow correctness

Only include invariants relevant to the project.

## Reliability Model

Describe the important reliability behavior required by the project, including where applicable:

* transaction boundaries
* idempotency
* retries
* timeouts
* dependency failures
* asynchronous work
* reconciliation
* recovery

Do not introduce reliability machinery that the product does not need.

## External Dependencies

List confirmed external systems only.

For each relevant dependency describe:

* purpose
* dependency boundary
* failure impact
* timeout/retry expectations
* fallback or recovery approach when applicable

Do not invent vendors.

## Constraints and Limitations

Record the important confirmed:

* technical constraints
* product constraints
* business constraints
* hosting constraints
* scale limitations
* dependency limitations
* security limitations

Do not hide meaningful limitations.

## Architecture Decisions

Document important confirmed decisions using:

* Decision
* Reason
* Trade-off
* Consequence

Do not document theoretical alternatives as current architecture.

# Rules

* Use selections and rules only from `04-always-on-rules/backend-prompt.md`.
* Keep the architecture as small as the product permits.
* Vercel is the default host, not a database.
* Edge is selected only for compatible work; do not claim it is universally faster.
* Propose a kebab-case project folder; do not create it or a GitHub repo.
* No UI tokens.
* No `[placeholders]`.
* Do not introduce technologies not present in the confirmed architecture.
* Do not introduce infrastructure without a product or technical reason.
* Ensure every major feature in `project-overview.md` has a technically valid place in the architecture.
* Ensure every important workflow has the technical support it requires.
* Ensure important state transitions are technically enforceable.
* Ensure authorization boundaries are represented by the architecture.
* Ensure data ownership and consistency requirements are represented.
* Ensure important external dependencies have defined failure boundaries.
* Ensure the architecture does not contradict the Blueprint.
* Ensure every architectural component has a product reason.
* Preserve explicit product limitations and constraints.
* Do not turn future-phase ideas into current infrastructure.
* Do not silently choose unresolved architecture decisions.
* Do not add UI design decisions.
* Do not add frontend prompt content.
* Do not generate code.
* Do not generate build jobs.

# Final validation

Before outputting `architecture.md`, verify internally:

* every major in-scope capability has a valid technical home
* important workflows are supported
* actor permissions are enforceable
* state transitions are representable
* required data is supported
* required integrations are supported
* important failure behavior is supported
* security boundaries are explicit
* reliability requirements are supported
* scale requirements are supported where material
* important limitations are preserved
* no unsupported technology was introduced
* no technology exists without a reason
* no contradiction exists with `project-overview.md`
* no contradiction exists with the confirmed Project Blueprint
* environment variable values and secrets are absent
* no placeholder remains

Then generate only:

`03-your-product/architecture.md`

Stop.
