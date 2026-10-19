# Dependency note

## R packages

- **tidyverse**: `readr` for `read_csv()`, and `dplyr` for `filter()`, `group_by()`, `summarise()` and `arrange()`.
- **knitr**: `kable()` to show the parity table in the HTML.

Both come with the course Codespace, so nothing extra was installed.

## Python packages

- **pandas**: loading, filtering, grouping and summarising in `translation.ipynb` and `helpers.py`.
- **pathlib**: part of Python's standard library; `helpers.py` uses it to check the file path.

pandas and the Jupyter notebook tools are listed in the root `.devcontainer/requirements.txt`. I did not add any packages, so that file is unchanged, and there is no second requirements file in the submission folder.

## Notebook hygiene

- The notebook runs on the course Codespace's Python 3.11 kernel, not a separate virtual environment.
- I reran it from a fresh kernel (Restart, then Run All) before committing.
- I cleared all outputs before committing, so the file holds no stale results.
- `helpers.py` sits in the same folder as the notebook, so `from helpers import load_and_preview` works.