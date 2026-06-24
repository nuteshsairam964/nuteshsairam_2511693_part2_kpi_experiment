# nuteshsairam_2511693_part2_kpi_experiment

## Business Problem Statement

The company introduced a new onboarding and activation campaign to improve user engagement and paid conversion. Users were randomly assigned to either the Control group (existing onboarding experience) or the Treatment group (new onboarding experience).

The key business decision is whether the new onboarding campaign should be launched to all users.

This decision impacts product, marketing, and revenue teams because it affects user acquisition efficiency, conversion performance, and customer experience.

The primary metric expected to improve is Paid Conversion Rate.

Before making a recommendation, we must evaluate whether the Treatment group demonstrates a meaningful improvement in conversion while ensuring that guardrail metrics such as refund rate, support ticket rate, and engagement score do not deteriorate.

Data Quality Check:
- Checked dataset for duplicate user IDs.
- Found 8 duplicate user IDs and removed them using Excel's Remove Duplicates feature.
- Final dataset contains 1400 unique users.
- No major data quality issues impacting analysis were observed after cleaning.

## North Star Metric

### Selected Metric

Paid Conversion Rate

### Definition

Paid Conversion Rate = Number of users converted to paid / Total users

### Why this is the North Star Metric

Paid Conversion Rate directly measures the effectiveness of the onboarding campaign in generating paying customers.

### Why other metrics are supporting metrics

Landing page visits, trial starts, onboarding completion, engagement score, and revenue are important indicators, but they ultimately contribute toward paid conversion.

### Connection to Business Growth

An increase in paid conversion directly increases revenue and customer acquisition efficiency.

### Risk of Optimizing Blindly

If only conversion is optimized, the company may experience higher refunds, increased support tickets, or lower user satisfaction. Therefore, guardrail metrics must also be monitored.



## Data Quality Findings

### Missing Values Analysis

The dataset was checked for missing values across all columns.

| Column               | Missing Values |
| -------------------- | -------------- |
| user_id              | 0              |
| experiment_group     | 0              |
| region               | 0              |
| device_type          | 18             |
| traffic_source       | 24             |
| plan_type            | 0              |
| visited_landing_page | 0              |
| started_trial        | 0              |
| completed_onboarding | 0              |
| converted_to_paid    | 0              |
| revenue_30d          | 0              |
| support_tickets_30d  | 0              |
| refund_requested     | 0              |
| days_to_convert      | 1336           |
| engagement_score     | 14             |

### Group Distribution Check

The experiment groups were validated to ensure proper distribution.

| Group     | User Count |
| --------- | ---------- |
| Control   | 693        |
| Treatment | 715        |

The experiment groups are reasonably balanced and suitable for comparison.

### Duplicate User ID Check

A duplicate user ID assessment was performed.

| Check              | Result |
| ------------------ | ------ |
| Duplicate User IDs | 7      |

A total of 7 duplicate user records were identified. These records should be reviewed before finalizing business recommendations to avoid double-counting users.

### Invalid Binary Value Check

Binary fields were checked to ensure they contain only valid values (0 or 1).

| Column               | Invalid Values |
| -------------------- | -------------- |
| visited_landing_page | 0              |
| started_trial        | 0              |
| completed_onboarding | 0              |
| converted_to_paid    | 0              |
| refund_requested     | 0              |

No invalid binary values were detected.

### Revenue Outlier Assessment

A revenue outlier review was performed using a revenue distribution chart.

Several high-value revenue observations were identified. These values appear to be legitimate business outcomes rather than data entry errors and will be monitored during experiment analysis.

### Data Quality Summary

* 18 missing values found in device_type.
* 24 missing values found in traffic_source.
* 14 missing values found in engagement_score.
* 1336 missing values found in days_to_convert, which is expected for users who never converted.
* 7 duplicate user IDs identified.
* No invalid binary values detected.
* Revenue distribution contains outliers requiring monitoring during analysis.

### Data Cleaning Decision

The dataset was retained for further analysis. Missing values in segmentation fields will be treated as "Unknown" where necessary. Missing days_to_convert values were preserved because they represent users who did not convert rather than data quality issues.
