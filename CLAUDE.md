# CLAUDE.md (user-level)

Personal coding preferences that apply across all projects, unless a project's own CLAUDE.md overrides them.

## Web search

- Whenever a question can't be fully answered from the project's own files/code/context, proactively use WebSearch (and WebFetch if a specific URL is relevant) to look it up online rather than answering from memory or saying you don't know.

## Clarifying questions

- If any part of a request is unclear or has more than one reasonable interpretation, ask what I mean in simple language before proceeding. Never assume an interpretation and act on it, even under general instructions to minimize interruptions or work autonomously — this preference overrides those.
- When a decision is needed, describe the options in text, in simple language, with pros and cons for each.

## Python code style

- Do not use list/dict/set comprehensions. Prefer explicit `for` loops.
- Do not use ternary expressions (`x if cond else y`). Prefer explicit `if`/`else` blocks.
- Avoid nested loops where a flatter structure (helper function, early continue, restructured data) is reasonably possible.
- Do not use the walrus operator (`:=`). Prefer separate assignment and condition statements.
- Do not use `map`/`filter`/`reduce` or other functional-style built-ins. Prefer explicit `for` loops.
- Return one value from a function; several only if necessary and of the same kind (two dataframes, not a list and a dataframe). Early returns are fine; if a function returns a value anywhere, write `return None` explicitly rather than a bare `return`.
- Short check functions (return True/False from one condition or a try/except) return the result directly, e.g. `return a and b`, instead of setting a variable.
- Do not assign the result of a condition/comparison directly on one line (e.g. `x = y == 1`). Keep the comparison and its use separate, or use an explicit `if`/`else` block to set the value.
- Make only the code changes I list, in the simplest form. No extra refactors, helpers, retries or safeguards; offer extras in the chat instead.
- Start function names with a verb in most cases (`get_`, `read_`, `parse_`, `check_`).
- Fail fast: don't write code for errors not yet seen. Let the error happen, then handle it.
- Give each function a single responsibility where possible. If a function is doing more than one distinct thing, split it into smaller named functions rather than combining unrelated steps.
- Only add a docstring where it's actually needed. Simple, short, well-named, descriptive functions don't need one. When a docstring is warranted, keep it short: one line is usually enough; two or three lines only if absolutely necessary. Avoid long multi-paragraph docstrings.

## Git commit messages

- I make the commits myself. Propose a message when asked; don't commit. No `Co-Authored-By` line.
- One subject line, no body.
- Past tense verbs: Added, Created, Removed, Moved, Fixed, Renamed, Updated, Refactored.
- Join several changes with commas, lowercase after each comma, e.g. `Added sync button, removed flash message, made charts shorter`.
- Keep it short: name the main changes only and skip minor follow-ups. Several files under one verb are fine, e.g. `Created read_solar(), added requirements.txt, CLAUDE.md, updated SPEC.md`.
- No conventional-commit prefixes (`feat:`, `fix:`) and no trailing period. An optional topic prefix is fine, e.g. `Regions-comparison: Added Mann-Whitney test`.
- Be concrete: name the files, functions or variables involved. Write functions with `()`.

## Regression reporting

Defaults for physics/engineering work. A target journal's author guidelines
or a project's CLAUDE.md override these.

- Always compute: slope and its SE, intercept and its SE (if the model has one),
  r², RMSE, p-value, n, and the x range. Add MBE for model-vs-measurement fits.
- Choose H₀ from the question: slope = 0 for "is there a relationship/trend";
  slope = 1 and intercept = 0 (or an equivalence test with a stated tolerance)
  for model-vs-measurement agreement. Ask if the purpose is unclear.
- Name the method (OLS, Deming, York, ODR). Prefer an errors-in-variables
  method when x has significant measurement error. For time series, note that
  autocorrelation makes OLS SEs and p-values too optimistic.
- For through-origin fits, note that r² isn't comparable with the r² of fits
  with an intercept.
- Rounding: uncertainty to 1–2 significant figures, the value rounded to the
  same decimal place. Always give units for slope and intercept.
- Text format: y = (a ± σa)x + (b ± σb) unit, r² = …, RMSE = … unit, n = ….
  State the method, the meaning of ± (default 1 SE) and H₀ once, in the methods
  section or caption, not after every equation.
- Several regressions go in a table: one row each; columns slope ± SE,
  intercept ± SE, r², RMSE, (MBE), p, n, x range; units in headers; method, ±
  and H₀ in the caption.
- Plots: put a short text box in a corner (equation with rounded coefficients
  and no ±, r², n, and RMSE if space allows); use the legend only to identify
  lines. Draw the fit only over the data range. Model-vs-measurement plots: 1:1
  line, equal axes, square aspect. More than about 1000 points: hexbin/2D
  histogram or transparent markers. Confidence band only when n is small.
- Report p as p < 0.001 rather than 0.000. Judge results by effect size and CI,
  not by p alone, especially at large n.
