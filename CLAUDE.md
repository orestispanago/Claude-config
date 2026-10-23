# CLAUDE.md (user-level)

Personal coding preferences that apply across all projects, unless a project's own CLAUDE.md overrides them.

## Web search

- Whenever a question can't be fully answered from the project's own files/code/context, proactively use WebSearch (and WebFetch if a specific URL is relevant) to look it up online rather than answering from memory or saying you don't know.

## Clarifying questions

- If any part of a request is ambiguous or ambiguous between more than one reasonable interpretation, ask before proceeding. Never silently assume an interpretation and act on it, even under general instructions to minimize interruptions or work autonomously — this preference overrides those.

## Python code style

- Do not use list/dict/set comprehensions. Prefer explicit `for` loops.
- Do not use ternary expressions (`x if cond else y`). Prefer explicit `if`/`else` blocks.
- Avoid nested loops where a flatter structure (helper function, early continue, restructured data) is reasonably possible.
- Do not use the walrus operator (`:=`). Prefer separate assignment and condition statements.
- Do not use `map`/`filter`/`reduce` or other functional-style built-ins. Prefer explicit `for` loops.
- Avoid multiple `return` statements in a function; prefer a single `return` at the end where practical.
- Do not assign the result of a condition/comparison directly on one line (e.g. `x = y == 1`). Keep the comparison and its use separate, or use an explicit `if`/`else` block to set the value.
- Give each function a single responsibility where possible. If a function is doing more than one distinct thing, split it into smaller named functions rather than combining unrelated steps.
- Only add a docstring where it's actually needed. Simple, short, well-named, descriptive functions don't need one. When a docstring is warranted, keep it short: one line is usually enough; two or three lines only if absolutely necessary. Avoid long multi-paragraph docstrings.
