# /brief

Run the six create prompts in order.

The purpose of `/brief` is to prepare and synchronize the project's discipline files from the project idea/blueprint without prematurely implementing the application.

Do not create application code.

Do not create the project repository.

Do not create the project folder.

Do not bypass required confirmations.

---

# Read

Before running the create prompts, read:

* `01-start-here/AGENTS.md` and its required read order
* `01-start-here/HOW-TO-BUILD.md`
* all relevant files in `02-fill-these-prompts`
* current `03-your-product` files
* the project blueprint/project analysis already established for this project
* current `frontend-prompt.md` when frontend profile information is needed
* current `backend-prompt.md` when backend profile information is needed
* existing `03-your-product/progress-tracker.md`

Treat existing confirmed project truth as authoritative.

Do not regenerate already-confirmed information merely because `/brief` is being run again.

---

# Execution order

Run the six create prompts in exactly this order:

1. `02-fill-these-prompts/01-idea.md`
2. `02-fill-these-prompts/02-stack.md`
3. `02-fill-these-prompts/03-theme.md`
4. `02-fill-these-prompts/04-standards.md`
5. `02-fill-these-prompts/05-jobs.md`
6. `02-fill-these-prompts/06-personas.md`

Do not reorder them unless a referenced prompt explicitly requires a dependency-preserving adjustment.

The purpose of the order is:

`Project Understanding`
→ `Stack`
→ `Frontend Theme`
→ `Standards`
→ `Jobs`
→ `Selected Personas`

---

# 1. Idea

If `03-your-product/project-overview.md` still contains unresolved `[placeholders]`, run:

`02-fill-these-prompts/01-idea.md`

Use the established project blueprint as context.

Do not invent missing product requirements.

Do not silently convert assumptions into confirmed requirements.

If the project overview is already complete and confirmed, do not unnecessarily regenerate it.

---

# 2. Stack

Run:

`02-fill-these-prompts/02-stack.md`

Confirm backend names from:

`backend-prompt.md`

When stack information already exists and is confirmed:

* preserve it
* validate consistency
* do not replace it merely because a newer technology is available
* identify contradictions rather than silently overwriting decisions

Technology must remain consistent with the established project requirements and architecture.

---

# 3. Theme

Run:

`02-fill-these-prompts/03-theme.md`

Confirm frontend names from:

`frontend-prompt.md`

Preserve already-confirmed visual direction.

Do not silently replace:

* visual profile
* design direction
* signature
* typography strategy
* visual language

merely because another style is fashionable.

If the selected frontend profile conflicts with confirmed project requirements, identify the conflict rather than forcing the profile.

---

# 4. Standards

Run:

`02-fill-these-prompts/04-standards.md`

Ensure standards are consistent with:

* project requirements
* architecture
* selected frontend persona
* selected backend persona
* existing constraints

Do not invent standards merely to make the project appear more professional.

Do not add technology or quality requirements that materially change scope without a project justification.

---

# 5. Jobs

Run:

`02-fill-these-prompts/05-jobs.md`

Generate the implementation jobs from the established project understanding.

Jobs must be:

* feature-scoped
* ordered
* testable
* implementable
* consistent with project truth
* consistent with architecture
* consistent with selected frontend/backend disciplines

Do not create jobs for:

* speculative features
* unrelated cleanup
* arbitrary refactors
* unnecessary infrastructure
* future ideas that do not belong in the current plan

---

# Full-stack job ordering

For full-stack projects:

Order jobs feature by feature.

Use:

`Frontend Job`
→
`Backend Pair`

rather than:

`all frontend jobs`
→
`all backend jobs`

When appropriate, create explicit `Pair` relationships.

Each paired feature should allow the eventual implementation workflow to understand:

* which frontend job belongs with which backend job
* which side comes first
* what shared behavior must be verified
* what user-visible workflow the pair produces

Do not create artificial pairs where no real feature relationship exists.

---

# Job sequencing integrity

The generated build plan must not contain ambiguous sequencing.

Each job should make it clear:

* what it implements
* what it depends on
* what comes before it
* what comes after it
* what is out of scope
* how it will eventually be verified

Do not mark jobs complete during `/brief`.

Do not imply implementation has occurred.

---

# 6. Personas

Run:

`02-fill-these-prompts/06-personas.md`

Copy the **exact selected sections** into both generated persona files as required by the existing discipline.

Do not summarize selected persona sections.

Do not silently rewrite them.

Do not weaken selected requirements.

The generated persona files must remain the authoritative selected frontend/backend discipline used later by:

* `/architect`
* `/develop`
* `/debug`
* `/verify`
* `/audit`
* `/ship`

---

# Blueprint alignment

The project blueprint is upstream project context.

Use it to make sure the generated files agree on:

* project purpose
* scope
* users/actors
* capabilities
* workflows
* business rules
* architecture direction
* quality requirements
* risks
* constraints
* MVP boundaries
* major dependencies

Do not copy the entire blueprint into the generated files unless the existing create prompt specifically requires it.

Do not reproduce the blueprint's full heading structure.

The goal is alignment, not duplication.

---

# Existing truth preservation

Before changing an existing file, determine whether its information is:

* confirmed
* assumed
* unresolved
* obsolete
* contradictory

Preserve confirmed information unless the user explicitly changes it or verified project truth proves it stale.

Do not overwrite confirmed decisions with newly generated guesses.

Do not replace a project-specific decision with a generic default.

---

# Contradiction handling

If the create prompts encounter a contradiction between existing project truth and newly derived information:

1. identify the contradiction
2. determine whether one side is explicitly confirmed
3. preserve the confirmed side
4. identify the affected files
5. record the required decision/open question when necessary
6. stop when the contradiction materially blocks reliable generation

Do not silently choose a side merely to complete `/brief`.

---

# Confirmation gates

Do not skip:

* stack confirmation
* theme confirmation
* any other confirmation explicitly required by the create prompts

Do not infer user approval from silence.

Do not treat an existing choice as permission to make unrelated new choices.

When a create prompt requires user confirmation, stop at that point until the existing workflow permits continuation.

---

# Idempotency

Running `/brief` again must not unnecessarily regenerate or destabilize project truth.

When the relevant files already contain complete, confirmed information:

* preserve their content
* validate consistency
* make only necessary corrections
* do not create duplicate sections
* do not duplicate jobs
* do not create duplicate personas
* do not reset confirmed selections

A second `/brief` should converge toward the same project model rather than continuously rewriting it.

---

# Progress tracker

Update:

`03-your-product/progress-tracker.md`

to:

`Files are ready`

only after the six required creation steps have actually completed and the resulting files are internally coherent.

The tracker must accurately reflect what has happened.

Do not set:

`Files are ready`

if:

* required confirmation is pending
* a required create prompt failed
* personas were not generated
* jobs were not generated
* critical contradictions remain unresolved
* required project truth is missing

---

# Files-ready gate

When all required creation work is complete:

Tell the user the next step is:

**Files are ready**

The user should then:

1. create `{project-name}/`
2. create the GitHub repository for that project folder only

Do not perform those actions during `/brief`.

---

# Repository separation

The discipline repository and future project repository are separate.

`/brief` must not:

* create the GitHub project repository
* initialize the application Git repository
* push application code
* create the Vercel project
* create the project folder
* place application source in the discipline root

Never overwrite the discipline `README.md`.

---

# Scope rule

`/brief` is a project-definition preparation command.

It may update the relevant discipline files required by its six create prompts.

It must not:

* write application source
* install project dependencies
* create framework code
* create project infrastructure
* deploy
* create repositories
* implement features
* start `/architect`
* start `/develop`

---

# Quality gate

Before declaring `/brief` complete, verify:

### Project

* project overview is coherent
* project blueprint and overview do not materially contradict each other

### Stack

* selected backend direction is confirmed
* stack information is coherent with architecture

### Theme

* selected frontend direction is confirmed
* selected theme aligns with project requirements

### Standards

* standards are present and coherent
* no unnecessary scope was introduced

### Jobs

* jobs are feature-scoped
* jobs have sensible ordering
* full-stack pairs are correctly related
* jobs do not invent functionality

### Personas

* required selected sections were copied exactly
* frontend/backend generated personas are available
* no selected requirements were silently weakened

### Progress

* progress tracker accurately states the current preparation state
* `Files are ready` is not claimed prematurely

---

# If information is missing

Use the existing create-prompt behavior.

Do not invent missing information.

If the missing information is non-blocking:

* preserve the established assumption mechanism
* label the assumption appropriately
* continue

If the missing information is blocking:

* ask the required question
* record the blocker where the discipline requires it
* stop the affected step

Do not force completion through fabricated information.

---

# Stop

* Do not create a GitHub repo
* Do not create the project folder yet
* Do not write app code
* Do not deploy
* Do not skip stack confirmation
* Do not skip theme confirmation
* Do not skip any required create prompt
* Do not summarize selected persona sections instead of copying the exact selected sections
* Do not invent product requirements
* Do not silently overwrite confirmed decisions
* Do not create duplicate jobs/personas
* Do not create a repository
* Do not start `/architect`
* Do not start `/develop`
* Do not overwrite the discipline `README.md`

---

# Completion report

Report:

* create prompts completed
* any required confirmations completed/pending
* generated/updated project truth files
* selected frontend/backend directions
* jobs created or preserved
* full-stack pairs when applicable
* persona generation status
* contradictions or blockers
* progress-tracker state
* next step: **Files are ready**

Do not report the application as built.

Do not report the project repository as created.

Do not report deployment.

`/brief` ends when the project's discipline files are ready for the next command.
