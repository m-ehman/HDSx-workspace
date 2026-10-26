# AI-Use Note

## Audit trail

Tool: Claude, in one claude.ai chat. The inline prompts are condensed summaries of my requests in that chat, and the code comments label them that way.

### Data load chunk (`visualization-audit.qmd`)

```r
# AI prompt (condensed from Claude chat): "Load nhanes_equity_v6.csv in a Quarto file
#   using a repository-root relative path (our _quarto.yml sets execute-dir: project),
#   and stop with a clear message if the file is missing."
# Verified: rendered with no errors; glimpse() shows 105,626 rows and 18 columns,
#   with BMI, IncomeGroup, Cycle, and Age spelled as used below.
```

### Draft plot chunk

```r
# AI prompt (viz05 Template 1 wording; code drafted by Claude in chat): "I have a data frame called 
#   bmi_by_income_cycle with columns Cycle, IncomeGroup, n and mean_bmi. Write a ggplot2 figure with 
#   mean_bmi on the y-axis and Cycle on the x-axis, with one line per IncomeGroup. The summary is 
#   unweighted and descriptive. Do not add a trend line or smoothing."
# Verified: column names match glimpse(); 33 points match the summary table;
#   no geom_smooth(); no "Removed rows" warning on render.
```

### Corrected plot chunk

```r
# AI prompt (viz05 Template 2 wording plus my audit fixes; code drafted by Claude in chat):
#   "Revise the draft: order IncomeGroup from low to high, with labels naming the
#   income-to-poverty ratio bands; use the Dark2 palette; start the y-axis at 0; add
#   labs() so the title describes the comparison without a causal claim, the subtitle
#   states the summary is unweighted for adults 20-80, and the caption gives the source,
#   exclusions, n range, y-axis choice and the missing 2019-2020 cycle."
# Verified: count() shows all three groups recoded with 11 cycles each and no NA;
#   render shows no "Removed rows" warning; points match the summary table; legend
#   reads Low, Middle, High; y-axis starts at 0; caption n range matches range(n);
#   brewer.pal.info lists Dark2 as colour-blind safe.
```

### Export chunk

```r
# Source: viz07 ggsave() call, saving corrected_plot instead of last_plot().
# AI prompt (condensed from Claude chat): "Save corrected_plot to the submission folder
#   as in viz07, with a white background so the PNG reads in any viewer."
# Verified: corrected-plot.png appears in submission/, opens in Open Preview with a
#   white background, and matches the figure in the rendered HTML.
```

### Revision text ("What the plot shows" and "What I revised and why")

```html
<!-- AI prompt (condensed from Claude chat): "Based on my identified issues and proposed solutions, draft a short, non-causal reading of the corrected plot and two paragraphs explaining what I revised from the starter plot and my draft, and why." -->
<!-- Verified: matched each number to R output: age range in the starter data (2 to 85); starter vs adult 2021-2023 means (group order reverses); endpoint_cycles (2 of 11 kept); summary table (a dip in each group; Low and Middle cross); adult means above 28 (32 of 33); lowest group per cycle (High in all 11); first vs last cycle (all three rose). Scanned the text for causal or population words. -->
```

### Files without inline comments

**`visual-audit-note.md`**
- AI prompt (condensed from Claude chat): "Audit flawed-plot-code.R. For each issue, give the audit category, why it matters and the correction, in the template's table. I believe there are issues with the age filtering, cycles included, "drives" in the title implies causality, obesity in the title vs bmi, truncated y axis, and the non-relative data path. Check these and others."
- Verified: ran an R check for each row (ages and share under 20, endpoint cycles and dips, means above 28, missing counts, income-to-poverty cut points, cycle list); read lines 10 to 14 of the script for the path row; checked the Correction column against the corrected plot.

**`caption.md`**
- AI prompt (condensed from Claude chat): "Write a caption for the corrected plot using the viz03 caption template, naming the statistic, data source, exclusions with a count, and one limitation (viz05 Template 3 checklist)."
- Verified: counted adults aged 20 to 80 and the excluded records in R, and matched the difference to the summary total; checked the caption against viz07's four required elements.

**`m1-link-note.md`**
- AI prompt (condensed from Claude chat): "We are planning to create a scatterplot. Based on these details [blurb from 'Planned figure' in initial-visual-plan.md], draft two or three sentences on how the visualization standards we have referenced applies to our planned INDFMPIR and PHQ-9 scatterplot."

- Verified: checked that each sentence names something specific to our project and matches our submitted visual plan; rejected a first draft that proposed changing the submitted plan.

**YAML header (`embed-resources: true`)**
- No prompt: Claude suggested this without being asked, so the HTML would hold its own figures. 
- Verified: No `visualization-audit_files/` folder was created, and the downloaded HTML shows both plots on its own.

## What AI helped with

- **Code:** Claude drafted the data load, draft plot, corrected plot and export chunks. 
- **Audit and writing:** I identified six of the starter plot's issues. Claude checked them, added two more (unreported missing records and group sizes; the palette, legend order and legend title), and drafted the issue descriptions and the draft-plot rows. Claude also drafted the caption, the revision paragraphs and the M1 link note.

## What I changed

- **Audit wording:** I reviewed and edited Claude’s draft issue descriptions to improve the wording and reflect how I understood the issues and proposed solutions. 
- **Comparison:** I kept the starter plot's comparison after checking the README, viz06 and viz07, which tie the A5 plot to the studio revision.
- **Attribution:** I asked Claude where the draft plot code came from and changed its prompt line to show that the wording is from viz05 Template 1 and the code is from Claude.

## How I verified the result

- **Column names:** I checked every column name in the code against `glimpse()`, and confirmed the income labels with `count()` before recoding them.
- **Numbers against course pages:** my total n (50,851) matches the sum of the group sizes in the Week 6 overview table. My missing counts (9,356 BMI, 9,415 income) match the same page. My hand-checked 1999-2000 Low Income mean matches the viz03 table (28.80654).
- **Audit claims:** I checked each row of the audit note in R, including the ages in the starter data, the dropped cycles, the 32 of 33 means its y-axis limits would delete, the missing counts and the income-to-poverty cut points.
- **Scale:** I confirmed the corrected y-axis starts at 0 and that the render shows no "Removed rows" warning.
- **Claims:** I checked the caption's exclusion count two ways (6,286 of 57,137 adults), and scanned all text for causal or population wording.