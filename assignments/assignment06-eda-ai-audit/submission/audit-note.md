# Table 1 Audit Note

## Cohort

The intended cohort is adults aged 20 to 80, inclusive. The code implements this with `filter(Age >= 20, Age <= 80)`, which keeps both endpoints and gives 57,137 records. Table 1 then excludes records missing BMI or income group, leaving 50,851.

## Missingness

Missingness was checked for BMI, Age, IncomeGroup, Gender, Race and Cycle within the age 20-80 cohort, using the cohort size as the denominator. Only BMI (1,009 records, 1.8%) and IncomeGroup (5,395 records, 9.4%) had missing values. These counts were reported before Table 1 was built.

## Planted Issues

| Issue | Category | Why it matters | Corrected approach |
|---|---|---|---|
| `filter(Age > 20, Age < 80)` excludes ages 20 and 80, but the prose says "20-80 (inclusive)". | Correctness | The code drops 3,709 records aged exactly 20 or 80 that the stated cohort includes. | Use `filter(Age >= 20, Age <= 80)` and add a `cohort_counts` flow table. |
| `candidate_paths` starts with a machine-specific path, `C:/Users/analyst/Documents/nhanes_equity_v6.csv`. | Reproducibility | Absolute paths break on other machines, and here the code only runs because it falls through to a relative path. | Use relative paths only, such as `examples/nhanes-equity/data/nhanes_equity_v6.csv`. |
| The interpretation calls BMI differences "statistically significant" and says "income determines BMI". | Interpretation | No test was run, and a descriptive table cannot show cause. | State in the methods note that the summary is descriptive and "should not be interpreted as causal effects or population estimates". |
| A comment says the data was "downloaded fresh from the NHANES website last week". | Stewardship | The code reads the cached classroom snapshot, so the comment misstates where the data came from. | Describe the data as a prepared classroom snapshot derived from public-use CDC NHANES files, and state the classroom-use boundary in the provenance note. |
| The columns say "mean (SD)", but the code computes `var()`. | Correctness | Variance is the SD squared, so High Income BMI shows 38.6 instead of an SD of 6.2. | Use `sd()`, as in the eda03 `mean_sd()` helper. |
| `na.omit()` drops rows missing any of the 18 columns, and no missingness is reported first. | Correctness | It silently removes 12,449 records (23%), including all of 2021-2023, where marital status is blank, so the table no longer describes the stated cohort. | Report missingness first, then use `filter(!is.na(BMI), !is.na(IncomeGroup))`. |
| The interpretation says removing rows with missing values makes the results "complete and publication-ready". | Interpretation | Complete-case removal can bias results if missingness is related to BMI or income, and an unweighted classroom table cannot support population claims. | State that records missing BMI or income group were excluded after missingness was reported, note the possible complete-case bias, and describe the table as descriptive and unweighted. |

## AI-Use Check

I identified the seven planted issues by reading and running the starter. Claude checked each issue against the code, flagged two suspected issues that did not hold up, and helped word the table and the Cohort and Missingness sections. I confirmed every number in the table with console checks; see `ai-use-note.md` for details.
