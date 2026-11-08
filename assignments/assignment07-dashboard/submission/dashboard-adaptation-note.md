# Dashboard Adaptation Note


## Audience

A public-health analyst preparing a short equity briefing for program managers who are not data specialists. The analyst will copy the dashboard figure into briefing slides, where it will be read without the rest of the dashboard page. The briefing focuses on middle-income adults, the group just above the low-income cut-off.

## Dashboard Question

How has average BMI among middle-income adults aged 20 to 80 changed across NHANES survey waves in the classroom dataset?

## Control And Visualization

- Control or interaction: `selected_income`, an editable value in the Control chunk of `dashboard.qmd`. It takes one of the three `IncomeGroup` values: `"Low Income (<1.3)"`, `"Middle Income"` or `"High Income (>3.5)"`. The analyst edits the value and renders again. A value that does not match exactly falls back to `"High Income (>3.5)"`, the first group in alphabetical order.
- Visualization affected: the line chart of mean BMI across the 11 NHANES cycles in the dataset (1999-2000 to 2021-2023) for the selected income group.
- What changes when the control changes: the summary table's `n` and `mean_bmi` values, the plotted points and line, and the plot title ("Mean BMI for" plus the selected group) all switch to the new group. The subtitle, axis labels and caption stay the same, so they must hold true for every group.

## Before And After

| Original text | Revised text | Why the revision helps |
|---|---|---|
| Figure caption: "Descriptive, unweighted classroom summary. Missing BMI, income group, cycle, and out-of-cohort ages are excluded." | Six-line figure caption: "Each point is the mean BMI (kg/m²) of more than 1,000 adults in one survey wave (NHANES cycle). Income groups use the family income-to-poverty ratio, with cut-offs at 1.3 and 3.5. The dataset has no 2019-2020 cycle, and the y-axis does not start at 0. Excludes ages outside 20-80 and records missing BMI, income group or cycle. This unweighted, descriptive summary does not give national estimates or show that income causes differences in BMI." | A reader of the slide learns what each point shows, what an NHANES cycle and the income cut-offs mean, that 2019-2020 is missing and the y-axis is zoomed, and the limits of the summary. No analytic logic changed. |

**KT rationale:** Program managers will see this figure in a slide, not on the dashboard page. A caption that explains the measure, the gap and the limits lets them read the pattern correctly without the analyst there, and keeps the limitation attached to the figure.

## Test Result

On 2026-11-08, I rendered the dashboard from the repository root with `quarto render assignments/assignment07-dashboard/submission/dashboard.qmd` for `"Low Income (<1.3)"`, `"Middle Income"` and `"High Income (>3.5)"`. Each render finished with no errors or warnings. The title, table and plot updated each time, and the six-line caption stayed in full and held true for every group. The submitted file is set to `"Middle Income"`, and it rendered in a fresh Codespace. Full results are in `testing-log.md`.

## Limitation

This unweighted, descriptive summary does not give national estimates or show that income causes differences in BMI. It appears as the last two lines of the figure caption.

## Privacy Check

The submitted preview shows only the figure: mean BMI by survey cycle for one income group, with no row-level records. Every point averages at least 1,089 adults, so there are no small cells to overclaim. The caption states that the summary is unweighted and descriptive and does not show cause, so the preview makes no causal or population claims.