# AI-Use Note

## Audit trail

Tool: Claude, in one claude.ai chat. I shared the A7 brief, excerpts from the Week 8 pages the starter files and my rendered HTML outputs. The prompts below are condensed from that chat.

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
  - AI prompt (condensed): "Suggest a specific audience and question for the starter dashboard, then draft each template section from my choices and test results."
  - Verified: the control values and fallback order with `sort(unique(na.omit(nhanes$IncomeGroup)))` in R; the Test Result, Limitation and Privacy Check sections against the separate files.
- **`before-after-text.md`**
  - AI prompt (condensed): "Give me candidate text changes for this audience, then draft the dash04 before-and-after file for the one I pick."
  - Verified: the original text matches the starter; the revised text matches the caption in `dashboard.qmd`; `git diff` against the starter shows changes only to the caption, its comments and the `selected_income` value.
- **`testing-log.md`**
  - AI prompt (condensed): "Draft a testing log for the dash05 six-step routine."
  - Verified: I filled in the titles, mean BMI values and smallest n from my own renders of all three groups.
- **`limitation-note.md` and `privacy-check.md`**
  - AI prompt (condensed): "Draft one limitation sentence that matches the caption, and three privacy sentences covering dash05 and the README."
  - Verified: the limitation sentence matches the caption word for word; the smallest n (1,089) comes from my three renders.
- **`reproducibility-note.md`**
  - AI prompt (condensed): "Draft one paragraph naming the render command, relative data path and fresh Codespace result."
  - Verified: the command and path match `testing-log.md`; I rendered the submitted file in a new Codespace.

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
- **Privacy:** no row-level data went to AI. Claude saw only the code, excerpts from the course pages and my rendered aggregate outputs.