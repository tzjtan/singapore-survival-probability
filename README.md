# Singapore Survival Probability Visualization

Interactive visualization of survival probabilities using Singapore's mortality data. Understand the statistical likelihood of reaching various ages—a perspective often missing from retirement planning.

**[View site →](https://tzjtan.github.io/singapore-survival-probability/)**

## Why This Matters

Retirement planning fixates on money while ignoring a fundamental truth that life is ephemeral. Knowing the life expectancy of 83.5 years is not enough information (*so what, I drop dead at 83.5?*). Knowing the mortality rates is also not helpful (*ok, so I have a 0.3% chance of dying in the next year but then what?*). For long-term planning, it is essential to convert the figures into another form.

Do you know that you (assuming average Singaporean) have a 95% chance of surviving 59 years old, a 80% chance of surviving 75 years old and 50% chance of surviving 84 years old? I think that would be more helpful information to look ahead into one's life.

## Mathematics

**Survival Probability**: Cumulative probability of surviving from birth to age *x*.

Given mortality rate *m(a)* per 1,000 at age *a*:
- Survival rate: `s(a) = 1 - m(a)/1000`
- Cumulative probability: `P(x) = ∏[a=0 to x] s(a)`

**Example**: 5 per 1,000 mortality at age 60 → 0.995 survival rate. If P(59) = 0.90, then P(60) = 0.90 × 0.995 = 0.8955 (89.55%).

**Reference Lines**:
- **LE at Birth**: Average years a newborn is expected to live
- **LE at 65**: Average remaining years from age 65
- **HALE**: Health-adjusted life expentancy, the years lived in full health (Global Burden of Disease methodology)

The official data for the mortality is grouped each 5-year age group. This causes the survival probability graph to be too jagged. A linear interpolation is done by looking at the mortality at the previous age to see how the mortalities per age in the next 5-year age group should be distributed while retaining the average mortality in the age group to be equal to the official figure.

## Data Sources

From data.gov.sg:

1. **Mortality Rates** ([`d_0d64da52342e43d864bc84898ba6835f`](https://data.gov.sg/datasets?resultId=d_0d64da52342e43d864bc84898ba6835f)) - 1960s to present, by age and gender
2. **HALE** ([`d_c93fe829a88716926223b5ad472e6044`](https://data.gov.sg/datasets?resultId=d_c93fe829a88716926223b5ad472e6044)) - 1990-2021, by gender
3. **Life Expectancy** ([`d_af61b90018b8fabecabe8e93950e0223`](https://data.gov.sg/datasets?resultId=d_af61b90018b8fabecabe8e93950e0223)) - 1960s to present, at birth and age 65

Live data with embedded fallback. Earlier years have coarser age breakdowns (70+).


