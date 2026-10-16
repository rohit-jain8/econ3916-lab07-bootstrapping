# Estimation & Bootstrapping — Quantifying Uncertainty Without a Formula

## Objective

The goal of this lab was to understand how we can measure uncertainty in statistical estimates using standard errors, confidence intervals, and bootstrapping, especially when traditional formulas aren't available or reliable.

## Methodology

- Loaded the UCI Adult Census Income dataset containing 32,561 respondents and examined variables including age, weekly hours worked, and capital gains.
- Compared standard deviation and standard error across four different sample sizes to understand how increasing sample size improves the precision of an estimate.
- Used the Central Limit Theorem (CLT) to construct parametric confidence intervals and compared how quickly sampling distributions approached normality for age and capital gains.
- Performed bootstrapping manually and using `scipy.stats.bootstrap` to estimate standard errors and construct 95% confidence intervals.
- Compared percentile and BCa bootstrap confidence intervals for capital gains to understand how skewed data affects uncertainty.
- Used bootstrapping to estimate the difference in average weekly hours worked between men and women.
- Calculated a 90/10 percentile ratio to examine inequality in positive capital gains.
- Used AI to generate a reusable bootstrap confidence interval function, revised my prompt to control randomness, and compared the results with my earlier calculations.
- Ran a coverage simulation using lognormal data with a sample size of 50 to compare parametric and bootstrap confidence intervals.

## Key Findings

- The standard deviation of age was 13.640 years, while the standard error for a sample of 100 was approximately 1.36 years. Increasing the sample size by a factor of four reduced the standard error by half.
- The sampling distribution of mean age became approximately normal much faster than the distribution of mean capital gains, which was heavily skewed.
- The bootstrap standard error for median age was 0.0000 because every resample returned the same median of 37. This reflected the large number of tied ages in the dataset rather than an error in the bootstrap process.
- For positive capital gains, the estimated mean was $12,939, with a bootstrap 95% confidence interval of [$12,114, $13,780].
- The percentile and BCa confidence intervals for mean capital gains were similar, although their endpoints differed slightly.
- Men reported working an average of 42.43 hours per week compared with 36.41 hours for women, a difference of 6.02 hours. The 95% BCa confidence interval was [5.73, 6.28] hours, which excluded zero but did not establish causation.
- The 90/10 ratio for positive capital gains was 6.45, with a 95% BCa confidence interval of [6.24, 8.37], showing uncertainty in the inequality estimate.
- My AI-generated bootstrap function initially produced different results across runs because it didn't control the random seed. After revising my prompt to include a seed, the results matched SciPy's interval of [$12,173, $13,796].
- In the coverage simulation, both methods slightly under-covered the mean, with a difference within the Monte Carlo standard error of approximately 1.3 percentage points. For the median, the mean-centered parametric interval performed much worse, while the bootstrap stayed near its intended 95% coverage.

Overall, this lab helped me understand why it's important to distinguish between the spread of individual observations and the uncertainty of an estimate. I also learned that bootstrapping can be useful when traditional formulas aren't available, but its results still depend on the characteristics of the data and how the samples are collected.
