# Viral vs Legacy Artist Analysis

## Overview

This project analyzes Spotify artist data to distinguish between **viral breakout artists** and **legacy artists** by separating short-term popularity momentum from long-term audience size. Rather than relying on raw popularity or follower counts alone, the analysis uses a residual-based framework to identify artists who are significantly overperforming or underperforming relative to expectations.

The central question is whether some artists achieve unusually high popularity despite having relatively small followings, while others maintain massive followings with only average or declining popularity.

---

## Core Idea

Artist popularity is strongly correlated with follower count. To avoid confusing scale with momentum, we first estimate the **expected popularity** for an artist given their number of followers. The difference between actual popularity and this expected value, called the **residual**, captures whether an artist is outperforming or underperforming relative to peers of similar size.

Residuals are then standardised into **z-scores**, which measure how rare or extreme an artist’s deviation is compared to the overall distribution. This allows for principled identification of viral behavior as a statistical outlier rather than an arbitrary threshold.

---

## Methodology

1. **Log-transform followers**  
   Follower counts are log-transformed to reflect diminishing returns of scale, where the difference between 1K and 10K followers is more meaningful than between 10M and 11M.

2. **Model expected popularity**  
   A robust regression is fitted to estimate expected artist popularity as a function of log-transformed followers.

3. **Compute residuals**  
   Residual = actual popularity − expected popularity.  
   Positive residuals indicate overperformance; negative residuals indicate underperformance.

4. **Standardise residuals (z-scores)**  
   Residuals are scaled using a robust measure of spread to identify statistically rare deviations.

5. **Classify artists**  
   - Viral breakout candidates: large positive z-scores with relatively low to mid follower counts  
   - Legacy artists: very large follower counts with residuals near zero  
   - Declining legacy: large follower counts with negative residuals  
   - Stable or normal: artists whose popularity aligns with expectations

---

## Visual Diagnostics

The analysis relies on three key plots for validation:

- **Popularity vs Followers with Expected Trend**  
  Confirms that popularity generally increases with follower count and validates the expected popularity baseline.

- **Residual Popularity Distribution**  
  Shows that most artists cluster near zero residual, with viral artists appearing as rare positive outliers.

- **Residuals vs Followers**  
  Demonstrates that popularity deviations are independent of follower size, confirming successful separation of scale and momentum.

These plots ensure that viral detection reflects genuine anomalies rather than artifacts of artist size.

---

## Key Findings

- Viral popularity is statistically rare and appears as extreme positive residuals.
- Most artists behave predictably given their follower base.
- Legacy artists cluster around zero residual at high follower counts, indicating stability rather than growth.
- Underperformance and decline are more common than breakout success.

---

## Limitations

- Artist popularity reflects aggregate momentum and cannot fully confirm one-hit wonders, which are fundamentally track-level phenomena.
- The analysis is cross-sectional and does not capture time-based dynamics such as sustained growth or decay.
- Results depend on the quality and coverage of the Spotify dataset used.

---



## Conclusion

This project provides a principled, data-driven framework for distinguishing viral breakout artists from legacy artists by evaluating popularity relative to expectation rather than raw scale. By focusing on residuals and statistical rarity, the approach avoids common pitfalls of ratio-based metrics and offers a robust foundation for further analysis of artist growth and virality.
