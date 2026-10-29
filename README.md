# Claude Code Template

A learning project to build a reusable **Claude Code project template**: a set of
folders and files you can drop into a new project so that every project starts
with the same layout, conventions, and Claude Code configuration.

We are building it **one step at a time**, and recording **what** we did and
**why** in [`docs/learning-log.md`](docs/learning-log.md).

## Repository layout

```
ClaudeCodeTemplate/
├── README.md            # This file: what the project is and how it's organised
├── CLAUDE.md            # Rulebook for Claude in THIS repo (rarely edited)
├── .claude/
│   ├── settings.json    # Claude Code permissions for THIS repo
│   └── memory/
│       └── PROJECT.md   # Living memory: goals, plan, progress (Claude updates it)
├── .gitignore           # Files Git ignores in THIS repo
├── docs/
│   └── learning-log.md  # Step-by-step journal: WHAT we did and WHY
└── template/            # The drop-in payload: copy its contents into a new project
    ├── .claude/
    │   ├── settings.json  # Shared Claude Code settings: what Claude may/can't do
    │   └── memory/
    │       └── PROJECT.md # Fill-in memory: goals, plan, progress
    ├── .gitignore       # Files Git should ignore (secrets, clutter, builds)
    ├── .env.example     # List of settings/secrets the project needs (no real values)
    ├── .editorconfig    # Shared basic formatting rules for all editors
    ├── CLAUDE.md        # Rulebook: how Claude works (rarely edited)
    ├── README.md
    ├── src/             # Main code
    ├── tests/           # Automated tests
    ├── docs/            # Longer documentation
    └── scripts/         # Developer helper scripts
```

The key split is:

| Folder      | Purpose                                   | Copied into new projects? |
|-------------|-------------------------------------------|---------------------------|
| `template/` | The actual template                       | **Yes**                   |
| everything else | Notes, history, and reasoning about the template | No              |

## Using the template

1. Copy the template into your new project:

```bash
cp -r template/. /path/to/new-project/
```

   The `/.` matters: it copies hidden files (names starting with `.`) too.
2. Fill in `.claude/memory/PROJECT.md` (or ask Claude to help you).
3. Leave `CLAUDE.md` alone unless you want to change how Claude works.

## Two kinds of Claude files

| File | What it is | Who changes it | How often |
|---|---|---|---|
| `CLAUDE.md` | Rulebook: *how* Claude works | You (or Claude, only when you ask) | Rarely |
| `.claude/memory/PROJECT.md` | Memory: *what* the project is and where it's at | Claude, when wrapping up | Every session |
