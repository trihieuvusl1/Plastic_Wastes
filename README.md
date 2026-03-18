# Plastic Waste is Our Global Problem
### A Statistical Case Study on Policy Impact and Behavioral Change

Context: Case study prepared for UNEP environmental data analysis
Tools: Python (matplotlib, scipy, numpy), Microsoft Excel
Data: 212 survey respondents per country, 848 total observations

## Why Do We Care About Plastic Waste?

Between 1950 and 2018, the amount of plastic produced worldwide skyrocketed from 1.5 million tons to more than 350 million tons per year. However, only a small fraction of this is recycled. Much of the rest is buried, burned, or worse — washed up in the ocean, harming marine life like turtles, seabirds, and fish.

The United Nations Environment Programme (UNEP) conducted a study on plastic consumption behavior across countries. This report analyzes data from four countries: Country A, which has not signed a commitment to reduce plastic waste, and Countries B, C, and D, which have signed and implemented such commitments.

The central question is: will Country A really discharge more plastic because of the lack of binding policies?

## Data Overview

Each record represents one survey respondent with two variables:

| Variable | Description |
|---|---|
| Plastic waste | Kilograms generated per person per year |
| Awareness participation | Number of environmental events attended in past 12 months |
| Country A | Has not signed a commitment to reduce plastic waste |
| Countries B, C, D | Have signed and implemented plastic waste reduction commitments |

Sample size: approximately 212 individuals per country (848 total). Data is stored in `139663_Vu.xls`.

## Analytical Approach

The analysis follows five steps, each building on the previous one.

**Step 1 — Descriptive Statistics**
Calculate basic metrics to understand the data: mean (a person's "typical" level of waste), median (the value in the middle if the entire data is sorted from low to high), standard deviation (how the data is scattered around the mean), coefficient of variation (the ratio between standard deviation and mean), and skewness (which side the data is skewed toward). The purpose is to compare A and B to see if there are any early signs that A discharges more.

**Step 2 — 98% Confidence Interval for Country A**
We cannot survey the entire population, but we can estimate a range in which the real value is almost certainly there. If the averages of other countries fall outside this range, then there is a basis to show that Country A is significantly different.

**Step 3 — ANOVA Test across all four countries**
Used to test whether at least one of the four countries has markedly different levels of littering. If that is the case, we then continue to specifically examine how Country A differs from each other country.

**Step 4 — Z-Test comparing Country A and Country B**
Test the hypothesis: does Country A really litter more than Country B? This step determines whether the discrepancy is reliable or just luck from random data.

**Step 5 — Correlation Between Awareness and Littering Behavior**
Check whether people who participate in many awareness-raising activities litter less. If there is a reverse relationship where more participation leads to less discharge, then community education can be considered an effective solution.

## Key Findings

### 1. Does Country A Really Litter More?

The results show that Country A wastes an average of 104.84 kg of plastic per year, which is significantly higher than the ~98–99 kg range across Countries B, C, and D. The median of Country A (105.54 kg) is also higher than the others, suggesting that the high tendency to litter in A is common across the population, not just due to a few extreme cases.

| Country | Mean (kg/person) | Median (kg/person) | Std Dev | CV | Skewness |
|---|---|---|---|---|---|
| A (No Policy) | **104.84** | 105.54 | 7.47 | 0.071 | -1.399 |
| B (Policy) | 98.47 | 98.20 | 11.00 | 0.112 | -0.005 |
| C (Policy) | 99.24 | — | 5.00 | — | — |
| D (Policy) | 98.13 | — | 4.00 | — | — |

Looking at the standard deviation, Country A has a lower value (7.47 kg compared to 11.00 kg for B), which shows that the level of littering in A is quite uniform between individuals while in B there is a larger spread. The coefficient of variation reinforces this point: Country A sits at 7.1% while Country B reaches 11.2%, demonstrating that littering behavior in A is stable and less volatile.

The skewness tells an interesting story. A negative skew value in Country A (-1.40) indicates that the majority of people litter a lot while only a few litter a little. Country B, by contrast, has an almost balanced distribution (skew ≈ 0), meaning that littering is more evenly spread across its population.

Combining all the indicators, Country A not only has a higher-than-average level of litter but also tends to be more uniform and prevalent throughout the population. This is an early clear indication that A may be littering more than Country B systematically, not by chance.

![Mean Plastic Waste by Country with 98% Confidence Interval](images/chart1_mean_ci.png)

### 2. Comparison with Country A's Confidence Interval

The 98% confidence interval for Country A falls in the range of [103.64 kg, 106.04 kg], meaning that with 98% confidence we can confirm the actual average of Country A is not less than 103.64 kg and not greater than 106.04 kg.

On average, the waste of Countries B, C, and D all sit outside and below this interval, which shows that the difference is real and cannot be explained by random error during sampling.

| Statistic | Value |
|---|---|
| Mean (kg/person) | 104.84 |
| Standard Deviation (kg) | 7.47 |
| Sample Size (n) | 212 |
| z-value (98% confidence) | 2.326 |
| Confidence Interval (kg) | [103.64, 106.04] |

| Country | Mean (kg) | Within CI? |
|---|---|---|
| Country B | 98.47 | No, falls below |
| Country C | 99.24 | No, falls below |
| Country D | 98.13 | No, falls below |

This result reinforces the conclusion from the previous section: Country A has a systematically higher level of littering, and the difference most likely exists in the national population, not just in the sample.

![Distribution of Plastic Waste by Country](images/chart2_boxplot.png)

### 3. Are There Any Other Countries That Litter Differently?

One-way ANOVA tests whether at least one country in the group has a significantly different mean from the others, with the following hypotheses:

H₀: The average plastic waste of all 4 countries is the same
H₁: At least one country has a differential average of waste

| Source of Variation | SS | df | MS | F | p-value |
|---|---|---|---|---|---|
| Between Groups | 6303.623 | 3 | 2101.208 | 38.587 | 2.26e-23 |
| Within Groups | 45959.42 | 844 | 54.454 | | |

Since the p-value is very small (close to zero) and F exceeds the critical value of 2.615, H₀ is rejected. There is strong statistical evidence that at least one country has markedly different levels of littering. While ANOVA does not point to a specific country, the averages clearly suggest that Country A at 104.84 kg is the main contributor to this difference.

### 4. Does Country A Really Litter More Than Country B?

Moving from the overall ANOVA result to a direct pairwise comparison, the hypotheses are:

H₀: The average plastic waste in Country A equals Country B (μA = μB)
H₁: Country A litters more than Country B (μA > μB)

| Parameter | Value |
|---|---|
| z-statistic | 6.87 |
| Rejection threshold z₁₋ₐ | 1.28 |
| Conclusion | Reject H₀ |

Since z = 6.87 is far beyond the threshold of 1.28, the average difference between the two countries is statistically significant and not due to chance. Country A has a significantly higher average level of litter than Country B, and this suggests that Country A's non-participation in an international agreement on waste control may be a contributing factor.

### 5. Do Participants in Many Environmental Events Litter Less?

To understand whether awareness programs can serve as a practical lever, the correlation between event attendance and waste volume was tested for each country:

H₀: There is no correlation between the number of events and the amount of waste (r = 0)
H₁: There is a negative correlation where more participation leads to less waste (r < 0)

![Correlation: Awareness Events vs. Plastic Waste](images/chart3_correlation.png)

| Country | Correlation Coefficient r |
|---|---|
| A | -0.2203 |
| B | -0.6527 |
| C | -0.3883 |
| D | -0.3832 |

All four countries show a negative correlation, meaning participants in more events tend to litter less. For Country A specifically, the t-value of -3.27 falls below the rejection threshold of -2.358 at α = 0.01, so H₀ is rejected. This confirms that the relationship is statistically significant in Country A, not a coincidence. People who actively participate in environmental activities do tend to litter less, even without a binding policy framework in place.

## Conclusions

Analysis of data from four countries shows a stark difference in plastic littering behavior between Country A and the other three countries. Country A has the highest littering rate with an average of 104.84 kg per person per year. The z-test confirms that the difference between A and B is statistically significant and not a random result. The ANOVA analysis shows that at least one country behaves markedly differently from the rest, and Country A is the most likely cause. The 98% confidence interval of Country A does not overlap with the averages of B, C, or D, which further reinforces that A is the outlier. Finally, the negative correlation between event attendance and waste volume is statistically significant in Country A, showing that raising public awareness does make a measurable difference.

## Policy Recommendations for UNEP

**1. Encourage Country A to join the international agreement on plastic waste control.** It is currently the only country in the group that has not signed, and the data suggests this absence may be contributing directly to higher pollution levels.

**2. Strengthen public awareness programs**, particularly practical events such as marine debris cleanup and recycling workshops. The data consistently shows that participants in these activities tend to generate less waste.

**3. Set specific waste reduction targets** based on each country's average and variance levels so that progress can be tracked meaningfully over time.

**4. Support Countries B, C, and D** in maintaining their current performance and sharing their policy models with Country A as a reference.

The analyses in this report provided clear quantitative evidence of the plastic waste problem and the impact of policy and public education. This is fully in line with UNEP's mission: to act on data for a sustainable environment.

## Areas for Further Investigation

- Evaluate the effectiveness of specific policy types such as bans, taxes, or incentive schemes across different national contexts
- Analyze demographic or regional differences within each country to identify which population segments drive the gap
- Measure the long-term impact of awareness programs and whether behavioral change persists or decays over time
- Assess infrastructure factors such as recycling access and waste collection quality as potential confounders in the policy-waste relationship

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

## References

Statista — Global Plastic Waste Overview: https://www.statista.com/topics/5401/global-plastic-waste/
United Nations Environment Programme (UNEP) — Plastic Waste Policy Framework
