# AI-Use Note

## Audit trail

Tool: Claude, in one claude.ai chat. The load, cohort and missingness code comes from the Week 7 worked example (eda03) and was not AI-drafted, except for one AI-suggested fallback path in the load chunk. The comment pairs below cover that line and the two AI-drafted chunks:

```text
Load chunk (fallback path only)
# AI prompt (fallback path only): Adapt the eda03 load code for a file in
#   assignments/assignment06-eda-ai-audit/submission/, three folders below the repo root.
# Verified: From the repo root, file.exists() returned TRUE when the fallback
#   was prefixed with assignments/assignment06-eda-ai-audit/submission/.
#   The load chunk selected examples/nhanes-equity/data/nhanes_equity_v6.csv.

Complete-case chunk
# AI prompt: Using `analysis_df` (adults 20-80):
#   1. Keep rows where BMI and IncomeGroup are both non-missing; store as `table1_df`.
#   2. Add a row "Rows after excluding missing BMI or income group" to `cohort_counts`
#      and print the updated table.
#   Use tidyverse only. Drop rows only for missing BMI or IncomeGroup, not other columns.
# Verified: table1_df has 50,851 rows; 57,137 - 50,851 = 6,286 rows dropped, matching
#   sum(is.na(analysis_df$BMI) | is.na(analysis_df$IncomeGroup)); anyNA(table1_df$BMI) is FALSE

Table 1 chunk
# AI prompt: Adapt the eda03 Table 1 code to use `table1_df` instead of `analysis_df`, so N
#   counts the same records behind each mean. Remove the IncomeGroup NA filter, since
#   `table1_df` already excludes those rows. Keep the eda03 mean_sd() helper and column labels.
#   Save the table with write_csv() to assignments/assignment06-eda-ai-audit/submission/table1.csv
#   (renders run from the repo root). Use tidyverse only.
# Verified: N sums to 50,851, matching the flow table; table1_df |> count(IncomeGroup) matches N;
#   mean_sd() uses sd(), not var(); table1.csv appears in submission/ with the same three rows;
#   means and SDs recomputed by group without mean_sd() match the table
```

## What AI helped with

Claude drafted the chunks above and the prose in the EDA note, including the methods note, which it adapted from the eda07 template. It also drafted the provenance note from the eda03, eda05 and eda07 templates, the Cohort, Missingness and AI-Use Check sections of the audit note, and a first draft of this note. I identified the seven planted issues myself, and Claude checked them against the code and helped word the audit table.

## What I changed

I replaced AI-drafted versions of the load, cohort and missingness code with the eda03 code, dropped the `stopifnot()` checks the AI had added and ran those checks in the console instead, and removed an `embed-resources` setting that the root `_quarto.yml` already provides. In the audit, I dropped two suspected issues that I felt did not hold up on checking, and edited down the text. I also edited the AI-drafted prose throughout all files for clarity, accuracy and tone.

## How I verified the result

I reran the row counts in the console at each step (105,626, 57,137 and 50,851) and confirmed that ages 20 and 80 were kept. I checked that missingness percentages use the cohort as the denominator (BMI 1.8%, not the full-file 8.9%), that Table 1's N sums to 50,851, that the BMI and age means and SDs match a separate recalculation, and that `table1.csv` is written to `submission/`. I compared the code with the eda03 worked example and confirmed every number in the audit table with console checks.