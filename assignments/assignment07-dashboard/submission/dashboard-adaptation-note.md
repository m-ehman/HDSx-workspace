# Dashboard Adaptation Note


## Audience

A public-health analyst preparing a short equity briefing for program managers who are not data specialists. The analyst will copy the dashboard figure into briefing slides, where it will be read without the rest of the dashboard page.

## Dashboard Question

For adults aged 20 to 80 in one income group, how does mean BMI differ across NHANES cycles in the classroom dataset?

## Control And Visualization

- Control or interaction: `selected_income`, an editable value in the Control chunk of `dashboard.qmd`. It takes one of the three `IncomeGroup` values: `"Low Income (<1.3)"`, `"Middle Income"` or `"High Income (>3.5)"`. The analyst edits the value and renders again. A value that does not match exactly falls back to `"High Income (>3.5)"`, the first group in alphabetical order.
- Visualization affected: the line chart of mean BMI across the 11 NHANES cycles in the dataset (1999-2000 to 2021-2023) for the selected income group.
- What changes when the control changes: the summary table's `n` and `mean_bmi` values, the plotted points and line, and the plot title ("Mean BMI for" plus the selected group) all switch to the new group. The subtitle, axis labels and caption stay the same, so they must hold true for every group.

## Before And After

| Original text | Revised text | Why the revision helps |
|---|---|---|
|  |  |  |

## Test Result

State how the dashboard was run or rendered and what happened.

## Limitation

Write one limitation that should appear in or beside the dashboard.

## Privacy Check

State how the submitted preview avoids row-level data, small-cell overclaiming, and causal overclaiming.
