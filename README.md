# Plastic Waste is Our Global Problem
### A Statistical Case Study on Policy Impact and Behavioral Change

**Author:** Tri Hieu Vu (Student ID: 139663)  
**Context:** Case study prepared for UNEP environmental data analysis  
**Tools:** Microsoft Excel  
**Data:** ~212 survey respondents per country, 848 total observations  

---

## Why Do We Care About Plastic Waste?

Between 1950 and 2018, the amount of plastic produced worldwide skyrocketed from 1.5 million tons to more than 350 million tons per year. However, only a small fraction of this is recycled. Much of the rest is buried, burned, or worse — washed up in the ocean, harming marine life like turtles, seabirds, and fish.

The United Nations Environment Programme (UNEP) conducted a study on plastic consumption behavior across countries. This report analyzes data from four countries: Country A, which has not signed a commitment to reduce plastic waste, and Countries B, C, and D, which have signed and implemented such commitments.

The central question is: will Country A really discharge more plastic because of the lack of binding policies?

---

## Data Overview

Each record represents one survey respondent with two variables:

| Variable | Description |
|---|---|
| Plastic waste | Kilograms generated per person per year |
| Awareness participation | Number of environmental events attended in past 12 months |
| Country A | Has not signed a commitment to reduce plastic waste |
| Countries B, C, D | Have signed and implemented plastic waste reduction commitments |

Sample size: approximately 212 individuals per country (848 total).  
Data is stored in `139663_Vu.xls`.

---

## Analytical Approach

The analysis follows five steps, each building on the previous one.

**Step 1 — Descriptive Statistics**  
Calculate basic metrics to understand the data: mean (a person's "typical" level of waste), median (the value in the middle if the entire data is sorted from low to high), standard deviation (how the data is scattered around the mean), coefficient of variation (the ratio between standard deviation and mean), and skewness (which side the data is skewed toward). Purpose: compare A and B to see if there are any early signs that A discharges more.

**Step 2 — 98% Confidence Interval for Country A**  
We cannot survey the entire population, but we can estimate a range in which the real value is almost certainly there. If the averages of other countries are outside this range, then there is a basis to show that Country A is significantly different.

**Step 3 — ANOVA Test (all four countries)**  
Used to test whether at least one of the four countries has markedly different levels of littering. If true, continue to specifically examine how Country A differs from each other country.

**Step 4 — Z-Test (Country A vs. Country B)**  
Test the hypothesis: does Country A really litter more than Country B? Used to determine whether the discrepancy is reliable or just luck from random data.

**Step 5 — Correlation Between Awareness and Littering Behavior**  
Check: do people who participate in many awareness-raising activities litter less? If there is a reverse relationship (participants are more → discharge less), then community education can be an effective solution.

---

## Key Findings

### 1. Does Country A Really Litter More?

The results show that Country A wastes an average of 104.84 kg of plastic per year, which is significantly higher than the ~98–99 kg range across Countries B, C, and D. The median of Country A (105.54 kg) is also higher than the others, suggesting that the high tendency to litter in A is common, not just due to a few extreme cases.

| Country | Mean (kg/person) | Median (kg/person) | Std Dev | CV | Skewness |
|---|---|---|---|---|---|
| A (No Policy) | **104.84** | 105.54 | 7.47 | 0.071 | -1.399 |
| B (Policy) | 98.47 | 98.20 | 11.00 | 0.112 | -0.005 |
| C (Policy) | 99.24 | — | 5.00 | — | — |
| D (Policy) | 98.13 | — | 4.00 | — | — |

When looking at the standard deviation, Country A has a lower value (7.47 kg compared to 11.00 kg for B). This shows that the level of littering in A is quite uniform between individuals, while in B there is a larger difference. The coefficient of variation reinforces this: Country A has 7.1% while Country B has 11.2%, demonstrating that littering behavior in A is stable and less volatile.

The skewness provides interesting information: a negative skew value in Country A (-1.40) indicates that the majority of people litter a lot, while only a few litter a little. In contrast, Country B has an almost balanced distribution (skew ≈ 0), which means that littering is more evenly distributed.

Combining all the indicators, Country A not only has a higher-than-average level of litter, but also tends to be more uniform and prevalent throughout the population. This is an early clear indication that A may be littering more than Country B systematically, not by chance.

![Mean Plastic Waste by Country with 98% Confidence Interval](images/chart1_mean_ci.png)

---

### 2. Comparison with Country A's Confidence Interval

The 98% confidence interval for Country A is in the range of [103.64 kg, 106.04 kg]. This means that with 98% confidence, we can confirm that the actual average of Country A is not less than 103.64 kg and not greater than 106.04 kg.

On average, the waste of Countries B, C, and D is outside (and below) the confidence interval of Country A. This shows that the difference is obvious and cannot be explained by random error during sampling.

| Statistic | Value |
|---|---|
| Mean (kg/person) | 104.84 |
| Standard Deviation (kg) | 7.47 |
| Sample Size (n) | 212 |
| z-value (98% confidence) | 2.326 |
| Confidence Interval (kg) | [103.64, 106.04] |

| Country | Mean (kg) | Within CI? |
|---|---|---|
| Country B | 98.47 | No — falls below |
| Country C | 99.24 | No — falls below |
| Country D | 98.13 | No — falls below |

This result reinforces the conclusion from the previous section: Country A has a systematically higher level of littering, and the difference is not just accidental observation in the sample, but most likely exists in the national population.

![Distribution of Plastic Waste by Country](images/chart2_boxplot.png)

---

### 3. Are There Any Other Countries That Litter Differently?

One-way ANOVA tests whether at least one country in the group has a significantly different mean from the others.

- H₀: The average plastic waste of 4 countries is the same
- H₁: At least one country has a differential average of waste

**ANOVA Table:**

| Source of Variation | SS | df | MS | F | p-value |
|---|---|---|---|---|---|
| Between Groups | 6303.623 | 3 | 2101.208 | 38.587 | 2.26e-23 |
| Within Groups | 45959.42 | 844 | 54.454 | | |

Since the p-value is very small (close to zero) and F > F-critical (2.615), H₀ is rejected. There is strong statistical evidence that at least one country has markedly different levels of littering than the rest.

Although ANOVA does not indicate which country caused the difference, based on the averages it can be seen that Country A has the highest value (104.84 kg) and is likely the main contributor to this difference.

---

### 4. Does Country A Really Litter More Than Country B?

- H₀: The average plastic waste in Country A is equal to Country B (μA = μB)
- H₁: Country A litters more than Country B (μA > μB)

| Parameter | Value |
|---|---|
| z-statistic | 6.87 |
| Rejection threshold z₁₋ₐ | 1.28 |
| Conclusion | Reject H₀ |

Since z = 6.87 > 1.28, we are in the rejection zone. The average difference between the two countries is statistically significant — not due to chance or data interference.

Country A has a significantly higher average level of litter than Country B. This suggests that Country A's non-participation in an international agreement on waste control may be a factor in the higher level of pollution. The difference is statistically reliable and can reflect the reality of people's plastic consumption behavior.

---

### 5. Do Participants in Many Environmental Events Litter Less?

- H₀: There is no correlation between the number of events and the amount of waste (r = 0)
- H₁: There is a negative correlation — participates more → litters less (r < 0)

![Correlation: Awareness Events vs. Plastic Waste](images/chart3_correlation.png)

| Country | Correlation Coefficient r |
|---|---|
| A | -0.2203 |
| B | -0.6527 |
| C | -0.3883 |
| D | -0.3832 |

The negative correlation coefficient in all countries shows that participants in many events tend to litter less. For Country A specifically:

| Statistic | Value |
|---|---|
| t-value | -3.27 |
| Degrees of freedom (df) | 210 |
| Rejection zone | t < -2.358 (α = 0.01) |
| Result | -3.27 < -2.358 → Reject H₀ |

There is clear statistical evidence that the negative correlation between event attendance and waste volume in Country A is significant. In other words, people who actively participate in environmental activities tend to litter less.

This strongly supports the hypothesis that raising awareness and organizing community events have a positive impact on reducing plastic waste, especially in Country A, which has not signed an international commitment to plastic waste control.

---

## Conclusions

Analysis of data from four countries shows a stark difference in plastic littering behavior between Country A and the other three countries (B, C, D):

Country A has the highest littering rate of the four countries, with an average of 104.84 kg per person per year — significantly higher than the rest. The difference between A and B is statistically significant, confirmed by the z-test, suggesting that this is not a random result. The ANOVA analysis demonstrates that there is at least one country in the group with markedly different levels of littering, and most likely Country A. The 98% confidence interval of Country A does not intersect with the average of B, C, D, further reinforcing that A is the exception. A negative correlation between the number of environmental event visits and the amount of waste showed that raising public awareness had a positive impact — and this correlation is statistically significant in Country A.

---

## Policy Recommendations for UNEP

**1. Encourage Country A to join the international agreement on plastic waste control**, as it is currently the only country in the group that has not signed it, and high levels of littering indicate that this may be having a negative impact.

**2. Strengthen public awareness programs**, especially practical events such as marine debris cleanup and recycling workshops, as data shows that participants in these events tend to litter less.

**3. Set specific waste reduction targets** based on average data and country-by-country volatility, to make it easy to track progress.

**4. Support countries that are behaving well** — B, C, D — to continue to maintain and share successful policy models with other countries.

The analyses in this report provided clear quantitative evidence of the plastic waste problem and the impact of policy and public education. This is fully in line with UNEP's mission: to act on data for a sustainable environment.

---

## Areas for Further Investigation

- Evaluate effectiveness of specific policy types (bans, taxes, incentive schemes) across different national contexts
- Analyze demographic or regional differences within each country to identify which population segments drive the gap
- Measure the long-term impact of awareness programs — does behavioral change persist or decay over time?
- Assess infrastructure factors such as recycling system access and waste collection quality as potential confounders

---

## Repository Structure
```
plastic-waste-analysis/
    README.md
    data/
        raw_data.xlsx
    analysis/
        statistical_analysis.xlsx
    report/
        case_study.pdf
    images/
        chart1_mean_ci.png
        chart2_boxplot.png
        chart3_correlation.png
    src/
        generate_charts.py
```

---

## References

Statista — Global Plastic Waste Overview: https://www.statista.com/topics/5401/global-plastic-waste/  
United Nations Environment Programme (UNEP) — Plastic Waste Policy Framework
