# /debug

Run the permanent production debugging prompt.

# Read

- `05-slash-commands/debug-prompt.md`
- `05-slash-commands/live.md`
- the current recipe and relevant generated persona

# Do

- Follow `debug-prompt.md` exactly
- Use the user's error/log/live symptom as its incident input
- If the previous command in this session already ran lint, typecheck, tests, and production build with all passing, and the fix has not changed those files, skip re-running unchanged checks
- Continue until the green deploy is proven on Vercel or a real product decision blocks progress

# Never

- Generate a replacement debug prompt
- Push red work
- Treat localhost as proof
- Add a feature or start the next job
