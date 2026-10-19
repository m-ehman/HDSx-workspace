# AI-use note

## Tools

- **GitHub Copilot Chat** in the Codespace, during class.
- **Claude (Opus 5.5)**, to review my drafts and walk through the assignment step by step.

## What AI generated

- **Copilot** drafted the pandas translation of the R pipeline, one step at a time, from this prompt: "Translate this R dplyr pipeline into Python/pandas one step at a time. For each step, explain the equivalent Python operation, the output I should inspect, and the parity check I should run against my R result. Do not combine steps or add new analysis choices."
- **Claude** reviewed that draft and my other files. It suggested the structure of the qmd and notebook and the check chunks (the raw checks, the stored-value printouts and the `identical()` checks). It also drafted the wording of the notebook audit notes, the answers to mastery exercises 1 and 2, the parity table notes, the parity discussion, the dependency note and this note.
- The R pipeline (Part A), the R function (Part B) and `helpers.py` come from the course textbook, not from AI.

## What I changed

- Simplified Copilot's translation: `dropna(subset=...)` instead of three `.notna()` conditions, `"std"` instead of a `lambda` with `ddof=1`, and default sorting instead of `sort=False`. I removed a mean age column and Python versions of the R function and exercises, which the assignment does not ask for.
- Kept the textbook version of `helpers.py` instead of Claude's suggested rewrite.
- Did not change R's display settings as Claude first suggested. Instead, I printed the stored values and noted the display difference (25.7 versus 25.74) in the parity table.
- Trimmed Claude's proposed additions to the R checks and the parity table to what the README and textbook ask for.
- Reworded a parity table note after I noticed that two `$` signs were rendering as a maths formula in the HTML.

## How I verified

- **Parity:** R and Python match on raw rows, columns, filtered rows, number of groups, group labels, and rounded means and SDs (see `parity-table.csv`).
- **R function:** five checks confirm the function gives the same rows, labels and values as the pipeline. All return `TRUE`.
- **Fresh runs:** I reran the notebook from a fresh kernel and re-rendered the qmd, then checked each output against the audit notes. An earlier draft of the notebook showed a column from a later cell because the cells had run out of order; the fresh run removed it.
- **Independent check:** Claude computed the expected values separately from the same CSV and compared them with my renders and notebook output.