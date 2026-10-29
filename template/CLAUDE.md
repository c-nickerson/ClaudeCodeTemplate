# CLAUDE.md

Instructions for Claude Code in this project. Keep this file short and specific:
it is loaded into every session. Replace every `TODO` below, then delete this
paragraph.

## Project
TODO: One or two sentences — what this project is and who it's for.

## Tech stack
TODO: Language, framework, package manager, runtime versions.

## Commands
TODO: The exact commands to use. Claude will run these, so make them copy-paste ready.
- Install: `TODO`
- Run / dev: `TODO`
- Test: `TODO`
- Lint / format: `TODO`

## Folder structure
- `src/` — main code.
- `tests/` — automated tests; mirror the layout of `src/`.
- `docs/` — longer documentation: guides, design notes, decisions.
- `scripts/` — developer helper scripts (setup, build, release). Not app code.

Put new files in the folder that matches. If none fits, ask before creating a new top-level folder.

## Conventions
- Follow the existing style of the file you are editing.
- Keep changes small and focused on the task; don't refactor unrelated code.
- Add or update tests alongside code changes.
- Never commit secrets. Configuration that varies per machine goes in `.env`
  (git-ignored); document required variables in `.env.example`.

## Before finishing a task
1. Run the test and lint commands above and make sure they pass.
2. Update docs (README, this file) if behaviour, commands, or structure changed.
