# NBA-statistics -- analyzing various predictors in determining player salary

A statistics project examining how NBA player salaries relate to on-court performance, using publicly available contract and performance data from the 2025-26 season.

## The dataset

The dataset combines three public sources into one file: player contract/salary data from [Spotrac](https://www.spotrac.com/nba/rankings/player/_/year/2025/sort/cap_base), per-game performance stats from [Basketball-Reference](https://www.basketball-reference.com/leagues/NBA_2026_per_game.html), and international-roster status from [NBA.com](https://pr.nba.com/international-players-2025-26-nba-rosters). It covers 566 players and includes salary, age, position, games played, minutes per game, points per game, assists per game, rebounds per game, and birthplace (recoded to a US/international binary).

Our main variable of interest is **player salary**, which we analyzed both on its own and against performance metrics. The core research question: which performance statistics best explain (and predict) what an NBA player is paid, and how reliable is "average salary" as a benchmark given how skewed player pay actually is?

## What's in this repository

- **`data/`** — the combined contract-and-performance dataset used across the project.
- **`Assignment 2/`** — the Assignment 2 dataset submission, including our data source notes and project requirements checklist.
- **`Assignment 3/`** — descriptive statistics, frequency tables, and graphs summarizing the dataset.
- **`Assignment 4/`** — distribution analysis and probability scenarios (e.g., percentile-based salary benchmarks, since salary isn't normally distributed).
- **`Assignment 5/`** — a one-sample hypothesis test and confidence interval for mean player salary.
- **`Assignment 6/`** — a multiple regression model predicting salary from performance stats, including a multicollinearity check across five candidate models.
- **`DECISION.md`** — a dated log of the key analytical decisions made at each stage of the project.

## Team

This analysis was completed as a team project (Group 5) for a graduate statistics course, with teammates Colin and Sean. This repository was assembled and is maintained by **Leah Fisher** as part of an individual course assignment to document and version the team's shared work.
