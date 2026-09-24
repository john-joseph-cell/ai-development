# /audit

Run the permanent architecture and product-truth audit prompt.

# Read

- `05-slash-commands/audit-prompt.md`
- `05-slash-commands/live.md`
- all `03-your-product` files
- project repository and generated persona(s)

# Do

- Follow `audit-prompt.md` exactly
- If the previous command in this session already ran lint, typecheck, tests, and production build with all passing, and no source files changed since, skip re-running those checks
- Update only verified truth drift in `03-your-product`
- Report evidence-backed findings and the correct next command

# Never

- Generate a replacement audit prompt
- Hide a defect by weakening a recipe
- Write feature/fix code
- Treat a green build as a clean audit
- Treat localhost as proof
