# /develop

Build one job only.

Follow `05-slash-commands/live.md` when the job is green. Never use localhost as proof.

The current job is the only implementation scope for this command.

Do not start the next job.

Do not silently expand the current job because an adjacent improvement appears useful.

---

# Need

* Job name from the user, or the first unfinished name in `03-your-product/00-build-plan.md`
* That job's recipe (`03-your-product/01-….md`)
* `01-start-here/AGENTS.md` read order and the matching persona
* Ready gate in `01-start-here/HOW-TO-BUILD.md` must already be true
* A GitHub repo and Vercel project should already exist **for the project folder** named in `03-your-product/architecture.md`
* GitHub repo URL and Vercel Project URL in Host. If missing, ask the user, write them in, then continue
* If that folder does not exist, stop and tell the user to finish **Files are ready** in `01-start-here/HOW-TO-BUILD.md`
* `03-your-product/project-overview.md`
* `03-your-product/architecture.md`
* `03-your-product/ui-context.md` when UI is in scope
* `03-your-product/progress-tracker.md`
* `03-your-product/00-build-plan.md`
* selected `frontend-prompt.md` sections when frontend work is in scope
* selected `backend-prompt.md` sections when backend work is in scope
* current project repository status before implementation

---

# Current-job identity

Establish the current job before writing application code.

Confirm:

* job name
* recipe path
* job Layer
* Pair when applicable
* project folder
* selected frontend persona when applicable
* selected backend persona when applicable
* expected routes/components/services when the recipe defines them
* expected acceptance behavior
* Verify requirements
* relevant architecture constraints

If the user explicitly named a job, use that job.

Otherwise use the first unfinished job in `03-your-product/00-build-plan.md`.

Do not silently change job identity after implementation begins.

If the current job is ambiguous, stop and resolve it before writing application code.

---

# Read order and truth

Follow `01-start-here/AGENTS.md` exactly.

Treat the following as authoritative within their intended scope:

* project truth
* current recipe
* architecture
* UI context
* selected frontend/backend personas
* current progress/build-plan state

The recipe is the implementation scope for the current job.

The project blueprint/truth explains why the job exists and what the system is expected to do.

The generated frontend/backend personas define the selected engineering/design discipline.

Do not invent new product behavior because the code structure makes another approach convenient.

---

# Preflight

Before writing application files:

1. Confirm the Ready gate is true.
2. Read the current job recipe completely.
3. Read relevant project truth and architecture.
4. Read the selected frontend persona for UI jobs.
5. Read the selected backend persona for backend jobs.
6. Inspect the existing project structure.
7. Inspect the existing implementation relevant to this job.
8. Inspect current Git status.
9. Identify existing uncommitted changes.
10. Determine whether existing changes belong to this job.
11. Confirm the project repository and project folder.
12. Confirm configured commands from `Architecture → Host`.
13. Confirm the required Verify checklist.
14. Identify any unresolved product decision that blocks implementation.

Do not begin coding until the implementation scope is understood.

---

# Existing work protection

Before editing:

* preserve valid existing user work
* do not reset the repository
* do not overwrite unrelated changes
* do not discard uncommitted work
* do not perform destructive Git cleanup
* do not silently reformat unrelated files

If the working tree already contains unrelated changes:

* preserve them
* do not stage them
* do not modify them unnecessarily
* do not include them in the current job commit

If existing changes materially conflict with the current job, stop and report the conflict rather than silently resolving it.

---

# Scope lock

The recipe defines the current implementation boundary.

Before coding, identify:

### In scope

What this job must implement.

### Supporting changes

Shared code/configuration changes genuinely required for this job.

### Out of scope

What must not be implemented during this job.

### Future work

Useful improvements that belong to later jobs.

Do not promote:

* future work
* cleanup
* unrelated refactors
* new features
* speculative infrastructure

into the current job merely because they are convenient to implement now.

---

# Blueprint-to-recipe traceability

Before implementation, mentally map:

`Project Requirement`
→ `Current Job`
→ `Recipe`
→ `Affected Workflow`
→ `Affected Frontend/Backend Boundary`
→ `Implementation`
→ `Verify Evidence`

The current implementation should be explainable from the project truth and recipe.

If a significant implementation decision cannot be justified by:

* the project requirement
* architecture
* current recipe
* selected frontend/backend persona
* an explicit existing decision

do not invent it silently.

Record the ambiguity and stop when it is blocking.

---

# Recipe completeness gate

Before coding, confirm the recipe contains enough information to implement the job.

For frontend jobs, verify the recipe gives enough detail to test, where applicable:

* visual direction
* signature element
* composition
* typography direction
* surfaces
* motion
* interaction states
* responsive behavior
* accessibility expectations
* relevant routes

For backend jobs, verify the recipe gives enough detail to test, where applicable:

* contract
* validation
* authorization
* ownership
* tenant behavior
* data behavior
* failure behavior
* reliability expectations
* relevant integrations

For full-stack jobs, verify:

* frontend/backend boundaries
* API/data contract
* Pair relationship
* user-visible workflow
* acceptance behavior

If product behavior is missing or materially ambiguous:

* add one focused open question to `03-your-product/progress-tracker.md`
* stop
* do not invent the behavior

---

# Implementation principles

Choose the smallest coherent implementation that satisfies:

* current job
* project requirements
* architecture
* selected persona
* quality requirements

Do not optimize for:

* maximum code
* maximum infrastructure
* maximum component count
* maximum abstraction
* maximum animation
* maximum dependencies

Professional implementation means:

* correct boundaries
* understandable code
* appropriate abstraction
* predictable behavior
* testability
* maintainability
* production safety

---

# Architecture adherence

Follow `03-your-product/architecture.md`.

Do not silently introduce:

* new framework
* new database
* new cache
* new queue
* new event broker
* new authentication system
* new cloud service
* new deployment model
* new AI infrastructure
* new microservice
* new serverless boundary

unless the current job and established architecture explicitly require it or the architecture has been intentionally updated.

If the current job exposes an architecture gap:

* identify the gap
* determine whether it is blocking
* record a focused decision/open question when necessary
* do not silently redesign the system

---

# Frontend implementation

When the job affects frontend:

Follow:

* `ui-context.md`
* selected sections in `frontend-prompt.md`
* current recipe
* existing design system

Implement the actual selected direction.

Do not replace required visual direction with:

* generic hero sections
* generic cards
* placeholder circles
* fake terminal windows
* fake metrics
* random gradients
* decorative widget collections
* repeated fade-up animations

Before writing frontend code, map the recipe to:

* composition
* typography
* surfaces
* spacing
* visual hierarchy
* signature interaction/visual
* motion
* component states
* breakpoints
* accessibility

If the recipe cannot test the required visual result, stop and run `/architect`.

---

# Frontend design-system adherence

Reuse existing:

* design tokens
* typography
* spacing
* radius
* surfaces
* components
* interaction states
* responsive primitives
* accessibility behavior

Do not create a parallel design system for a single job.

Do not duplicate an existing primitive merely because local implementation seems faster.

If a new shared primitive is genuinely required:

* keep it focused
* make the abstraction reusable
* ensure the current job actually depends on it
* avoid unrelated redesign

---

# Frontend responsive implementation

For UI work:

* implement mobile intentionally
* recompose tablet behavior where appropriate
* maintain desktop hierarchy
* handle wide layouts
* prevent horizontal overflow
* prevent excessive whitespace
* preserve interaction usability

Do not treat mobile as a scaled desktop.

Use the selected breakpoint system.

Do not invent arbitrary one-off breakpoints without a reason.

---

# Frontend interaction-state implementation

Implement applicable states explicitly:

* default
* hover
* focus
* focus-visible
* active / pressed
* selected
* checked
* open
* loading
* disabled
* success
* error

Do not conflate visual state with actual application state.

Do not create sticky hover behavior on touch devices.

Do not remove keyboard focus indicators.

---

# Frontend motion implementation

Follow the selected motion direction from the current persona/recipe.

Motion must:

* have a purpose
* communicate state/continuity
* remain performant
* behave correctly across breakpoints
* honor reduced motion

Do not add motion merely because an animation library is available.

Do not use expensive effects without a project-specific reason.

---

# Frontend SEO implementation

When public/indexable pages are in scope:

* implement the recipe's SEO requirements
* use semantic HTML
* provide appropriate metadata
* maintain canonical behavior
* preserve intended indexability
* support structured data where required
* maintain crawlable links
* preserve sitemap/robots strategy
* maintain social metadata where relevant

Do not invent:

* rankings
* reviews
* testimonials
* statistics
* awards
* certifications
* search-performance claims

Do not create SEO-only filler content.

---

# Frontend accessibility implementation

Follow the selected frontend prompt and project requirements.

Use:

* semantic HTML
* correct labels
* accessible names
* keyboard navigation
* visible focus
* correct heading hierarchy
* landmarks
* appropriate ARIA
* reduced motion
* contrast
* accessible errors
* accessible dynamic states

Prefer native semantics before ARIA.

Do not use ARIA to compensate for incorrect native controls when a native element is sufficient.

---

# Backend implementation

When the job affects backend behavior:

Follow:

* `architecture.md`
* selected sections in `backend-prompt.md`
* current recipe
* existing service/module boundaries

Implement:

* contracts
* validation
* authorization
* ownership
* tenant isolation
* data integrity
* error behavior
* idempotency
* reliability
* observability

where applicable to the job.

Do not create infrastructure merely because the backend persona lists it as an available capability.

---

# Backend API discipline

For API work:

* preserve established contracts
* validate inputs
* use appropriate status codes
* return stable error structures
* enforce authorization server-side
* keep responses bounded
* paginate large collections
* preserve compatibility
* document contract changes when required

Do not silently change existing API semantics.

If a breaking API change is genuinely required:

* identify consumers
* identify compatibility impact
* follow the architecture's versioning/migration strategy
* update relevant tests and documentation

---

# Backend data discipline

For database/data work:

* preserve domain invariants
* enforce important constraints server-side
* consider concurrency
* consider duplicate operations
* preserve tenant/ownership boundaries
* handle migrations safely
* avoid unnecessary schema changes
* avoid unnecessary database technologies

Do not silently modify production data models beyond the current job.

---

# Backend reliability discipline

For remote interactions or asynchronous work, follow the selected backend persona's applicable rules for:

* timeouts
* retries
* idempotency
* duplicate delivery
* failure handling
* partial completion
* recovery
* dead-letter behavior
* observability

Do not add blind retries.

Do not make non-idempotent operations unsafe through repeated execution.

---

# Backend security discipline

Never weaken:

* authentication
* authorization
* ownership checks
* tenant isolation
* input validation
* secret handling
* safe errors

Never place:

* secrets
* credentials
* private keys
* tokens

in source code.

Never use temporary authentication bypasses as a development convenience in production-bound code.

---

# Full-stack implementation

For full-stack jobs, implement the complete contract across the pair.

Verify alignment between:

* frontend request
* API contract
* backend validation
* authorization
* database behavior
* response
* frontend state

Do not use frontend assumptions to compensate for missing backend guarantees.

Do not use backend behavior that produces undocumented frontend states.

---

# Dependency discipline

Before adding a dependency ask:

* Is it required?
* Does an existing project dependency already solve it?
* Can the platform solve it simply?
* Does it increase bundle/runtime cost?
* Does it introduce security risk?
* Does it increase maintenance burden?
* Does it create vendor lock-in?
* Is it appropriate for the current job?

Do not add packages merely because they are popular.

---

# File-scope discipline

Write application files only inside the project folder.

Never write:

* application `package.json`
* application `app/`
* application `src/`
* application `README.md`
* application configuration

into the discipline root unless the existing project architecture explicitly requires that file there.

Never overwrite the discipline `README.md`.

Never move project source into `03-your-product`.

---

# Generated files

Do not commit generated files unless the project architecture explicitly requires them.

Before committing, inspect:

* build artifacts
* cache directories
* coverage output
* screenshots
* debug dumps
* generated logs
* temporary exports

Do not allow generated noise into the project repository.

---

# Environment and secrets

Use configuration according to `Architecture → Host`.

Do not:

* commit `.env` secrets
* hardcode credentials
* embed private API keys in client code
* expose server-only secrets through public configuration
* log sensitive environment values

When a new environment variable is required:

* document its name
* identify whether it is public or secret
* update the correct project configuration/documentation
* never record the actual secret value in discipline truth

---

# Testing during implementation

Add or update tests appropriate to the job.

Potential tests include:

* unit
* component
* integration
* API
* database
* workflow
* authorization
* accessibility
* visual regression
* end-to-end
* performance

Test behavior rather than implementation details whenever practical.

For critical workflows, cover relevant negative paths.

Do not inflate tests merely to increase coverage numbers.

---

# Negative-path implementation

Where applicable, implement and test:

* invalid input
* unauthorized access
* forbidden access
* missing resource
* duplicate request
* retry
* timeout
* dependency failure
* empty data
* server failure
* cancellation
* expiration
* partial completion
* concurrency conflict

Do not implement only the happy path when the recipe requires recovery or failure behavior.

---

# Observability implementation

When the job introduces meaningful runtime behavior, add appropriate:

* structured logs
* error reporting
* metrics
* traces
* relevant client telemetry
* operational context

Do not add noisy logging.

Do not log secrets or sensitive user data unnecessarily.

Observability must help diagnose the actual current-job behavior.

---

# SEO/performance/accessibility regression awareness

When shared frontend work changes:

* metadata
* rendering
* CSS
* components
* images
* fonts
* routing
* navigation

inspect relevant:

* SEO
* accessibility
* performance
* responsive behavior

Do not assume a shared change only affects the page being edited.

---

# Shared-code change rule

A shared component, token, hook, utility, API contract, schema, or infrastructure component may be changed during `/develop` only when:

1. the current job genuinely requires the change, and
2. the change remains within the job's reasonable blast radius, and
3. the affected existing behavior can be verified.

If a broader refactor is desirable but not required:

* do not perform it in the current job
* leave it for a dedicated job

---

# Blast-radius awareness

Before a significant change, identify affected:

* routes
* components
* workflows
* APIs
* consumers
* data
* tests
* integrations
* configuration
* deployment
* observability

For shared code, test representative existing consumers.

Do not assume a shared primitive is safe because the current page works.

---

# Implementation stopping rule

Stop implementation and update the appropriate truth/decision record when:

* expected behavior is materially undefined
* architecture is contradictory
* the current recipe conflicts with confirmed project truth
* required credentials/infrastructure are missing
* an external dependency's current behavior is unknown and materially affects correctness
* the requested change would require a new product decision
* the job would necessarily expand beyond its defined scope

Do not invent missing requirements to keep coding.

---

# Pre-green review

Before running the final checks:

1. Inspect the diff.
2. Confirm current-job scope.
3. Confirm no unrelated changes.
4. Confirm no debug artifacts.
5. Confirm no secrets.
6. Confirm no placeholder implementation.
7. Confirm no disabled checks.
8. Confirm no accidental configuration changes.
9. Confirm no unnecessary dependencies.
10. Confirm tests cover the implemented behavior.
11. Confirm the implementation still matches the selected persona(s).
12. Confirm required Verify items are testable.

---

# Green gate

Run the real commands from `03-your-product/architecture.md` inside the project folder:

* lint
* types/typecheck
* relevant tests
* production build

Run additional project-required checks when the architecture specifies them.

Do not substitute unrelated commands merely to create a green result.

Do not bypass failures by:

* disabling lint rules
* suppressing type errors
* weakening tests
* removing assertions
* hiding console errors
* adding arbitrary ignores
* changing configuration solely to conceal the problem

If any required check is red:

* do not push
* do not call the job green
* do not start the next job
* run `/debug`

---

# Final pre-deployment review

When all checks pass:

Inspect:

* `git status`
* relevant diff
* staged diff if staged
* current commit state
* branch
* repository remote

Confirm:

* only current-job changes remain
* no secret exists
* no generated junk exists
* no unrelated work is staged
* current recipe is satisfied
* selected personas are satisfied
* required verification items are testable

---

# Update project truth

Update `03-your-product/progress-tracker.md` with the current job's verified development state as required by the discipline.

Do not mark the job complete merely because the local build is green.

The job is not complete until production verification/release gates say so.

Preserve:

* current job
* current status
* blockers
* decisions
* next action

Do not overwrite unrelated progress information.

---

# Green → live workflow

When the job is green and project files changed:

Follow `05-slash-commands/live.md`.

That workflow must establish:

`current job`
→ `correct scope`
→ `green checks`
→ `release commit`
→ `remote`
→ `Vercel production deployment`
→ `production URL`

Do not use localhost as proof.

Do not report the job as shipped from `/develop`.

`/develop` implements the job.

`/verify` independently proves it.

`/ship` closes the release.

---

# Full-stack job sequencing

For full-stack projects:

* check the recipe `Layer` field
* if this is a frontend job, confirm the paired backend job is explicitly identified and comes next
* if this is a backend job, connect the implementation to its frontend `Pair`
* do not begin unrelated frontend/backend jobs
* do not silently implement both halves when only one job is currently active unless the current recipe explicitly requires that behavior

A full-stack pair must remain feature-scoped.

---

# Frontend Definition of visually done

A frontend job is not complete merely because:

* the route renders
* components exist
* tests pass
* build succeeds

The implementation must visibly satisfy the recipe's applicable:

* visual direction
* signature
* composition
* typography
* surfaces
* spacing
* motion
* states
* responsive behavior
* accessibility

Do not substitute technical validity for visual completion.

---

# Backend Definition of technically done

A backend job is not complete merely because:

* an endpoint exists
* a database query works
* the build passes

The implementation must satisfy the recipe's applicable:

* contract
* validation
* authentication
* authorization
* ownership
* tenant isolation
* data integrity
* failure behavior
* idempotency
* reliability
* observability

---

# Completion state

At the end of `/develop`, report:

* current job
* job Layer
* recipe
* files changed
* important implementation decisions
* tests/checks run
* green/red status
* deployment status
* production URL when live workflow has completed
* remaining risk
* exact next command

Do not report the next job as started.

Do not mark a job shipped before `/ship`.

---

# Stop

* Red build → `/debug`. Do not push.
* Red lint/typecheck/tests → `/debug`. Do not push.
* Red production build → `/debug`. Do not push.
* Missing product behavior → record one focused open question and stop.
* Architecture conflict → record the conflict and stop.
* Mixed scope → separate it or stop.
* Secret detected → stop and remove/rotate safely before any push.
* Missing required infrastructure/credentials → stop and record the blocker.
* Do not start the next job.
* Do not invent product behavior.
* Do not use localhost as proof.
* Do not create or modify unrelated features.
* Do not perform unrelated refactors.
* Do not bypass quality checks.
* Do not disable security controls to make the job pass.
