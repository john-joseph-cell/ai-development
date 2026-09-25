# /architect

Write one recipe.

No application code.

The recipe is the executable design contract for exactly one build-plan job.

Do not create or modify implementation source during `/architect`.

---

# Need

* The job name from the user, or the first unfinished name in `03-your-product/00-build-plan.md`
* `03-your-product/project-overview.md`
* `03-your-product/architecture.md`
* `03-your-product/ui-context.md`
* `03-your-product/progress-tracker.md`
* `03-your-product/00-build-plan.md`
* Matching generated `frontend-prompt.md` and/or `backend-prompt.md`
* `04-always-on-rules/recipe-format.md`
* Relevant project blueprint/project truth
* Existing project state needed to understand the current job
* Existing related recipes when the current job depends on or pairs with another job

---

# Purpose

Translate one already-defined build-plan job into a precise implementation recipe.

The recipe must connect:

`Project Truth`
→ `Build-Plan Job`
→ `Recipe`
→ `Develop`
→ `Verify`
→ `Ship`

Do not reinterpret the entire product.

Do not create a new roadmap.

Do not turn `/architect` into a general architecture redesign session.

Stay inside the selected job.

---

# Job identity

Before writing the recipe, establish:

* exact job name
* job path/number
* Layer
* Pair when applicable
* project folder
* relevant prerequisites
* relevant dependencies
* current project state

If the user explicitly named a job, use that job.

Otherwise use the first unfinished job in `03-your-product/00-build-plan.md`.

Do not silently choose another job.

If the job cannot be determined unambiguously:

* do not create a recipe for a different job
* identify the ambiguity
* record the appropriate open question
* stop

---

# Source-of-truth order

Use this priority when creating the recipe:

1. Confirmed project/product truth
2. Explicit current job in the build plan
3. Existing architecture decisions
4. Existing UI context
5. Existing selected frontend/backend personas
6. Existing accepted recipes/decisions that affect the job
7. Project constraints and known risks
8. Reasonable implementation assumptions

Never use a generic best practice to silently override confirmed project truth.

Never invent product behavior to make the recipe look complete.

---

# Blueprint relationship

Use the project blueprint as upstream context.

Extract only the information necessary for this job, such as:

* affected requirement
* affected user/workflow
* relevant business rule
* relevant state transition
* affected data/domain
* relevant integration
* security constraint
* quality requirement
* limitation
* risk
* acceptance expectation

Do not copy the entire blueprint into the recipe.

Do not reproduce all blueprint headings.

The recipe is a **job-level implementation contract**, not another copy of the project blueprint.

---

# Stay inside the job

The recipe must answer:

> What exactly is being built in this one job?

It must not silently expand into:

* the next job
* unrelated product work
* broad refactoring
* speculative features
* future infrastructure
* general cleanup
* unrelated accessibility work
* unrelated SEO work
* unrelated performance work

Supporting changes are permitted only when the current job genuinely requires them.

---

# Recipe scope

Define clearly:

### In scope

What this job must implement.

### Supporting changes

Shared/component/API/data/configuration changes that are genuinely necessary.

### Out of scope

What this job must not implement.

### Dependencies

What must already exist.

### Follow-up

What belongs to later jobs.

Do not use "nice to have" items to expand the current job.

---

# Preconditions

Before implementation can begin, identify required preconditions.

Examples:

* prerequisite job completed
* route exists
* component exists
* API contract exists
* database structure exists
* authentication exists
* design token exists
* third-party integration configured
* required decision confirmed

If a prerequisite is not satisfied:

* identify it
* do not invent a workaround
* determine whether the job is actually ready

---

# Implementation boundary

Define the smallest reasonable boundary for the job.

Where applicable identify:

* routes
* pages
* components
* shared primitives
* frontend state
* API endpoints/actions
* services/modules
* database entities
* migrations
* background jobs
* integrations
* configuration

Do not prescribe files that are not necessary.

Do not create artificial architectural boundaries merely to make the recipe appear detailed.

---

# Frontend recipe requirements

For frontend jobs, make the implementation observable and testable.

The recipe must define applicable:

* route/page
* composition
* visual direction
* typography
* surface system
* spacing
* signature element
* interaction model
* states
* motion
* responsive behavior
* accessibility
* SEO
* performance considerations

The selected visual direction from `frontend-prompt.md` must be treated as an implementation requirement where the persona applies.

Do not reduce the frontend recipe to:

> Build a page with cards and buttons.

---

# Frontend visual contract

When visual requirements exist, specify:

* visual thesis
* primary hierarchy
* signature visual/interaction
* key composition
* important typography behavior
* surface treatment
* spacing rhythm
* motion behavior
* responsive recomposition

The recipe must make the visual result testable on the Vercel production URL.

The Verify section must let a reviewer determine whether the selected direction is actually implemented.

Do not accept vague wording such as:

> Make it modern.

Use observable behavior.

---

# Frontend state contract

For relevant interactive elements define applicable:

* default
* hover
* focus
* focus-visible
* active/pressed
* selected
* checked
* open
* loading
* disabled
* success
* error
* empty

Only include states relevant to the actual component/workflow.

Do not invent states merely to increase checklist size.

---

# Frontend responsive contract

Define where relevant:

* mobile behavior
* tablet behavior
* desktop behavior
* wide-screen behavior
* breakpoint changes
* component collapse
* navigation changes
* spacing changes
* typography changes

Mobile must be testable as an intentional composition.

Do not merely state:

> responsive.

---

# Frontend accessibility contract

Where UI is in scope, define testable requirements for:

* semantic structure
* keyboard access
* focus-visible
* labels
* accessible names
* heading hierarchy
* landmarks
* contrast
* reduced motion
* dialogs/menus/forms when relevant

Do not rely on vague:

> accessible.

---

# Frontend SEO contract

When public/indexable UI is part of the job, define the applicable SEO behavior under the recipe's SEO requirements.

Where relevant include:

* route indexability
* title
* description
* canonical
* robots behavior
* structured data
* sitemap impact
* internal-link requirements
* Open Graph metadata
* semantic headings

Do not invent SEO claims.

Do not add SEO work when the current job does not affect public/indexable content.

---

# Backend recipe requirements

For backend jobs, define applicable:

* contract
* request/input
* response/output
* validation
* authentication
* authorization
* ownership
* tenant boundaries
* data behavior
* business rules
* error behavior
* idempotency
* retries/timeouts where relevant
* asynchronous behavior
* integrations
* observability
* security

Do not reduce backend work to:

> Create an endpoint.

---

# Backend contract

For API/action jobs, make clear:

* operation
* inputs
* required fields
* validation
* response shape
* success behavior
* error behavior
* authorization
* pagination/bounds when relevant
* compatibility considerations
* idempotency where applicable

The Verify section must make the contract testable.

---

# Backend data contract

When data is involved, identify:

* affected entities
* ownership
* relationships
* required fields
* uniqueness
* integrity constraints
* state changes
* migration requirements
* deletion/retention implications
* consistency/concurrency considerations

Do not invent a new datastore when the architecture does not require it.

---

# Backend failure contract

For important operations define relevant:

* invalid input
* missing resource
* unauthorized access
* forbidden access
* duplicate request
* timeout
* dependency failure
* retry
* partial failure
* recovery
* cancellation
* expiration

Not every job requires every failure category.

Include what the actual operation needs.

---

# Full-stack recipe requirements

For full-stack jobs, explicitly connect:

`User Action`
→ `Frontend`
→ `API/Action`
→ `Backend`
→ `Data/Integration`
→ `Response`
→ `Frontend State`
→ `Final Outcome`

The recipe must define enough behavior for both sides to implement the same feature.

---

# Pairing rules

For full-stack projects:

* if this is a backend job for a feature that already has a frontend job, set `Pair` to the frontend job name
* if this is the frontend job, note that the backend pair comes next
* preserve feature-by-feature ordering
* ensure the pair describes the same user-visible behavior
* ensure the pair uses a compatible contract

Do not create artificial Pair relationships.

---

# Contract consistency

When a frontend/backend pair exists, verify the recipe does not create contradictory expectations.

Check:

* request shape
* response shape
* validation
* loading states
* error states
* authentication
* authorization
* persistence
* user-visible completion

A pair should not require one side to assume undocumented behavior from the other.

---

# Workflow contract

Every important workflow in the recipe should identify applicable:

* trigger
* preconditions
* main path
* alternate path
* validation
* business rules
* state changes
* failure
* recovery
* cancellation
* retry
* timeout
* partial completion
* idempotency
* concurrency
* notifications
* audit
* final state

Do not force irrelevant workflow categories into tiny jobs.

Include the ones needed to make the job implementation unambiguous.

---

# State consistency

When the job changes a stateful object:

Define:

* current state
* target state
* valid transition
* who can trigger it
* automatic behavior
* invalid transition behavior
* failure behavior
* terminal behavior where applicable

The recipe's state behavior must not contradict established project workflows.

---

# Business rules

Extract only rules relevant to this job.

For each important rule identify, where applicable:

* condition
* allowed behavior
* forbidden behavior
* exception
* consequence
* actor
* ownership
* permission

Business rules must not remain hidden inside vague implementation instructions.

---

# Security contract

For backend or security-sensitive frontend work, define applicable:

* authentication
* authorization
* ownership
* tenant isolation
* input validation
* sensitive-data handling
* secret handling
* abuse boundaries
* safe errors

Do not introduce security requirements that are unrelated to the current job.

Do not weaken established project security rules.

---

# Data/integration dependencies

For external systems, identify:

* dependency
* purpose
* data exchanged
* authentication
* expected failure behavior
* rate/usage implications where known
* fallback/recovery where relevant

If provider behavior is uncertain and materially affects the job:

* mark it as needing verification
* do not fabricate the behavior

---

# Observability requirements

When the job adds meaningful runtime behavior, define the minimum useful observability.

Examples:

* structured logs
* errors
* metrics
* traces
* job/queue monitoring
* client-side error reporting

The recipe should state what must be observable, not merely:

> Add logging.

---

# Performance requirements

Only specify performance requirements relevant to the job.

Where applicable define:

* route loading
* response latency
* payload bounds
* pagination
* rendering behavior
* image/media behavior
* animation behavior
* expensive operations
* background processing

Use measurable targets only when they are supported by project requirements or evidence.

Never invent arbitrary performance numbers.

---

# SEO/performance/accessibility interaction

When a frontend job affects more than one quality discipline, identify their interaction.

Examples:

* route rendering affects SEO and initial loading
* images affect SEO, accessibility, and performance
* animations affect UX, accessibility, and performance
* dynamic content affects layout stability and SEO
* navigation affects accessibility and crawlability

Do not optimize one discipline by silently breaking another.

---

# Acceptance contract

Every recipe must have a visible Verify section using:

* observable behavior
* exact route/action
* expected outcome
* relevant state
* relevant viewport
* relevant actor
* safe production-test method

Do not write verification items that cannot actually be checked.

Avoid vague checks such as:

* Looks good
* Works correctly
* Is scalable
* Is secure
* Is responsive

Replace them with observable behavior.

---

# Production verification requirement

Verify checkboxes must be testable on the Vercel production URL.

Never use localhost as final proof.

For frontend verification, include observable checks such as:

* route loads
* navigation works
* responsive composition is correct
* signature exists
* required states behave correctly
* keyboard/focus behavior works
* motion behaves correctly
* reduced motion works where relevant

For backend verification, include safe checks such as:

* expected request succeeds
* malformed input is rejected
* unauthorized access is rejected
* ownership boundary is enforced
* bounded/paginated response exists
* error does not expose secrets
* duplicate/idempotent behavior works where applicable

Do not require dangerous production mutations.

---

# Verify checklist quality

Each checkbox should be:

* specific
* observable
* reproducible
* job-scoped
* production-testable where applicable

A good checkbox should allow a verifier to answer:

> What action was taken?

> What should happen?

> What actually happened?

Do not hide multiple unrelated requirements inside one vague checkbox.

---

# Blast radius

Name the blast radius explicitly.

Consider:

* routes
* shared components
* design system
* API consumers
* database
* background jobs
* integrations
* authentication
* authorization
* tenant boundaries
* SEO
* accessibility
* performance
* deployment

For shared changes, identify representative existing behavior that needs regression verification.

Do not exaggerate the blast radius.

---

# Rollback

Every recipe must include rollback guidance appropriate to the job.

Identify:

* what can be reverted safely
* deployment rollback
* feature-flag rollback where applicable
* data rollback considerations
* migration implications
* external integration implications
* irreversible effects
* known-good deployment/commit when practical

Do not claim data rollback is possible when the operation is irreversible.

---

# Risk

Name important job-specific risks.

Prioritize realistic risks such as:

* security
* data integrity
* authorization
* tenant isolation
* API compatibility
* migration
* deployment
* responsive regression
* accessibility
* performance
* external dependency
* user workflow disruption

Do not generate a giant generic risk list.

---

# Dependencies

Identify job dependencies accurately.

Possible dependencies:

* prior recipe
* shared component
* API
* database
* authentication
* design token
* external provider
* infrastructure
* existing state

If a dependency is not actually required, do not add it.

---

# Open-question rule

If product behavior is missing or materially ambiguous:

* add an open question in `03-your-product/progress-tracker.md`
* identify exactly what is unclear
* identify why the recipe cannot safely resolve it
* stop recipe generation

Do not invent the behavior.

Do not hide the ambiguity inside implementation wording.

---

# Existing recipe consistency

When related jobs already exist, inspect them for:

* shared contracts
* shared states
* shared components
* previous decisions
* previous dependencies
* paired workflows
* overlapping scope

The new recipe must not silently contradict an established earlier recipe.

If a contradiction exists:

* identify it
* determine whether it is intentional
* preserve confirmed decisions
* update the appropriate truth/decision record when required
* stop when the contradiction is blocking

---

# No broad architecture redesign

`/architect` may identify an architecture problem relevant to the current job.

It must not silently redesign the whole system.

If the job cannot be implemented without a new major architecture decision:

* identify the required decision
* explain the affected boundary
* record the open question/decision
* stop

Do not invent a replacement architecture inside the recipe.

---

# No implementation

Do not write:

* application source
* application components
* API implementation
* database implementation
* infrastructure implementation
* deployment code

The recipe describes what implementation must accomplish.

It does not implement it.

---

# Recipe-format compliance

Write:

`03-your-product/[nn]-[name].md`

using **only the headings defined in**:

`04-always-on-rules/recipe-format.md`

Do not invent additional recipe headings.

Do not remove required recipe-format headings.

Do not create a second recipe format.

Respect the exact expected field names and structure.

---

# Recipe quality gate

Before writing the recipe, confirm:

### Identity

* correct job
* correct Layer
* correct Pair

### Scope

* in scope defined
* out of scope defined
* dependencies identified

### Behavior

* workflow understandable
* business rules understandable
* states understandable

### Frontend, when applicable

* visual direction
* signature
* motion
* states
* breakpoints/responsive behavior
* accessibility
* SEO/performance where relevant

### Backend, when applicable

* contracts
* validation
* authorization
* data behavior
* failure handling
* reliability
* security

### Verification

* Verify items are observable
* Vercel production testing is possible
* dangerous production tests are avoided

### Operations

* blast radius identified
* rollback understood
* risks identified

If any critical requirement is missing:

* add the appropriate open question
* stop
* do not fabricate the missing information

---

# Final recipe validation

Before saving:

1. Compare the recipe against the current build-plan job.
2. Compare it against project truth.
3. Compare it against architecture.
4. Compare it against UI context when applicable.
5. Compare it against the selected frontend/backend persona.
6. Compare it against related recipes.
7. Confirm no future-job scope leaked in.
8. Confirm every important Verify item is observable.
9. Confirm blast radius and rollback are realistic.
10. Confirm the recipe contains no application code.

---

# Output

Write exactly one recipe:

`03-your-product/[nn]-[name].md`

Then report:

* recipe path
* job name
* Layer
* Pair when applicable
* scope summary
* prerequisites
* blast radius
* rollback summary
* Verify coverage
* any open question/blocker

Do not create application source.

Do not start `/develop`.

Do not create a GitHub repository.

---

# Stop

* Do not invent features
* Do not invent product behavior
* Do not invent business rules
* Do not invent architecture
* Do not write application source
* Do not modify application code
* Do not start `/develop`
* Do not start `/verify`
* Do not start `/ship`
* Do not create a GitHub repo
* Do not create deployment infrastructure
* Do not create unrelated jobs
* Do not combine multiple jobs into one recipe
* Do not silently expand scope
* Do not silently contradict established architecture
* Do not weaken frontend persona requirements
* Do not weaken backend persona requirements
* Do not make Verify checkboxes vague
* Do not use localhost as final proof
* Do not make destructive production verification requirements
* Do not hide missing product decisions
* Do not create a recipe when a blocking product decision is unresolved

---

# Core principle

`/architect` converts one approved job into one precise implementation contract.

The recipe must make it possible for `/develop` to know:

> What exactly do I build?

and for `/verify` to know:

> What exactly do I have to prove?

and for `/ship` to know:

> What exactly am I releasing?

The recipe is complete when the job can be implemented and independently verified without inventing missing product behavior.
