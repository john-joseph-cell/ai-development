# Prompt: theme

Use this after the Project Blueprint / Discovery stage and after:

* `03-your-product/project-overview.md`
* `03-your-product/architecture.md`

are real.

# You replace

`03-your-product/ui-context.md`

# You read

* the confirmed Project Blueprint from the discovery conversation
* `03-your-product/project-overview.md`
* `03-your-product/architecture.md`
* `04-always-on-rules/frontend-prompt.md` — the only frontend prompt source

# Blueprint dependency

The visual system is downstream of product understanding.

Use the Project Blueprint and confirmed product truth to understand:

* who uses the product
* what those users are trying to accomplish
* what information matters
* what workflows are important
* which actions are primary
* which states need strong visibility
* which content needs emphasis
* which permissions affect what users see
* which contexts are operational, transactional, editorial, analytical, or promotional
* which devices and input methods matter
* which accessibility requirements matter
* which performance constraints matter
* which visual limitations or product constraints exist

Do not let visual style redefine product behavior.

Do not introduce product features merely because they fit a visual pattern.

Do not create visual complexity that harms an important workflow.

# Design decision principle

Choose the visual language that best communicates the confirmed product's:

* purpose
* hierarchy
* trust requirements
* user goals
* information density
* interaction model
* brand character
* operational context

Do not choose a style merely because it is fashionable.

Do not force every project into the same visual direction.

# You ask (names only, then stop)

Recommend from the Recommendation law in `frontend-prompt.md`.

Ask only:

* Visual: Google | Awwwards | Apple | Dribbble | E-commerce | SaaS | Linear | Vercel | Stripe | Shopify | Master
* Motion: Apple | Stripe | Awwwards | Linear
* Product UX: Raycast | Tabular | E-commerce CRO | SaaS dashboard | Shopify store
* Engineering: Production AA

Mark one recommendation per group and give one short reason.

The recommendation must be based on:

* Project Blueprint
* `project-overview.md`
* `architecture.md`
* actual product workflows
* actual information density
* actual device requirements
* actual user needs

Do not choose a visual level independently of the product.

# Visual recommendation rules

When recommending a visual direction, evaluate:

### Product context

Does the product require:

* trust
* speed
* calmness
* operational density
* storytelling
* conversion
* technical credibility
* creative expression
* discoverability
* data clarity

### Workflow context

Does the user spend most of the time:

* reading
* creating
* editing
* comparing
* searching
* purchasing
* monitoring
* managing
* navigating
* configuring
* approving
* reviewing

### Information density

Determine whether the product needs:

* spacious editorial composition
* medium-density product UI
* dense operational workspace
* commerce-oriented discovery
* analytical/data-heavy presentation

Do not use an immersive/cinematic direction for a dense operational workflow merely because it looks impressive.

### Device and interaction context

Consider:

* desktop
* tablet
* mobile
* touch
* keyboard
* screen reader
* browser zoom
* reduced motion

The visual choice must remain usable across the actual supported environments.

# Motion recommendation rules

Motion must come from the product's actual interaction model.

Choose motion according to whether the project benefits from:

* state communication
* spatial continuity
* navigation
* storytelling
* product demonstration
* data changes
* operational feedback
* touch interaction

Do not add cinematic motion to workflows where speed and clarity are more important.

Do not add motion merely because the selected visual direction permits it.

# Product UX recommendation rules

Choose the Product UX direction according to actual information architecture and workflow needs.

For example:

* command-heavy tools may justify Raycast
* data-heavy systems may justify Tabular
* shopping flows may justify E-commerce CRO
* repeat-use SaaS may justify SaaS dashboard
* merchant/admin + storefront systems may justify Shopify store

Do not select a Product UX persona merely because the project belongs to a similar industry.

# Engineering rule

Use:

* Production AA

Production accessibility is part of the project quality baseline.

Do not weaken it merely to make a visual effect easier to implement.

# Confirmation gate

Do not generate `ui-context.md` before the user confirms the recommended selections.

Do not treat:

* silence
* unrelated messages
* requesting more detail
* asking for code
* asking for implementation

as confirmation.

Wait for explicit confirmation of the selections.

# You write

After confirmation, replace:

`03-your-product/ui-context.md`

Write plain markdown.

No extra commentary.

Use exactly these headings:

* `# UI Context`
* `## Selected prompts`
* `## Theme`
* `## Signature`
* `## Colors`
* `## Typography`
* `## Spacing and radius`
* `## Surfaces and borders`
* `## Layout and breakpoints`
* `## Components and icons`
* `## Motion`
* `## Data, tables, and pagination`
* `## States`
* `## Accessibility and performance`
* `## Anti-patterns`

# Selected prompts

Use the exact confirmed names.

Do not rename them.

Do not merge multiple visual personas.

Do not add an unconfirmed visual direction.

# Theme

Apply the selected visual prompt specifically to the actual product.

The theme must reflect:

* product purpose
* user context
* important workflows
* information hierarchy
* confirmed architecture
* device requirements
* accessibility requirements
* performance requirements

Do not produce a generic description of the chosen visual style.

# Signature

Define:

* Visual thesis: one sentence describing the project's visual/compositional identity
* Memorable element: one meaningful visual or interaction element that belongs specifically to this product

The signature must emerge from the product.

Do not add a decorative signature with no product purpose.

Do not create multiple competing signatures.

# Colors

Define semantic CSS variables and values appropriate to the product.

Colors must support:

* hierarchy
* state communication
* readability
* accessibility
* selected art direction
* important workflows

Do not choose colors merely because they belong to the selected persona.

Do not hardcode component-specific colors here.

# Typography

Define:

* display
* body
* label
* metadata
* numeric roles

Typography must account for:

* actual content
* information density
* long text
* numbers
* tables
* localization where relevant
* responsive behavior
* accessibility

Do not define typography around placeholder content.

# Spacing and radius

Define a coherent spacing and radius system.

Consider:

* content density
* touch interaction
* operational workflows
* responsive recomposition
* component relationships

Do not introduce arbitrary page-specific spacing rules.

# Surfaces and borders

Define the product's:

* base
* canvas
* elevated
* overlay
* borders
* shadows/elevation
* functional depth

Use surfaces to communicate hierarchy and interaction, not decoration alone.

# Layout and breakpoints

Define:

* shell behavior
* content width
* grid behavior
* page composition
* mobile
* tablet
* desktop
* wide

Breakpoints must derive from content and interaction constraints.

Mobile must be intentionally recomposed.

Do not simply compress the desktop layout.

# Components and icons

Define:

* component library
* primitive behavior
* icon system
* icon sizing
* reusable state patterns
* hierarchy of controls

Only define components justified by the product.

Do not create generic component collections disconnected from actual workflows.

# Motion

Define:

* timings
* curves/springs
* route behavior
* reduced-motion behavior

Motion must correspond to confirmed product behavior.

Where appropriate, define motion for:

* state transitions
* navigation
* expansion
* creation
* deletion
* loading
* synchronization
* feedback
* product storytelling

Do not create motion for every element.

# Data, tables, and pagination

Define applicable behavior based on the actual product and selected Product UX prompt.

Consider:

* sorting
* filtering
* search
* pagination
* page size
* row actions
* selection
* bulk actions
* mobile behavior
* large data sets
* loading
* empty
* error
* no-results
* permission states

Only include applicable behavior.

# States

Define all relevant product states.

At minimum, consider:

* default
* hover
* focus-visible
* active
* selected
* loading
* disabled
* success
* error

For data-driven surfaces, consider:

* first use
* populated
* empty
* no-results
* permission denied
* recoverable error
* offline/stale
* partial failure
* partial completion

For destructive or consequential actions, consider:

* confirmation
* cancellation
* recovery

Every state must correspond to actual product behavior established by the Blueprint.

# Accessibility and performance

Preserve:

* Production AA
* keyboard access
* focus behavior
* semantic structure
* contrast
* reduced motion
* touch usability
* responsive behavior
* layout stability
* efficient assets
* appropriate loading behavior
* performance requirements from the selected frontend prompt

Do not sacrifice core workflow usability for visual effects.

# Anti-patterns

Create project-specific prohibitions derived from:

* the Blueprint
* `project-overview.md`
* `architecture.md`
* selected frontend prompts

Include only meaningful prohibitions.

Examples may include:

* generic card-grid layouts where inappropriate
* decorative components with no product purpose
* fake functionality
* fake data
* invented metrics
* excessive motion
* inaccessible interactions
* desktop layouts compressed into mobile
* visual treatments that interfere with critical workflows

# Rules

* Derive every decision from the confirmed Project Blueprint, product overview, architecture, and exact selected sections in `frontend-prompt.md`.
* Use semantic tokens.
* Components do not invent local visual values.
* Match the confirmed stack in `architecture.md`.
* Production AA remains selected unless the user waives it in writing.
* Do not invent content.
* Do not invent features.
* Do not invent statistics.
* Do not invent media.
* Do not invent routes.
* Do not invent user roles.
* Do not invent product workflows.
* Do not add decorative widgets without product purpose.
* Do not create fake functionality.
* Do not produce generic card-grid layouts merely because they are common.
* Preserve the Universal foundation from the frontend rules.
* Respect the actual product's information architecture.
* Ensure mobile behavior is defined.
* Ensure keyboard interaction and focus behavior are defined.
* Ensure reduced-motion behavior is defined.
* Ensure states are explicitly designed.
* Ensure all UI decisions are implementable with the confirmed stack.
* Do not allow visual decisions to redefine product scope.
* Do not allow visual decisions to contradict product workflows.
* Do not introduce an architectural decision through UI design.
* Do not turn future ideas into current UI.
* Do not create design complexity without a product reason.
* Do not generate frontend code.
* Do not generate backend code.
* Do not generate build jobs.

# Final validation

Before outputting `ui-context.md`, verify internally:

* the selected visual direction fits the product purpose
* the selected motion direction fits the actual workflows
* the selected Product UX direction fits the information architecture
* the Blueprint's user needs are represented
* important workflows have appropriate visual treatment
* important states are represented
* responsive behavior is defined
* accessibility requirements are represented
* performance requirements are represented
* the architecture is respected
* no feature has been invented
* no product behavior has been changed through design
* no unsupported technology has been introduced
* no contradiction exists with `project-overview.md`
* no contradiction exists with `architecture.md`
* no contradiction exists with the confirmed Project Blueprint
* no placeholder remains

Then generate only:

`03-your-product/ui-context.md`

Stop.
