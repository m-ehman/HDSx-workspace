# Before and After Text

The changed element is the figure caption, set by `caption =` inside `labs()` in the Visualization chunk of `dashboard.qmd`.

## Original text

```text
Descriptive, unweighted classroom summary. Missing BMI, income group, cycle, and out-of-cohort ages are excluded.
```

## Revised text

```text
Each point is the mean BMI (kg/m²) of more than 1,000 adults in one survey wave (NHANES cycle).
Income groups use the family income-to-poverty ratio, with cut-offs at 1.3 and 3.5.
The dataset has no 2019-2020 cycle, and the y-axis does not start at 0.
Excludes ages outside 20-80 and records missing BMI, income group or cycle.
This unweighted, descriptive summary does not give national estimates
or show that income causes differences in BMI.
```

## Why the change helps

The analyst will paste the figure into slides without the rest of the page, so the caption now gives program managers what they need to read it on its own: what each point and NHANES cycle represent, the income cut-offs, the missing 2019-2020 cycle, the zoomed y-axis and the limits of the summary.

## Analytic logic

No analytic logic changed: the only edits to `dashboard.qmd` are the caption text and the R comments recording how it was drafted and checked, so the filters, summary, plotted values and control are the same as in the starter.