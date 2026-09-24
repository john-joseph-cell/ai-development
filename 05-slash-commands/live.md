# Live check

Proof is the Vercel production URL. Never localhost. Never `npm run dev` as evidence.

# Need

From `03-your-product/architecture.md` under Host:

- GitHub repo URL
- Vercel production URL (Project URL)

If either is missing, stop and ask the user once. Write the answers into Host. Then continue.

Work only in the project folder named under Host → Project folder.

# Push

Follow this exact sequence. No exceptions.

1. `git pull origin main` — sync before pushing
2. `git status` — confirm what changed
3. `git add <specific-files>` or `git add -u` — stage explicitly, never blind `git add .`
4. `git commit -m "feat: precise imperative message"` — commit with intent
5. `git pull origin main` — safety pull before push
6. `git push origin main` — push clean history

- Never `git push --force`
- Never leave uncommitted changes while pulling. Commit or `git stash` first
- Never commit secrets, `.env` files, or debug artifacts
- Do not create an empty commit or push when no project file changed

If the previous command in this session already committed, pushed, and confirmed the Vercel deploy, the next command does not repeat those steps.

# After /develop, /debug, /verify, /audit, /ship

Open the Vercel URL. Cite that URL. Localhost is not pass.

`/verify`, `/audit`, and `/ship` use their permanent `*-prompt.md` files. They must not generate weaker replacement prompts.

`/brief` and `/architect` do not push app code. `/ship` never creates a GitHub repo.
