# Plastic Waste Reduction Strategy
### A Data-Driven Case Study on Policy Impact and Behavioral Change

**Author:** Tri Hieu Vu (Student ID: 139663)  
**Context:** Case study prepared for UNEP environmental data analysis  
**Tools:** Python (matplotlib, scipy, numpy), Microsoft Excel  
**Data:** ~212 survey respondents per country, 848 total observations  

---

## Executive Summary

This analysis evaluates plastic waste generation behavior across four countries to assess the measurable impact of international policy commitments and public awareness programs.

Three findings emerge from the data:

1. Country A generates significantly more plastic waste (104.84 kg/person/year) than Countries B, C, and D (~98–99 kg), and this gap is statistically confirmed — not a sampling artifact.
2. Country A's high waste behavior is structurally uniform across its population, not driven by outliers. This signals a systemic issue rather than an individual one.
3. Participation in environmental awareness events is negatively correlated with waste generation in all four countries, and the relationship is statistically significant even in Country A — meaning awareness programs work as an independent lever, even without a formal policy framework in place.

The data supports a combined strategy: policy enforcement anchors the baseline, while behavioral interventions drive further reduction.

---

## Business Problem

Plastic waste is one of the most pressing environmental challenges globally. Between 1950 and 2018, worldwide plastic production grew from 1.5 million to over 350 million tons per year, with only a small fraction recycled.

This project addresses a policy-relevant question for UNEP and sustainability organizations:

> Do countries without formal plastic waste reduction commitments generate measurably more waste — and what levers can realistically reduce it?

This question is applicable across sustainability strategy, ESG analytics, public health policy, and environmental compliance reporting.

---

## Dataset

| Variable | Description |
|---|---|
| Plastic waste | Kilograms generated per person per year |
| Awareness participation | Number of environmental events attended in past 12 months |
| Country A | No signed international plastic waste agreement |
| Countries B, C, D | Signatories to international plastic waste reduction commitment |

Sample size: 212 individuals per country (848 total).  
Data is stored in `139663_Vu.xls`.

---

## Analytical Approach

The analysis follows a five-step statistical pipeline, each building on the previous result.

**Step 1 — Descriptive Statistics**  
Baseline comparison of all countries using mean, median, standard deviation, coefficient of variation, and skewness. Goal: detect early behavioral signals before formal testing.

**Step 2 — 98% Confidence Interval (Country A)**  
Estimate the range in which Country A's true population mean sits. If other countries' averages fall outside this range, the gap is unlikely to be explained by sampling variation.

**Step 3 — One-Way ANOVA (all four countries)**  
Test whether at least one country's mean is statistically different from the rest. Establishes the foundation for pairwise comparison.

**Step 4 — One-Tailed Z-Test (Country A vs. Country B)**  
Directional hypothesis test confirming whether Country A generates significantly more waste than Country B. One-tailed framing reflects the a priori research hypothesis.

**Step 5 — Correlation Analysis**  
Pearson correlation between event attendance and waste volume, with t-test significance check for Country A. Identifies whether awareness programs are a viable policy lever.

---

## Key Findings

### 1. Country A has the highest and most uniform waste levels

| Country | Mean (kg/person/year) | Std Dev | Coefficient of Variation | Skewness |
|---|---|---|---|---|
| A (No Policy) | **104.84** | 7.47 | 7.1% | -1.40 |
| B (Policy) | 98.47 | 11.00 | 11.2% | -0.01 |
| C (Policy) | 99.24 | 5.00 | 5.0% | — |
| D (Policy) | 98.13 | 4.00 | 4.1% | — |

Country A's mean is approximately 6.4–6.7 kg/person/year higher than every signatory country. More importantly, its low CV (7.1%) and strong negative skew (-1.40) indicate that the majority of the population clusters at high waste levels — this is not a pattern driven by a handful of extreme cases.

![Mean Plastic Waste by Country with 98% Confidence Interval](images/chart1_mean_ci.png)

---

### 2. The difference is statistically confirmed and structural

**98% Confidence Interval for Country A: [103.64 – 106.04 kg]**

The means of Countries B, C, and D all fall well below this range. The difference cannot be attributed to random sampling error.

![Distribution of Plastic Waste by Country](images/chart2_boxplot.png)

The box plot makes the structural difference visible. Country A's distribution is tightly clustered at high values. Country B's spread is wider, suggesting its policy commitment may still be in early-stage adoption. Countries C and D show tight, low distributions consistent with established behavioral norms.

**ANOVA results (all four countries):**

| Source | SS | df | MS | F | p-value |
|---|---|---|---|---|---|
| Between Groups | 6303.62 | 3 | 2101.21 | 38.59 | ~2.26e-23 |
| Within Groups | 45959.42 | 844 | 54.45 | | |

F = 38.59 >> F-critical = 2.615. p-value ≈ 0. H₀ rejected: at least one country is a clear outlier.

**Z-test: Country A vs. Country B**

| Parameter | Value |
|---|---|
| z-statistic | 6.87 |
| Critical value (α = 0.05, one-tailed) | 1.28 |
| Result | Reject H₀ |

z = 6.87 is far into the rejection zone. Country A generates statistically more waste than Country B. This is not coincidence.

---

### 3. Awareness participation reduces waste generation

![Correlation: Awareness Events vs. Plastic Waste](images/chart3_correlation.png)

| Country | Correlation (r) | Interpretation |
|---|---|---|
| A | -0.2203 | Moderate inverse relationship |
| B | -0.6527 | Strong inverse relationship |
| C | -0.3883 | Moderate inverse relationship |
| D | -0.3832 | Moderate inverse relationship |

All four countries show a negative correlation. For Country A, the relationship was confirmed statistically significant at the 1% level (t = -3.27, critical value = -2.358). People who attend more environmental events in Country A generate measurably less waste — even in the absence of a binding policy framework.

The stronger correlation in Country B (r = -0.65) compared to Country A (r = -0.22) suggests that awareness programs are amplified when a policy environment already exists. Policy and behavior change are complementary, not competing strategies.

---

## Synthesis

The three findings converge on a consistent interpretation:

Country A's waste problem is structural. Its population is homogeneously high-waste (low variance, negative skew), which means the gap with other countries reflects systemic conditions — not individual outliers or measurement noise. The most likely driver is the absence of a binding policy commitment, which in other countries appears to establish a behavioral floor across the population.

Awareness programs work, but their effect is moderated by policy context. Country B achieves a much stronger awareness-to-waste reduction ratio than Country A, suggesting that when policy gives people a framework, behavioral interventions become more effective.

---

## Recommendations

**1. Prioritize bringing Country A into the international agreement.**  
The statistical evidence is unambiguous and consistent across every method applied. Country A is the only non-signatory in the group and shows the worst performance on every metric. Policy engagement should be treated as the highest-leverage intervention available.

**2. Deploy awareness programs in Country A immediately, without waiting for policy.**  
Even with a weaker effect size than in policy countries, the correlation in Country A is statistically significant. Practical community events (beach cleanups, recycling workshops, public education campaigns) can reduce waste now and lay the groundwork for stronger impact once a policy framework is in place.

**3. Investigate Country B's higher variance.**  
Countries C and D maintain tight, low-waste distributions, suggesting effective and consistent implementation. Country B's higher standard deviation (SD = 11.00 vs. 4–5 for C and D) indicates uneven adoption. UNEP should examine whether implementation differs by region, income group, or urban/rural status within Country B — the findings could produce a replicable model for Country A.

**4. Track awareness participation as a leading indicator.**  
Waste measurement is lagging by nature — it captures behavior after the fact. Event attendance is observable in real time and is correlated with future waste reduction. UNEP should instrument this metric for ongoing monitoring across all countries.

**5. Anchor reduction targets to distribution shape, not just mean.**  
Country A's negative skew means the median waste level is already near the top of other countries' distributions. Mean-based targets will understate the required reduction. Targets set at the 75th or 90th percentile of the within-country distribution would better reflect the scale of behavioral change needed.

---

## Areas for Further Investigation

- Evaluate whether specific policy types (bans, taxes, incentive schemes) produce different effect sizes on per-capita waste
- Add demographic segmentation (age, income, urban/rural) to identify which population segments drive the Country A gap
- Measure the long-term impact of awareness programs — does the effect decay, sustain, or compound over time?
- Assess infrastructure variables (recycling access, waste collection quality) as potential confounders in the policy-waste relationship
- Replicate the correlation analysis with event quality metrics, not just attendance count, to determine whether program design matters

---

## Statistical Limitations

The analysis is based on survey self-report data, which may introduce under-reporting bias for waste and over-reporting bias for event attendance. The frequency table format means individual-level data was partially aggregated before some calculations, reducing precision.

Causality cannot be established from cross-sectional data alone. The z-test confirms the Country A gap is not due to chance, but does not rule out confounders correlated with both policy adoption and waste behavior (e.g., economic development level, infrastructure quality, cultural factors).

The correlation results show association, not causation. Reverse causality is plausible: lower-waste individuals may self-select into awareness events rather than events causing lower waste. Longitudinal data would help resolve this.

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
