# Project Memory

> Claude updates this file when wrapping up a session. It's a snapshot of the
> project *now* — replace outdated info rather than adding to it.

**Last updated:** 2026-10-29

## Overview
A learning project to build a reusable Claude Code project template: copy
`template/` into a new project and it starts with a standard layout, conventions
and Claude Code setup.

## Goals
- A drag-and-drop template with standard folders and files.
- Learn how Claude Code projects are best set up, one step at a time.
- Document WHAT we did and WHY (`docs/learning-log.md`).

## Requirements
- Template stays language-agnostic.
- Copying is manual: `cp -r template/. /path/to/new-project/` (no copy script).
- Scripts for this repo, if ever needed, are Node.js.
- `CLAUDE.md` = rules (edited only when the user asks).
  `.claude/memory/PROJECT.md` = project facts and progress (updated by Claude at wrap-up).
- Replies to the user are short and ELI5.

## Tech stack
Markdown and JSON config files. Node.js for any helper scripts.

## Commands
- Use the template: `cp -r template/. /path/to/new-project/`
- Check a JSON file is valid: `node -e 'JSON.parse(require("fs").readFileSync("<file>","utf8"))'`

## Plan
Status: ✅ done · 🔄 in progress · ⬜ not started

### Phase 1 — Template basics ✅
- ✅ Step 1: Split `template/` from the learning docs
- ✅ Step 2: `CLAUDE.md` files (repo + template)
- ✅ Step 3: Standard folders (`src/`, `tests/`, `docs/`, `scripts/`)
- ✅ Step 4: `.gitignore`, `.env.example`, `.editorconfig`
- ✅ Step 5: `.claude/settings.json` permissions

### Phase 2 — Claude Code setup 🔄
- ✅ Step 6: Claude setup for this repo
- ✅ Step 7: Split rules (`CLAUDE.md`) from memory (`.claude/memory/PROJECT.md`)
- ⬜ Custom slash commands (e.g. `/wrap-up`)
- ⬜ Hooks

## Current focus / Next up
- Pick next: custom slash commands or hooks.

## Decisions
- `template/` holds the payload so learning docs never get copied.
- Template is language-agnostic; language specifics go in each project's `PROJECT.md`.
- No copy script — one `cp` command is enough.
- `CLAUDE.md` is the stable rulebook; `PROJECT.md` is the living memory, loaded via `@` import.

## Open questions
- None right now.
