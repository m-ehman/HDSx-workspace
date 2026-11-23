# AI-Use Note

## Audit trail

Tool: Claude, in one claude.ai chat. I shared the A8 brief, some week 9 textbook pages, the three A8 starter files, my A7 submissions in my repository, and my classmate's feedback. The prompts below are condensed from that chat.

- **`slides.qmd` (slide wording)**
  - AI prompt (condensed): “Context: an A8 slide deck built from one figure, a line chart of mean BMI by NHANES cycle for middle-income adults aged 20 to 80 (29.0 in 1999-2000, 30.3 in 2021-2023, dips to 28.3 in 2001-2002 and 28.9 in 2011-2012). Original: the placeholder text in `starter-slides.qmd`. Audience: public health program managers who are not data specialists. Task: fill the starter slides with an audience, a question, a why-it-matters line, a one-sentence takeaway, a limitation and a next step. Rules: reuse my A7 wording where it fits, describe only what the figure shows, compare two survey waves rather than claim a trend, and make no causal or population claims.”
  - Verified: the takeaway numbers match the first and last points on the A7 figure and my A7 adaptation note; the five parts Task 6 requires (context, evidence, takeaway, limitation, next step) appear across four content slides; no causal or population wording.
- **`slides.qmd` (layout)**
  - AI prompt (condensed): “Render the deck and check that the figure, source note and limitation are readable on each slide. Suggest the smallest layout change that fixes any problem.”
  - Verified: after Claude suggested moving the takeaway to its own slide, placing the source note as the figure caption, adding a References slide and using `{.smaller}` on slide 5, I rendered the deck and checked that every slide fits and that the source note and limitation are visible, as the brief requires.
- **`plain-language-summary.md`**
  - AI prompt (condensed): “Context: the same figure and slides. Audience: the same program managers. Task: write a 150-250 word summary covering the four comm05 parts: who the audience is, what the result says, what it does not prove and what should follow. Rules: define BMI, NHANES and middle-income in plain words, use only numbers from my A7 outputs, and make no trend, causal or population claims.”
  - Verified: the four comm05 parts appear in order; every number matches the A7 figure or adaptation note; no trend, causal or population claims.
- **`source-note.md`**
  - AI prompt (condensed): “Draft 1-3 bullets naming the dataset and its citation (matching the `cdc-nhanes` entry in `references.bib`), the file and settings that produced the figure, and the descriptive, unweighted caveat.”
  - Verified: three bullets, within the brief's 1-3; the citation matches the References slide; the file path and `selected_income` value match my A7 submission, so the figure is traceable.
- **`peer-feedback.md` (feedback request and synthesis)**
  - AI prompt (condensed): “Context: the comm04 feedback table and the brief's `peer-feedback.md` requirements. Original: my classmate's numbered answers to the comm04 prompts. Task: place her answers in the table, suggest a revision tied to her specific comment, and draft one sentence describing it. Rules: keep her wording, and tie the revision to a change in the slides.”
  - Verified: the table matches her answers; the revision is tied to her row 8 comment, as comm05 requires; the revised limitation appears on slide 5 of the rendered deck.

## What AI helped with

Claude reviewed the brief, flagged the required structures and suggested the A7 figure as evidence. It drafted the first pass of the slide wording, the plain-language summary, the source note, and a draft of this note. Claude also rendered copies of my slides to check the layout, made a PDF of the deck for my reviewer, and suggested a revision from her feedback.

## What I changed

- I chose the A7 figure, the revealjs deck and program managers as the audience.
- Claude first suggested a caution line under the takeaway. I moved it into the limitation on slide 5 instead, so each slide covers one part of the story.
- I shortened my reviewer's improvement row to one item, with her agreement.
- I reviewed all of Claude's suggeste wording and drafts and made minor edits to wording for clarity and tone.

## How I verified the result

- **Numbers:** every value in the slides and summary (29.0, 30.3, 28.3, 28.9, and more than 1,000 adults per point) matches the A7 figure and adaptation note.
- **Claims:** the takeaway compares two survey waves and does not claim a trend, a cause or a national estimate.
- **Visibility:** the source note sits under the figure on slide 3, and the limitation is on slide 5 at full size.
- **Structure:** four content slides cover all five required parts; the summary has all four comm05 parts; the source note has three bullets.
- **Render:** the deck renders without errors, and I downloaded `slides.html` and checked every slide.
- **Privacy:** I did not share row-level data with any AI tool. Claude worked from my committed files, aggregate outputs, the course pages and my reviewer's feedback.