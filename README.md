# Claude-config

Global Claude Code configuration, shared across all machines and OSes.

- `CLAUDE.md`: global preferences. Loaded through a one-line import in `~/.claude/CLAUDE.md`.

Settings are not synced; set them by hand on each machine (step 3).

Project-specific preferences live in each project's own `CLAUDE.md` or `.claude/rules/`, not here.

## Setup on Linux

1. Clone this repo in `~/Projects/`
2. Create `~/.claude/CLAUDE.md` containing only the import line:

```bash
mkdir -p ~/.claude
echo '@~/Projects/Claude-config/CLAUDE.md' > ~/.claude/CLAUDE.md
```

3. Set by hand: allow WebSearch (choose "don't ask again" the first time Claude searches), theme and push notifications (`/config`).
4. Start `claude` from **anywhere outside this repo** and run `/memory`: this repo's `CLAUDE.md` should be listed.

## Setup on Windows

`~/.claude` is `C:\Users\orestis\.claude`.

1. Clone this repo in `C:\Users\orestis\Projects`
2. Create `C:\Users\orestis\.claude\CLAUDE.md` containing only the import line:

```
@~/Projects/Claude-config/CLAUDE.md
```

3. Set by hand: allow WebSearch (choose "don't ask again" the first time Claude searches), theme and push notifications (`/config`).
4. Start `claude` from anywhere **outside this repo** and run `/memory`: this repo's `CLAUDE.md` should be listed. If it isn't, replace the import line in `C:\Users\orestis\.claude\CLAUDE.md` with the full path:

```
@C:/Users/orestis/Projects/Claude-config/CLAUDE.md
```
