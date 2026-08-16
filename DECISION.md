# Decision Log

## Assignment 2: Dataset (2026-07-16)

- Dataset: combined NBA player contract and performance data for the 2025-26 season, compiled from Spotrac (contracts), Basketball-Reference (performance), and NBA.com (international status).
- Main variable of interest: **player salary**, because we wanted to explore it against performance metrics and were curious how teams evaluate contracts. We noted it would also be useful in binary form (over/under a threshold).
- Key decision: chose this dataset as a team because of a shared interest in sports analytics and how teams determine contracts and evaluate performance — the goal was to understand player and team performance through data, not just box scores.

## Assignment 3: Descriptive Stats & Data Visualization (2026-07-24)

- Cleaning done: no missing values in the dataset. We collapsed five roster positions into three (Guard, Forward, Center) and reduced birthplace to a US/international binary. Salary was converted to a plain numeric value.
- For each continuous variable, we calculated count, mean, median, standard deviation, minimum, maximum, and range. For each categorical variable, we calculated count, mode, and number of unique categories.
- Most surprising pattern: salary is heavily right-skewed — mean of $9M vs. median of $3M — meaning a small number of high earners pull the average well above what a typical player makes. There was also a small dip in games-played around 10-40 games, which raised questions about load management or injury status. Notable outliers included Cooper Flagg (age 19) and LeBron James (age 41), and salary outliers ranging from under $15K to Steph Curry's $59.6M. 

## Assignment 4: Probability & Distributions (2026-07-26)

- Normal vs. empirical, and why: none of the seven continuous variables (age, rebounds, assists, points, minutes, games played, salary) met the assumptions of a normal distribution — most were right-skewed, games played was left-skewed, and minutes per game was flatter than normal. Because of this, we used percentiles from the empirical distribution rather than the normal distribution to calculate probabilities (e.g., \~28% of players earn over $10M; the 90th percentile salary is \~$28.36M). This reinforced how misleading the average salary (\~$9.3M) is compared to the median (\~$3.6M).

## Assignment 5: Hypothesis Testing & Confidence Intervals (2026-08-07)

- What we tested, alpha, conclusion: ran a one-sample hypothesis test and confidence interval (95%) on mean player salary. Both point to the same conclusion — the mean is solidly above $5M, but it's pulled upward by a small group of stars, not the typical player (median salary is only $3.63M, below the confidence interval's lower bound). With a sample size of 566, we used a t-distribution despite the right skew in salary and points per game, since independence held reasonably well (one player's stats don't meaningfully affect another's). We noted results should be read as specific to this season rather than generalized across years.

## Assignment 6: Regression Modeling (2026-08-12)

- First predictor removed and why: nationality/international status was dropped early — there's no logical mechanism by which birthplace should affect salary, and it added no explanatory value and had the highest P value. We tested five candidate models before settling on a final model with four predictors: position (guard = baseline), minutes per game, assists per game, and points per game (adjusted R² = 0.615). The adjusted R^2 explains \~61.5% of the variation in NBA player salaries.
- Multicollinearity handling: minutes per game, points per game, and assists per game are all correlated (minutes-points r = 0.87, assists-minutes r = 0.71), which is likely why minutes per game showed a counterintuitive negative coefficient. We kept all three anyway because each captures a distinct aspect of player value (playing time, scoring, playmaking) that the others don't fully explain, and "guard" showed only weak correlation with the other predictors so it wasn't a concern. Points per game was the strongest, most reliable predictor (~$1.79M in salary per additional point per game).
