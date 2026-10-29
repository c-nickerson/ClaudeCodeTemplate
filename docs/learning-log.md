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

---

## Step 2 — Add `CLAUDE.md` (two of them)

**Date:** 2026-10-29

### What
- `template/CLAUDE.md` — a language-agnostic starter with `TODO` placeholders for
  project summary, tech stack, commands, folder structure, plus a few universal
  conventions and a "before finishing a task" checklist.
- `CLAUDE.md` at the repo root — instructions for Claude Code when working on
  *this* repo: the `template/` vs. everything-else split, the learning-log rule,
  one step per commit, and **Node.js for our own scripts**.
- Updated the layout tree in `README.md`.

### Why
**What `CLAUDE.md` is:** Claude Code automatically reads `CLAUDE.md` from the
project root at the start of every session. It's the project's "memory" — the
place to tell Claude the things it can't reliably guess (commands, conventions,
where things go).

**Why two files:** they have different audiences.
- The *root* one shapes how Claude helps build this template. It means we don't
  have to repeat "log every step" or "use Node" in every conversation.
- The *template* one is what new projects start with.

Because `template/` is a subfolder, its `CLAUDE.md` doesn't take over while we
work here — Claude Code loads the root one at startup and only picks up
subfolder `CLAUDE.md` files when it works with files in that subfolder.

**Why language-agnostic:** we don't yet know which kinds of projects this will
be used for. Anything language-specific (npm vs. pip commands, for example) is
left as a `TODO` for each project to fill in. Language-specific variants can
come later.

**Why so short:** `CLAUDE.md` is loaded into context every session, so every
line costs tokens and competes for attention. Concrete, checkable instructions
("run the tests before finishing") work better than vague ones ("write good
code"). The placeholders push each project toward the things that matter most:
exact commands and folder purposes.

**Why Node.js for our scripts:** a decision (yours) recorded here so it's
explicit. Using built-in modules only means no `npm install` step — scripts
just run with `node`.

### Alternatives considered
- **A long, comprehensive `CLAUDE.md`** with style guides etc. Rejected: it
  bloats every session, and most of it would be language-specific anyway.
- **Using `/init`** (Claude Code's command that generates a `CLAUDE.md` by
  scanning a codebase). Great for an existing project, but a brand-new template
  has no code to scan. A new project can still run `/init` later to fill in the
  `TODO`s.
- **Leaving out the root `CLAUDE.md`.** Then Claude would only see the template
  one here, which describes a generic project, not this one.

### Next
Candidates for Step 3:
1. `.claude/settings.json` — shared project settings (e.g. permissions that let
   Claude run safe commands without asking every time).
2. A standard folder layout inside `template/` (`src/`, `tests/`, `docs/`, …),
   recorded in the template `CLAUDE.md`.
3. Housekeeping: `.gitignore`, `.env.example`, `.editorconfig` (the template
   `CLAUDE.md` already mentions `.env.example`).
4. A Node.js `scripts/new-project.mjs` that copies `template/` into a target
   folder.
