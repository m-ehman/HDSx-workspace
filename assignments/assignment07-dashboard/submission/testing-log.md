# Testing Log

- **Date and place:** 2026-11-08, in my GitHub Codespace.
- **Command:** from the repository root, `quarto render assignments/assignment07-dashboard/submission/dashboard.qmd`, then opened `dashboard.html` from the Explorer.
- **Values tried and results:** each render finished with no errors or warnings. The title, table and plot updated each time. The subtitle still named the dataset, and the caption's six lines stayed in full and held true: 11 cycles, no 2019-2020 cycle, every n above 1,000, and a y-axis that does not start at 0.
  - `"Low Income (<1.3)"` (starter default): title "Mean BMI for Low Income (<1.3)"; mean BMI 28.8 in 1999-2000 and 30.4 in 2021-2023; smallest n 1,089.
  - `"Middle Income"`: title "Mean BMI for Middle Income"; mean BMI 29.0 in 1999-2000 and 30.3 in 2021-2023; smallest n 1,327.
  - `"High Income (>3.5)"`: title "Mean BMI for High Income (>3.5)"; mean BMI 27.9 in 1999-2000 and 29.2 in 2021-2023; smallest n 1,123.
- **Submitted value:** set to `"Middle Income"` and rendered again, so the submitted file, HTML and preview match.