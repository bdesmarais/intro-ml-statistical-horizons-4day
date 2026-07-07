# Machine Learning — Statistical Horizons (4-day)

Participant materials for Bruce Desmarais's **Machine Learning** seminar with
[Statistical Horizons](https://statisticalhorizons.com/seminars/machine-learning/).

Everything a participant needs: the slide decks, the hands-on R tutorials, and the data.

## Contents

```
slides/       Compiled slide decks (PDF), one per day
tutorials/    Hands-on R Markdown tutorials + data, grouped by the day they're covered
  day1_intro_and_evaluation/     01_turnout, 02_fearon_laitin
  day2_regression_extensions/    09_energy_efficiency, 10_wine_quality
  day3_regularization_and_selection/  08_ames_housing, 11_state_policy_liberalism, 12_state_welfare_spending
  day4_classic_learners/         05_gibler_braithwaite, 06_pinyonjay_rsf, 07_snake_rsf
```

- `slides/day1_intro_and_evaluation.pdf` — Introduction & model evaluation
- `slides/day2_regression_extensions.pdf` — Regression extensions (logistic/MLE, polynomials, splines, GAMs)
- `slides/day3_regularization_and_selection.pdf` — Ridge / lasso / elastic net / best-subset (ABESS)
- `slides/day4_classic_learners.pdf` — SVM, trees, random forests, XGBoost, k-NN, interpretation

## Running the tutorials

Each tutorial is a self-contained `.Rmd`. **The tutorials read their data directly from this
repository over the web**, so you can knit them from anywhere (including Posit Cloud) without
downloading anything — just open the `.Rmd` and knit. The rendered `.pdf` sits next to each `.Rmd`
so you can see the expected output.

Install the packages once with `tutorials/packages_needed.R`.

## Data

Each tutorial's data lives in its own `data/` folder here and is pulled by raw-GitHub URL from
inside the tutorial (e.g. `read.csv("https://raw.githubusercontent.com/bdesmarais/intro-ml-statistical-horizons-4day/main/tutorials/.../data/...")`).
