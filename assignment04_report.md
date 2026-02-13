# Assignment 04 Interpretation Memo

**Student Name:** [Alycia Reji
**Date:** February 12th, 2026
**Assignment:** REIT Annual Returns and Predictors (Simple Linear Regression)

---

## 1. Regression Overview

You estimated **three** simple OLS regressions of REIT *annual* returns on different predictors:

| Model | Y Variable | X Variable | Interpretation Focus |
|-------|------------|------------|----------------------|
| 1 | ret (annual) | div12m_me | Dividend yield |
| 2 | ret (annual) | prime_rate | Interest rate sensitivity |
| 3 | ret (annual) | ffo_at_reit | FFO to assets (fundamental performance) |

For each model, summarize the key results in the sections below.

---

## 2. Coefficient Comparison (All Three Regressions)

**Model 1: ret ~ div12m_me**
- Intercept (β₀): [0.1082] (SE: [0.006], p-value: [0.000])
- Slope (β₁): [-0.0687] (SE: [0.032], p-value: [0.035])
- R²: [0.002] | N: [2527]

**Model 2: ret ~ prime_rate**
- Intercept (β₀): [0.1998] (SE: [0.016], p-value: [0.000])
- Slope (β₁): [-0.0194] (SE: [0.003], p-value: [0.000])
- R²: [0.016] | N: [2527]

**Model 3: ret ~ ffo_at_reit**
- Intercept (β₀): [0.0973] (SE: [0.009], p-value: [0.000])
- Slope (β₁): [0.5770] (SE: [0.567], p-value: [0.309])
- R²: [0.000] | N: [2518]

*Note: Model 3 may have fewer observations if ffo_at_reit has missing values; statsmodels drops those rows.*

---

## 3. Slope Interpretation (Economic Units)

**Dividend Yield (div12m_me):**
- A 1 percentage point increase in dividend yield (12-month dividends / market equity) is associated with a [0.0687] change in annual return.
- [Your interpretation: Is higher dividend yield associated with higher or lower returns? Why might this be?] 
higher dividend yield is associated with lower annual returns. REITs with higher dividend yields may have depressed stock prices suggesting market concerns about their future growth prospects. REITs with lower dividend yields might be reinvesting profits for capital appreciation leading to better overall returns.

**Prime Loan Rate (prime_rate):**
- A 1 percentage point increase in the year-end prime rate is associated with a [-1.94%] change in annual return.
- [Your interpretation: Does the evidence suggest REIT returns are sensitive to interest rates? In which direction?]
Yes returns appear sensitive to interest rates, and the relationship is negative (higher rates are associated with lower REIT returns)

**FFO to Assets (ffo_at_reit):**
- A 1 unit increase in FFO/Assets (fundamental performance) is associated with a [0.5770] change in annual return.
- [Your interpretation: Do more profitable REITs (higher FFO/Assets) earn higher returns?]
The slope is positive but it is not statistically significant so the evidence does not support a reliable relationship between higher FFO/assets and higher returns in this model.

---

## 4. Statistical Significance

For each slope, at the 5% significance level:
- **div12m_me:** [Significant / Not significant] — [one sentence conclusion] at the 5% sig level, the slope is statistically significant
- **prime_rate:** [Significant / Not significant] — [one sentence conclusion] at the 5% sig level, the slope is statistically significant
- **ffo_at_reit:** [Significant / Not significant] — [one sentence conclusion] at the 5% sig level, the slope is not statistically significant 

**Which predictor has the strongest statistical evidence of a relationship with annual returns?** the prime rate has the strongest statistical evidence with the smallest p-value.

---

## 5. Model Fit (R-squared)

Compare R² across the three models:
- [Your interpretation: Which predictor explains the most variation in annual returns? Is R² high or low in general? What does this suggest about other factors driving REIT returns?]
Prime rate explains the most variation with the highest R squared (0.016). overall r squared values are very low suggesting most variation in REIT returns is driven by other factors beyond these single predictors.

---

## 6. Omitted Variables

By using only one predictor at a time, we might be omitting:
- [market conditions]: drives REIT returns and can correlate with rates/dividend yield.
- [property sector fundamentals]: affect cash flows and returns, could correlate with FFO/assets
- [leverage/capital structure]: higher leverage can boost returns but is tied to interest rates and dividend policy

**Potential bias:** If omitted variables are correlated with both the X variable and ret, our slope estimates may be biased. [Brief discussion of direction if possible]
If rates are higher when the economy is stronger, omitting market/sector conditions could make the negative rate slope too weak. if higher leverage coincides with higher rates and higher returns, omitting leverage could also bias the rate slope toward zero or even positive.

---

## 7. Summary and Next Steps

**Key Takeaway:**
[2-3 sentences summarizing which predictor(s) show the strongest relationship with REIT annual returns and whether the evidence is consistent with economic theory]
The prime rate shows the strongest and statistically significant relationship with REIT annual returns, and the negative slope is consistent with theory that higher interest rates raise financing costs. Dividend yield is also significant but weak, with a small negative association. FFO/Assets is not significant, so profitability alone does not explain returns in this simple setup.

**What we would do next:**
- Extend to multiple regression (include two or more predictors)
- Test for heteroskedasticity and other OLS assumption violations
- Examine whether relationships vary by time period or REIT sector

---

## Reproducibility Checklist
- [ ] Script runs end-to-end without errors
- [ ] Regression output saved to `Results/regression_div12m_me.txt`, `regression_prime_rate.txt`, `regression_ffo_at_reit.txt`
- [ ] Scatter plots saved to `Results/scatter_div12m_me.png`, `scatter_prime_rate.png`, `scatter_ffo_at_reit.png`
- [ ] Report accurately reflects regression results
- [ ] All interpretations are in economic units (not just statistical jargon)
