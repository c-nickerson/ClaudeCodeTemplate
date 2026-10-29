# CLAUDE.md — ClaudeCodeTemplate (this repo)

This repo builds a reusable, drop-in Claude Code project template. It is a
learning project: we go one small step at a time and document each one.

## Layout
- `template/` — the payload copied into new projects. Everything in it must make
  sense in *any* new project. Keep it language-agnostic.
- `docs/learning-log.md` — journal of every step (What / Why / Alternatives / Next).
- Everything outside `template/` is about the template and is never copied.

## Rules
- **Every change gets a learning-log entry.** Add a new `## Step N — ...` section
  at the bottom of `docs/learning-log.md` in the same commit.
- **One step per commit.** Commit message starts with `Step N: ...`.
- **Scripts for this repo are written in Node.js** (plain `.mjs`, built-in modules
  only unless a dependency is clearly justified in the log). They live in
  `scripts/` at the repo root, not in `template/`.
- Keep `README.md`'s layout tree in sync when adding or moving files.
- Prefer small, explained changes over large ones — the goal is learning.

## Talking to the user
- Explain like I'm 5 (ELI5): short, plain words, no jargon.
- Keep replies brief. Don't over-explain; the details go in the learning log.
