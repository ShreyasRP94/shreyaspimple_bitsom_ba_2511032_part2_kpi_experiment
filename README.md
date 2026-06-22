# KPI Framework, Business Experiment Analysis & Decision Recommendation

## Business Problem Statement

The company recently launched a new onboarding and activation campaign designed to improve the user journey from initial signup to becoming an engaged paying customer. Users were randomly assigned to either the Control group, which received the existing onboarding experience, or the Treatment group, which received the new campaign experience.

The key business decision is whether the new onboarding campaign should be rolled out to all users or whether the company should continue using the existing experience.

This decision primarily impacts business leadership, product managers, growth teams, marketing teams, and future users of the platform. A successful rollout could increase customer acquisition efficiency, improve user activation, and generate additional subscription revenue.

The primary metric expected to improve is the conversion rate from user signup to paid subscription. Supporting metrics such as onboarding completion rate, trial start rate, engagement score, and revenue generated should also demonstrate positive performance.

While pursuing higher conversion rates, the company must monitor potential risks through guardrail metrics. These risks include increased customer support burden, higher refund request rates, lower user satisfaction, or reduced engagement quality that could negatively affect long-term business performance.

Before recommending a full rollout, sufficient evidence must demonstrate that the treatment group performs better than the control group on key success metrics and that any observed improvements are statistically significant rather than the result of random variation. Additionally, guardrail metrics should remain stable or improve to ensure the campaign does not create unintended negative consequences.


## North Star Metric

### Selected North Star Metric: Paid Conversion Rate

The North Star Metric for this experiment is **Paid Conversion Rate**, which measures the percentage of users who successfully convert from a new user into a paying subscriber.

### Why Paid Conversion Rate is the Main Success Metric

The primary goal of the onboarding and activation campaign is not simply to increase clicks, visits, or trial registrations. The ultimate objective of a subscription business is to convert users into paying customers who generate revenue for the company. Therefore, Paid Conversion Rate is the most important metric because it directly measures whether the new onboarding experience drives meaningful business outcomes.

An improvement in this metric indicates that the onboarding campaign successfully moves users through the acquisition funnel and creates financial value for the business.

### Why Other Metrics are Supporting Metrics

Several other metrics are important for understanding user behavior, but they are intermediate indicators rather than the final business outcome:

* **Visited Landing Page** measures initial interest but does not guarantee business value.
* **Started Trial** indicates activation intent but users may not become paying customers.
* **Completed Onboarding** shows that users finished the onboarding flow, but completion alone does not generate revenue.
* **Engagement Score** measures user activity and product usage, which supports retention and conversion but is not a direct revenue metric.
* **Revenue in First 30 Days** is important but depends on the number of users who convert, making it a downstream outcome.
* **Support Tickets** and **Refund Requests** are guardrail metrics used to monitor user experience and business risk.

These metrics help explain *why* conversion changes, but they do not replace Paid Conversion Rate as the primary success indicator.

### Connection to Business Growth

Paid Conversion Rate is directly connected to business growth because:

1. Higher conversion increases the number of paying customers.
2. More paying customers generate higher recurring subscription revenue.
3. Improved conversion reduces customer acquisition costs by increasing the return on marketing and onboarding investments.
4. Sustained improvements in conversion contribute to long-term revenue growth and profitability.

Therefore, optimizing Paid Conversion Rate supports both short-term and long-term business objectives.

### Risks of Optimizing This Metric Blindly

Although Paid Conversion Rate is the most important metric, optimizing it without considering other indicators can create unintended consequences.

Potential risks include:

* Aggressive onboarding tactics may pressure users into purchasing, resulting in a higher refund rate.
* Users may convert initially but become dissatisfied, increasing customer support tickets.
* Short-term conversion gains may reduce user trust and negatively impact long-term retention.
* Revenue quality may decline if users convert but do not remain engaged with the product.

For these reasons, Paid Conversion Rate should always be evaluated alongside guardrail metrics such as Refund Request Rate, Support Tickets, and Engagement Score to ensure sustainable business growth.

## Dataset Description

The dataset `campaign_experiment_data.xlsx` contains user-level experiment data for both Control and Treatment groups.

The dataset includes:

	* User ID
	* Experiment Group
	* Landing Page Visit Status
	* Trial Start Status
	* Onboarding Completion Status
	* Paid Conversion Status
	* Revenue in First 30 Days
	* Support Tickets
	* Refund Requests
	* Engagement Score
	* Days to Convert
	* Region
	* Device Type
	* Traffic Source
	* Plan Type

The dataset was used for KPI analysis, A/B testing, guardrail evaluation, and business recommendation.

---


## Data Cleaning and Preparation

The experiment dataset was validated before conducting KPI and A/B test analysis.

### 1. Missing Values

The dataset was checked for missing values across all columns.

* No missing values were found in critical fields such as `user_id`, `experiment_group`, conversion indicators, revenue, support tickets, and refund information.
* Small numbers of missing values were observed in:

  * `device_type`
  * `traffic_source`
  * `engagement_score`
* `days_to_convert` contains a large number of missing values because this metric is only applicable to users who converted to paid subscriptions. Therefore, these missing values were retained and treated as business-expected missingness rather than data quality issues.

### 2. Group Counts

The experiment groups were reasonably balanced:

* Control Group: 693 users
* Treatment Group: 715 users

This balance supports a fair comparison between both groups.

### 3. Duplicate User IDs

A duplicate check was performed on `user_id`.

* A small number of duplicate user IDs were identified.
* These records were documented separately for review and transparency.
* The duplicates were retained in the raw analysis workbook to preserve dataset integrity as provided.

### 4. Binary Variable Validation

The following binary columns were validated:

* visited_landing_page
* started_trial
* completed_onboarding
* converted_to_paid
* refund_requested

All values were valid and restricted to 0 or 1.

### 5. Revenue Outlier Detection

Revenue outliers were identified using the Interquartile Range (IQR) method.

* Q1 and Q3 were calculated.
* Upper and lower bounds were derived using:

  * Lower Bound = Q1 − 1.5 × IQR
  * Upper Bound = Q3 + 1.5 × IQR
* Outlier records were documented separately for transparency.

No outliers were removed because they may represent legitimate high-value customers and are relevant to business performance evaluation.

### 6. Segment Distribution

The distribution of users across:

* Region
* Device Type
* Traffic Source

was compared between Control and Treatment groups.

The distributions were broadly balanced, indicating that the experiment groups are comparable and suitable for A/B testing and business decision-making.


## KPI Tree Summary

The KPI Tree was designed around the North Star Metric: **Paid Conversion Rate**.

### Primary KPI Drivers

1. User Acquisition Quality

   * Landing Page Visit Rate
   * Traffic Quality

2. User Activation Funnel

   * Trial Start Rate
   * Onboarding Completion Rate

3. User Engagement & Retention

   * Engagement Score
   * Revenue in First 30 Days

### Guardrail Metrics

* Refund Rate
* Support Ticket Rate
* Days to Convert

The KPI Tree image is available in:

```text
outputs/kpi_tree.png
```

---

## Experiment Analysis Approach

The experiment dataset was validated and prepared before analysis.

The following checks were performed:

* Missing Value Analysis
* Group Count Validation
* Duplicate User ID Check
* Binary Variable Validation
* Revenue Outlier Detection
* Segment Distribution Analysis

Experiment summaries were created for:

* Overall Performance
* Region-wise Analysis
* Device Type Analysis
* Traffic Source Analysis
* Plan Type Analysis

The summary workbook is available in:

```text
outputs/experiment_summary.xlsx
```

---

## Hypothesis Test Summary

### Primary Metric Tested

Paid Conversion Rate

### Hypotheses

**Null Hypothesis (H0)**

Treatment does not improve Paid Conversion Rate.

```text
H0: pT ≤ pC
```

**Alternative Hypothesis (H1)**

Treatment improves Paid Conversion Rate.

```text
H1: pT > pC
```

### Test Type

One-tailed Z-Test for Difference in Proportions

### Significance Level

```text
α = 0.05
```

### Experiment Results

| Metric               | Control | Treatment |
| -------------------- | ------: | --------: |
| Users                |     693 |       715 |
| Paid Conversions     |      22 |        50 |
| Paid Conversion Rate |   3.17% |     6.99% |

### Test Statistics

| Statistic  |    Value |
| ---------- | -------: |
| Difference |    3.82% |
| Z Score    |   3.2519 |
| P-value    | 0.000573 |

Since:

```text
P-value < 0.05
```

The Null Hypothesis was rejected.

The Treatment group significantly outperformed the Control group.

---

## Guardrail Metrics Considered

The final decision was not based solely on conversion improvement.

The following guardrail metrics were evaluated:

### Refund Rate

The Treatment group did not show a concerning increase in refunds.

**Risk Level:** Low

### Support Ticket Rate

Support activity remained stable.

**Risk Level:** Low

### Days to Convert

The Treatment group converted users efficiently without additional delays.

**Risk Level:** Low

### Engagement Score

User engagement improved under the Treatment experience.

**Risk Level:** Very Low

Overall, no major business risk was identified.

---

## Segment-Level Insights

Performance was analyzed across:

* Region
* Device Type
* Traffic Source
* Plan Type

The Treatment group demonstrated consistent performance improvements across major segments.

No major segment-level decline was observed.

---

## Final Recommendation

### Decision: Launch

The Treatment group demonstrated:

* Higher Paid Conversion Rate (6.99% vs 3.17%)
* Statistically significant improvement
* Stable Refund Rate
* Stable Support Ticket Rate
* Higher Engagement
* Faster conversion efficiency

The evidence supports launching the new onboarding and activation campaign for all users.

---

## Assumptions and Limitations

The following limitations should be considered:

1. The experiment covers a limited observation period.
2. Long-term retention was not evaluated.
3. Revenue analysis is limited to the first 30 days.
4. User behavior may change after full-scale rollout.

Continuous monitoring is recommended after deployment.

---

## Screenshots Included

The repository includes the following screenshots:

* `screenshots/kpi_tree_preview.png`
* `screenshots/summary_metrics.png`
* `screenshots/hypothesis_test_output.png`

These screenshots provide visual evidence of the KPI framework, experiment summary, and statistical test results.

---

## Final Conclusion

**The new onboarding and activation campaign should be launched for all users because it delivers a statistically significant improvement in Paid Conversion Rate while maintaining healthy guardrail metrics and sustainable business performance.**
