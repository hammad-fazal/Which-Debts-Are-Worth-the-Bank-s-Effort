# Which Debts Are Worth the Bank's Effort?

A guided analysis of whether a more intensive debt-recovery strategy appears to recover more than its incremental cost. The exercise focuses on accounts near an **expected recovery amount of $1,000**, where the supplied strategy changes from Level 0 to Level 1. The assumed extra cost of Level 1 is **$50 per account**.

**Project type:** Guided DataCamp Workspace project. The scenario and dataset are supplied for learning; this is not an assessment of a real bank.

## Repository contents

| File | Purpose |
| --- | --- |
| [`which_debpts_are_worth.ipynb`](which_debpts_are_worth.ipynb) | Exploratory plots, balance checks and regression models; original filename retained |
| [`datasets/bank_data.csv`](datasets/bank_data.csv) | 1,882 account records with expected and actual recovery, strategy, age and sex |

## Question and method

Accounts with expected recovery amounts up to $1,000 receive Level 0 treatment; those just above $1,000 receive Level 1. Comparing all accounts in the two groups would confound treatment with expected recovery. The notebook therefore examines accounts **near the cutoff**, using a simple regression-discontinuity approach.

1. Plot age against expected recovery amount near the threshold.
2. In the $900-$1,100 window, check age using Kruskal-Wallis and sex using a chi-square test.
3. Plot actual recovery and compare it near the threshold, including a narrower $950-$1,050 window.
4. Fit OLS for actual recovery using expected recovery, then add an indicator for being at or above $1,000. Repeat with the narrower window.
5. Compare the estimated recovery jump with the scenario's $50 extra cost.

## Results recorded in the notebook

| Expected recovery window | Accounts | Estimated threshold jump | Extra cost |
| --- | ---: | ---: | ---: |
| $900-$1,100 | 183 | About **$278** | $50 |
| $950-$1,050 | 99 | About **$287** | $50 |

The age and sex balance tests in the wider window report p-values around **0.063** and **0.538**, respectively. They check two observed characteristics; they do not prove the groups are identical. Both model estimates exceed the assumed extra cost. This supports the notebook's conclusion **for the supplied scenario near the $1,000 cutoff**.

## Limitations

- The supplied dataset and guided exercise do not establish that the effect generalizes to other banks, periods or strategy cutoffs.
- Other differences between groups or manipulation around the threshold could affect a causal interpretation.
- The analysis does not provide a full operational cost, risk or compliance assessment.
- The conclusion concerns this local cutoff; it does not evaluate every strategy level.

## Run locally

Use Python 3 with pandas, NumPy, Matplotlib, SciPy, statsmodels and Jupyter. From the repository root:

```bash
python -m pip install pandas numpy matplotlib scipy statsmodels jupyter
jupyter notebook which_debpts_are_worth.ipynb
```

Run cells in order so `datasets/bank_data.csv` resolves. Saved plots and model summaries are also visible on GitHub.

## Skills and attribution

The notebook demonstrates Python data analysis, visual exploration, statistical checks, an OLS threshold model and translating an estimate into a cost comparison. It contains **no SQL or production pipeline**. The notebook and scenario originate from a guided DataCamp project, with its instructional context retained in the file.
