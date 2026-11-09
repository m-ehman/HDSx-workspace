# AI-Use Note

## Audit trail

Tool: Claude, in one claude.ai chat. I shared the A7 brief, excerpts from the Week 8 pages, the starter code templates, and my rendered HTML outputs. The prompts below are condensed from that chat.

### Caption in the Visualization chunk (`dashboard.qmd`)

```r
# AI prompt (condensed from Claude chat): "Rewrite this ggplot2 caption for program managers who
#   will see the figure in slides. The plot shows mean_bmi (numeric) by Cycle (character, 11 values
#   from 1999-2000 to 2021-2023, no 2019-2020) for one IncomeGroup ('Low Income (<1.3)', 'Middle
#   Income' or 'High Income (>3.5)'), adults with Age 20-80 and BMI and Cycle present. Explain the
#   statistic, NHANES cycle, income cut-offs, missing cycle and zoomed y-axis, and add one
#   non-causal limitation. One sentence per line, true for every income group."
# Verified: count(IncomeGroup, Cycle) for adults 20-80 with BMI, IncomeGroup and Cycle present
#   gives 11 cycles per group, a minimum n of 1,089 and no 2019-2020 cycle; exclusions match
#   filter() in the Summary chunk; render shows all six caption lines in full and a y-axis that
#   does not start at 0; no causal or population wording.
```

### Notes without inline comments

- **`dashboard-adaptation-note.md`**
  - AI prompt (condensed): “Using the A7 template headings, draft an adaptation note for a public-health analyst briefing program managers: the audience, one question the unchanged starter can answer, an accurate description of the `selected_income` control and the chart it updates, and Test Result, Limitation and Privacy Check sections that match my separate files.”
  - Verified: confirmed the control values and fallback order with `sort(unique(na.omit(nhanes$IncomeGroup)))` in R; checked that the unchanged starter can answer the question; checked the interpretation numbers against my Middle Income render and that its wording is descriptive, with no causal or population claims; checked that the Test Result, Limitation and Privacy Check sections match the separate files.
- **`before-after-text.md`**
  - AI prompt (condensed): “List three audience-facing text elements in the starter that could be clearer for program managers reading the figure on a slide, without changing analytic logic. For the one I choose, draft the dash04 record: original and revised text verbatim, one sentence on why it helps, and one confirming no analytic logic changed.”
  - Verified: confirmed the original text matches the starter and the revised text matches the caption in `dashboard.qmd` word for word; checked that the file has dash04's four parts; checked that the revised caption makes no causal or population claims; `git diff` against the starter shows changes only to the caption, its comments and the `selected_income` value.
- **`testing-log.md`**
  - AI prompt (condensed): “Following the dash05 routine, draft a testing log with the date, render command, each `selected_income` value tried and what updated, leaving blanks for my results.”
  - Verified: filled in the titles, mean BMI values and smallest n from my own renders of all three groups, and the fresh Codespace result from my own render; confirmed the log covers the date, command, values tried and results the brief asks for.
- **`limitation-note.md` and `privacy-check.md`**
  - AI prompt (condensed): “Draft one limitation sentence identical to the caption’s last sentence. Then draft three privacy sentences covering dash05 (data source and classroom boundary, aggregate-only output, no row-level data shared with AI) and the README (no row-level data, small cells or causal claims).”
  - Verified: confirmed the limitation is one sentence, matches the caption word for word, and makes no causal or population claim; confirmed `privacy-check.md` has three sentences covering the dash05 and README points; took the smallest n (1,089) from my three renders; confirmed the sentence on AI sharing is accurate.
- **`reproducibility-note.md`**
  - AI prompt (condensed): “Draft one paragraph stating the render command, the relative data path, the packages needed, and confirming the file renders in a fresh Codespace.”
  - Verified: confirmed the command and relative path match `testing-log.md` and the Setup chunk; checked that tidyverse and knitr are the only packages loaded; rendered the submitted file in a new Codespace.

## What AI helped with

Claude reviewed the brief and Week 8 pages, flagged the required structures and two inconsistencies, and suggested the audience, the question and the figure caption as the element to change. It drafted the caption, its code, the six other notes and a first draft of this note. To check that the caption fit the figure, Claude redrew the plot using only the aggregate Low Income table printed on dash03. It also checked my rendered HTML files against the expected values.

## What I changed

- I reviewed all of Claude's drafts and made minor edits to the wording across most of the notes for clarity, accuracy and tone.
- I chose the caption from three candidate changes and added a plain-language meaning for "NHANES cycle" (survey wave), adapted from dash04's label example.
- I kept the caption right-aligned, ggplot2's default, rather than add a formatting line, so the change stays text-only.
- I filled in the testing log from my own renders and edited the sentence in the privacy check on what Claude saw.
- I chose Middle Income as the submitted group instead of the starter’s default, Low Income, and reworded the dashboard question to match.
- I kept AI-drafted wording only where it matched my rendered output and the A7 brief.

## How I verified the result

- **Caption claims:** in R, `count(IncomeGroup, Cycle)` for adults aged 20 to 80 with BMI, income group and cycle present gave 11 cycles per group, a smallest n of 1,089, and no 2019-2020 cycle.
- **Control:** `sort(unique(na.omit(nhanes$IncomeGroup)))` listed the three values in the fallback order.
- **Renders:** I rendered all three groups and checked the title, table, plot and six caption lines each time, with no warnings. I then set the submitted value to Middle Income and rendered again.
- **Analytic logic:** `git diff` against the starter showed changes only to the caption, its comments and the `selected_income` value.
- **Fresh Codespace:** the submitted file rendered without errors in a new Codespace.
- **Wording:** I checked that the caption and notes match the output and make no causal, population or row-level claims, as A7's AI-use expectations require.
- **Privacy:** I did not share row-level data with any AI tool. Claude saw only the code, excerpts from the course pages and my rendered aggregate outputs.