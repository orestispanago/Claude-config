# Claude-config

Global Claude Code configuration, shared across all machines and OSes.

- `CLAUDE.md`: global preferences. Loaded through a one-line import in `~/.claude/CLAUDE.md`.
- `settings.json`: reference copy of `~/.claude/settings.json`. Copied by hand, so each OS can add its own entries.

Project-specific preferences live in each project's own `CLAUDE.md` or `.claude/rules/`, not here.

## Setup on Linux

1. Clone this repo in `~/Projects/`
2. Create `~/.claude/CLAUDE.md` containing only the import line:

```bash
mkdir -p ~/.claude
echo '@~/Projects/Claude-config/CLAUDE.md' > ~/.claude/CLAUDE.md
```

3. Copy `settings.json` (if `~/.claude/settings.json` already exists, merge by hand instead)
4. Start `claude` from **anywhere outside this repo** and run `/memory`: this repo's `CLAUDE.md` should be listed.

## Setup on Windows

`~/.claude` is `C:\Users\orestis\.claude`.

1. Clone this repo in `C:\Users\orestis\Projects`
2. Create `C:\Users\orestis\.claude\CLAUDE.md` containing only the import line:

```
@~/Projects/Claude-config/CLAUDE.md
```

3. Copy `settings.json` (if `C:\Users\orestis\.claude\settings.json` already exists, merge by hand instead)
4. Start `claude` from anywhere **outside this repo** and run `/memory`: this repo's `CLAUDE.md` should be listed. If it isn't, replace the import line in `C:\Users\orestis\.claude\CLAUDE.md` with the full path:

```
@C:/Users/orestis/Projects/Claude-config/CLAUDE.md
```
