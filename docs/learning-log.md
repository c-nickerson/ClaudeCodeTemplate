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

---

## Step 2.5 — Set how Claude talks to us

**Date:** 2026-10-29

### What
Added a "Talking to the user" section to the root `CLAUDE.md`: ELI5, short replies.

### Why
Chat should be quick to read. The full reasoning lives here in the log instead.
Putting it in `CLAUDE.md` means every future session follows it automatically.

---

## Step 3 — Standard folder layout

**Date:** 2026-10-29

### What
Added four folders to `template/`, each with a short `README.md`:

- `src/` — main code
- `tests/` — automated tests (mirror `src/`)
- `docs/` — longer documentation
- `scripts/` — developer helper scripts

Filled in the "Folder structure" section of `template/CLAUDE.md` and updated the
tree in the root `README.md`.

### Why
- **Same layout every time** — you (and Claude) always know where things go.
- **These four names are near-universal.** They work for almost any language, so
  the template stays language-agnostic.
- **A `README.md` in each folder** because Git doesn't save empty folders. A README
  keeps the folder *and* says what it's for. (Plain `.gitkeep` files would keep the
  folder but explain nothing.)
- **Listed in `CLAUDE.md`** so Claude puts new files in the right place. The "ask
  before creating a new top-level folder" rule stops the layout from drifting.

### Alternatives considered
- **More folders** (`config/`, `assets/`, `examples/`, …). Left out: not every
  project needs them, and empty folders are clutter. Easy to add per project.
- **Language-specific layouts** (e.g. Python's `src/<package>/`). Too specific for
  now; could become variants later.

### Next
Housekeeping files (`.gitignore`, `.env.example`, `.editorconfig`), or
`.claude/settings.json`.

---

## Step 4 — Housekeeping files

**Date:** 2026-10-29

### What
Added three hidden files to `template/`:

- `.gitignore` — files Git should never track.
- `.env.example` — a list of the settings/secrets a project needs, with no real values.
- `.editorconfig` — basic formatting rules (indent, line endings) that most editors follow.

Also updated the root `README.md` tree and noted that `cp -r template/.` is needed
to copy hidden files.

### Why
- **`.gitignore`** stops secrets (`.env`) and junk (OS files, logs, build output,
  dependency folders) from being committed. It also ignores
  `.claude/settings.local.json` — Claude Code's *personal* settings file — while
  keeping the shared `.claude/settings.json` tracked. That sets up the next step.
- **`.env.example`** pairs with the ignored `.env`: the real secrets stay local, but
  everyone can see *which* settings are needed. `CLAUDE.md` already tells Claude to
  keep it up to date.
- **`.editorconfig`** prevents noisy diffs from mixed tabs/spaces or Windows vs. Unix
  line endings. It's language-agnostic and supported by most editors.

### Alternatives considered
- **A big language-specific `.gitignore`** (e.g. from github/gitignore). Too much for
  a generic template. We kept a few very common entries (`node_modules/`, `.venv/`,
  `dist/`…) because they're harmless when unused.
- **`.gitattributes`** for line endings. Overlaps with `.editorconfig`; skipped to
  stay simple.
- **Formatter configs (Prettier, Black…).** Language-specific — left to each project.

### Next
`.claude/settings.json` — shared Claude Code settings (permissions).
