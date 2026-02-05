# A/B Test: Impact of Gate Placement on Player Retention (Cookie Cats)

## Overview
This project analyses the results of a randomised A/B experiment conducted in the mobile game *Cookie Cats*.  
The goal is to evaluate whether moving the first progression gate from level 30 (control) to level 40 (treatment) improves player retention and engagement.

The analysis follows an end-to-end experimentation workflow:
- SQL for data cleaning and validation
- Python for statistical testing and inference
- Tableau for decision-focused visualisation

---

## Experiment Design
- **Control group:** Gate at level 30 (`gate_30`)
- **Treatment group:** Gate at level 40 (`gate_40`)
- **Unit of analysis:** Individual user
- **Sample size:** ~90,000 users, evenly split

Users were randomly assigned to control or treatment, enabling causal inference.

---

## Metrics
### Primary Metric
- **7-day retention rate**  
  Proportion of users returning to the game within 7 days

### Secondary Metrics
- **1-day retention rate**
- **Average number of game rounds played**

---

## Methodology
### Data Preparation (SQL)
- Imported raw data into SQLite
- Validated experiment groups and sample balance
- Converted boolean retention indicators to numeric (0/1)
- Deduplicated users and enforced one row per user
- Exported an analysis-ready dataset

### Statistical Analysis (Python)
- Two-proportion z-test for retention metrics
- Welch’s t-test for engagement
- Computed effect sizes and confidence intervals
- Explicit distinction between statistical and practical significance

### Visualisation (Tableau)
- Built an interactive dashboard highlighting:
  - Primary metric
  - Guardrails
  - Engagement depth
- Scaled axes transparently to surface small but meaningful differences
- Included a clear ship / no-ship recommendation

---

## Results Summary
| Metric | Control | Treatment | Uplift |
|------|--------|-----------|--------|
| 7-day retention | ~19.0% | ~18.2% | **−0.82 pp** |
| 1-day retention | ~44.8% | ~44.2% | −0.59 pp |
| Avg. game rounds | ~52.5 | ~51.3 | −1.16 |

- The treatment group underperformed across all metrics
- The decline in 7-day retention was statistically significant
- Engagement showed a negative trend but was not statistically significant

---

## Recommendation
**Do not ship** the new gate placement at level 40.

The treatment leads to a statistically significant reduction in long-term retention, with no compensating gains in engagement. Further iteration or alternative progression designs should be tested before rollout.

---

## Dashboard
🔗 **Interactive Tableau dashboard:**  
[[Link to Tableau Public dashboard]](https://public.tableau.com/views/ABTestforthegameCookieCats/ABTestImpactofGatePlacementonPlayerRetentionintheGameCookieCats?:language=en-GB&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)


---

## Tools & Technologies
- SQL (SQLite)
- Python (pandas, numpy, scipy, statsmodels)
- Tableau
- Jupyter Notebook

