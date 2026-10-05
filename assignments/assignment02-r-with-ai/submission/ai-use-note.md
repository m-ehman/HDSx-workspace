# AI-Use Note

## Audit trail

AI prompt: "Give me a line or two of code to check that Education is only recorded for adults."
Verified: youngest age with education recorded is 20; all 47,164 non-adults are missing education.

AI prompt: "Summarize BMI by Education for adults 20+, add a BMI 30+ flag with mutate(), and 
show missing BMI in each group instead of dropping it."
Verified: College Grad row recalculated separately and matched; 
NA row matches the 87 adults missing Education; 
group sizes add up to all adults.

AI prompt: "Give me code to check that the values in the education summary table are correct."
Verified: every expected value matched the table.

AI prompt: "Suggest a simple function that returns n, number missing, mean, and SD for a numeric variable" 
(with the starter's mean_with_n() as an example).
Verified: results for adults$BMI matched single-line calculations; 
known-answer test on made-up values passed.

AI prompt: "Give me single lines of code that return n, number missing, mean, and SD for adults$BMI, 
to compare with describe_numeric()."
Verified: all four values and the known-answer test matched.

## What AI helped with
I used Claude (Opus 5.5) to map the assignment requirements, suggest a summary question (BMI by Education among adults), 
and draft the summary table, the describe_numeric() function, and the checks for each.

## What I changed
I rejected Claude's first draft, which rewrote the data path and added more complicated code than I needed. 
After that, I instead started from the top of the assignment, and worked through each chunk separately. 
I asked for an additional verification of Education and missingness. I asked for a stronger check of the education summary, 
as the first version only checked column names and row counts, not the table's values.

## How I verified the result
I confirmed Education is only recorded for adults before using it. I recalculated the College Grad row separately, 
matched it to the summary table, and checked that no adults were lost. I compared describe_numeric() with 
single-line calculations and a known-answer test I could work out by hand.