# Visual Audit Note

## Plot Question

What was the mean BMI in each income group across NHANES cycles, among adults aged 20 to 80 in the prepared classroom dataset?

## Issues Checked

### Flawed starter plot (`flawed-plot-code.R`)

| Issue | Category | Why it matters | Correction |
|---|---|---|---|
| The subtitle says "Adults age 20-80", but the code never filters on age, so it averages records from ages 2 to 85. | Correctness | Records under 20 make up 39% of the plotted data and pull every mean down, which reverses the group order: among adults, Low Income has the highest 2021-2023 mean (30.4), not the lowest. | Filtered to ages 20 to 80 and stated the restriction in the subtitle. |
| The code keeps only the first and last of 11 cycles and joins them with dashed lines, while the subtitle says BMI "climbed steadily across every NHANES cycle." | Bias and aggregation | Dropping nine cycles hides real dips, such as High Income adults falling from 28.8 in 2007-2008 to 28.2 in 2011-2012. | Plotted all 11 cycles with solid lines and points, and removed the "steadily" claim. |
| The title says low income "drives" obesity in "American adults." | Interpretation | "Drives" claims cause, and "American adults" implies a population estimate, which an unweighted summary of a classroom snapshot cannot support. | Used a descriptive title and stated in the subtitle that the summary is unweighted. |
| The title says "obesity" and the y-axis says "BMI", but the plot shows mean BMI. | Correctness | Mean BMI does not show the proportion of participants classified as having obesity. | Named the statistic as "Mean BMI" in the title and on the y-axis. |
| `scale_y_continuous(limits = c(24, 28))` sets a narrow 4-unit axis. | Design | The narrow range makes small gaps look large, and `limits` removes out-of-range values from the plotted data: with the age filter fixed, 32 of 33 adult means exceed 28. | Removed the limits, started the axis at 0 with `expand_limits(y = 0)`, and stated this in the caption. |
| Records missing BMI or income are dropped without comment, and group sizes are never counted. | Bias and aggregation | Readers cannot see that 9,356 records lack BMI and 9,415 lack income, or check whether any group is small. | Counted n per group, dropped groups under 30, and disclosed the exclusions and n range in the caption. |
| The default palette shows High Income in red and Low Income in green, the legend runs High, Low, Middle, and the legend title "Income" does not name the measure. | Design | Red and green are hard to tell apart for many colour-blind readers, alphabetical order breaks the income gradient, and ">3.5" and "<1.3" mean little without "income-to-poverty ratio." | Used the colour-blind-safe Dark2 palette, ordered groups from low to high income, and named the measure in the legend. |
| The first data path is a Windows desktop path, and the third climbs one folder too many (`../../../`). | Reproducibility | A machine-specific path breaks the course's relative-path rule and could quietly load a different copy of the data on the analyst's machine. | Used one path relative to the repository root, which the workspace's `execute-dir: project` setting supports. |

### My draft plot

| Issue | Category | Why it matters | Correction |
|---|---|---|---|
| The default y-axis zooms in on the data, from about 28 to 30.5. | Design | Gaps of 1 to 1.5 BMI units fill the panel and look large. | Started the axis at 0 with `expand_limits(y = 0)`. |
| The draft has no title, subtitle or caption. | Interpretation | Nothing tells the reader that the summary is unweighted, limited to adults aged 20 to 80, or missing excluded records. | Added a descriptive title, subtitle and caption. |
| The cycles are evenly spaced, but the dataset has no 2019-2020 cycle. | Design | The last step, from 2017-2018 to 2021-2023, spans four years but looks like two. | Noted the missing cycle in the caption. |
| The draft keeps the default palette and alphabetical legend. | Design | It repeats the colour and ordering problems in the starter plot. | Applied the same palette and ordering fixes. |

## Final Caption

This figure shows mean BMI by family income-to-poverty ratio group across 11 NHANES cycles, from 1999-2000 to 2021-2023 (the dataset has no 2019-2020 cycle), for adults aged 20 to 80 in the prepared NHANES Health Equity classroom dataset. The summary is descriptive and unweighted. Records missing BMI, income group or cycle were excluded (6,286 of 57,137 adults), leaving 1,089 to 2,088 records per point. The plot supports comparison of patterns, not causal claims or population-level estimates.

## AI-Use Check

Claude helped draft the plot code, the issue list, the caption, and the revision text. I checked the code against `glimpse()` column names and my summary table, confirmed the y-axis starts at 0, verified each issue in R, and removed causal and population claims. Details are in `ai-use-note.md`.
