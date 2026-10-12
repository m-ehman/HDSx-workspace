## Git audit note

## Diff summary (AI-assisted, verified by me)

Added one sentence in README.md to clarify assignment submission folder requirements.
No code lines were added or removed.

## AI prompt and output

*Diff inspection*

**Prompt:** I asked Copilot Chat: "I am about to commit these changes. Explain what I 
changed in plain English. Did I delete or change anything important?"

**Copilot Chat output:** "You added one sentence to README.md: it tells students to put 
submission files in the relevant assignment’s submission/ folder and gives an example path.
You didn’t delete or change any existing text in the diff. It’s a documentation-only 
clarification; it doesn’t change how the project works."

**My verification:** I manually inspected the diff and confirmed this was accurate. 

*Commit message*

**Prompt:** I asked Copilot Chat: "Based on this diff, write a one-sentence, professional commit message for my Quarto document."

**Copilot Chat output:** Clarify assignment submission folder requirements in the README.

**My verification:** I confirmed this accurately represented the substance of the change. 

## .gitignore check

Checked .gitignore at the repo root. It already excludes R session files, Quarto temp 
folders, OS files and .env secrets. No unwanted generated or temporary files were being tracked and required HTML remains committable, so no change was needed.

## AI-use sentence

I used Copilot Chat to summarize the diff and draft the commit message; 
I re-read the diff myself and confirmed the summary is accurate.

## M0 readiness

**Members:** Morgan Ehman (`m-ehman`), Yoon Park (`yoon-cloud-28`), Humnah Rashid (`humnahr`), 
and Jade Lee (`Jade-ok`) 

**Repository access:** I am the group repository owner. All members accepted the invite, 
confirmed their access, and made an initial commit. 

**Communication plan:** We have a group WhatsApp chat, and we will conduct weekly check-ins 
for 10 minutes after each Tuesday class. 

**Codespaces access:** All members opened the group Codespace, made a separate branch, 
ran `quarto check`, and confirmed that R, Quarto, and the tidyverse were available. 

**Repository status:** Ready for M0.
