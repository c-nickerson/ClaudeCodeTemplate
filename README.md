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
├── CLAUDE.md            # Instructions for Claude Code when working on THIS repo
├── docs/
│   └── learning-log.md  # Step-by-step journal: WHAT we did and WHY
└── template/            # The drop-in payload: copy its contents into a new project
    ├── CLAUDE.md        # Starter instructions for Claude Code in a new project
    └── README.md
```

The key split is:

| Folder      | Purpose                                   | Copied into new projects? |
|-------------|-------------------------------------------|---------------------------|
| `template/` | The actual template                       | **Yes**                   |
| everything else | Notes, history, and reasoning about the template | No              |

## Using the template

Not ready yet. Once it is, the usage will be roughly:

```bash
cp -r template/. /path/to/new-project/
```
