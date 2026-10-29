# Learning Log

A running journal of how this template was built. Each step records:

- **What** — the change we made
- **Why** — the reasoning behind it
- **Alternatives considered** — what we chose *not* to do, and why
- **Next** — what the step sets up

Newest steps go at the bottom so the log reads like a story.

---

## Step 1 — Separate the template from the project about the template

**Date:** 2026-10-29

### What
Created the repository skeleton:

- `README.md` — explains the project and its layout.
- `docs/learning-log.md` — this file.
- `template/` — the folder whose contents get copied into new projects
  (currently just a placeholder `README.md`).

### Why
This repo has two jobs at once:

1. **Be** the template.
2. **Explain** how and why the template was built.

If those were mixed together at the root, then "drag and drop into a new project"
would also drag in this learning log, notes, and experiments — clutter that every
new project would have to delete. Putting the payload in its own `template/`
folder makes the copy step trivial and unambiguous: *copy `template/`, nothing
else.*

A learning log (rather than only commit messages) was chosen because commit
messages explain *a change*, while the log explains *the journey* — it's easier to
read top to bottom when revisiting the reasoning later.

### Alternatives considered
- **Template at the repo root** (use the repo itself as the template, e.g. via
  GitHub's "Use this template" button). Simpler, but the learning docs would leak
  into every new project. We can still revisit this later once the template is
  stable.
- **Two separate repos** (one for the template, one for notes). Cleaner
  separation, but more overhead for a learning project and the history of *why*
  would be split from *what*.

### Next
Decide what goes inside `template/` first. Likely candidates, roughly in order:

1. `CLAUDE.md` — the instructions file Claude Code reads automatically at the
   start of every session. This is the heart of a Claude Code template.
2. `.claude/` — project-level Claude Code settings (permissions, hooks, custom
   commands, agents).
3. Standard folder layout (`src/`, `tests/`, `docs/`, …).
4. Housekeeping files (`.gitignore`, `.editorconfig`, …).
