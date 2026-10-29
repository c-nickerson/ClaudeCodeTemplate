# CLAUDE.md — ClaudeCodeTemplate (this repo)

This repo builds a reusable, drop-in Claude Code project template. It is a
learning project: we go one small step at a time and document each one.

## Layout
- `template/` — the payload copied into new projects. Everything in it must make
  sense in *any* new project. Keep it language-agnostic.
- `docs/learning-log.md` — journal of every step (What / Why / Alternatives / Next).
- `.claude/` and this `CLAUDE.md` — Claude Code setup for working on *this* repo.
  Don't confuse them with `template/.claude/` and `template/CLAUDE.md`, which are
  part of the template.
- Everything outside `template/` is about the template and is never copied.

## How a step works
1. Agree the step with the user before changing files.
2. Make the change (small and focused).
3. Update the `README.md` layout tree if files were added or moved.
4. Add a `## Step N — ...` entry at the bottom of `docs/learning-log.md`
   (What / Why / Alternatives considered / Next).
5. Commit everything in one commit: `Step N: ...`. Push.
6. Reply to the user with a short ELI5 summary and suggest the next step.

## Rules
- **Scripts for this repo are written in Node.js** (plain `.mjs`, built-in modules
  only unless a dependency is clearly justified in the log). They live in
  `scripts/` at the repo root, not in `template/`. Only add a script when the user
  asks for one.
- Copying the template is done by hand: `cp -r template/. /path/to/new-project/`.
- Prefer small, explained changes over large ones — the goal is learning.

## Talking to the user
- Explain like I'm 5 (ELI5): short, plain words, no jargon.
- Keep replies brief. Don't over-explain; the details go in the learning log.
