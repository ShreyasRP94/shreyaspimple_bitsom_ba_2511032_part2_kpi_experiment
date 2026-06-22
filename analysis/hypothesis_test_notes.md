# Hypothesis Test Notes

## Business Context

The company introduced a new onboarding and activation campaign to improve the percentage of users converting to paid subscriptions. An A/B experiment was conducted in which:

* Control Group: Existing onboarding experience
* Treatment Group: New onboarding and activation campaign

The business objective is to determine whether the new campaign should be rolled out to all users.

---

## Metric Being Tested

**Paid Conversion Rate**

Formula:

Paid Conversion Rate = Number of users converted to paid / Total number of users

This metric was selected because it is the North Star Metric of the experiment and directly represents the company's subscription growth objective.

---

## Null Hypothesis (H0)

The new onboarding campaign does not improve paid conversion.

Mathematically:

H0: Paid Conversion Rate (Treatment) ≤ Paid Conversion Rate (Control)

or

H0: pT ≤ pC

where:

* pT = Paid Conversion Rate of Treatment Group
* pC = Paid Conversion Rate of Control Group

---

## Alternate Hypothesis (H1)

The new onboarding campaign improves paid conversion.

Mathematically:

H1: Paid Conversion Rate (Treatment) > Paid Conversion Rate (Control)

or

H1: pT > pC

---

## Type of Test

**One-tailed hypothesis test**

Reason:

The business objective is specifically to determine whether the treatment performs better than the existing onboarding experience.

The experiment is not interested in proving that the treatment is simply different; it needs evidence that the treatment produces a higher conversion rate.

Therefore, a one-tailed test is appropriate.

---

## Significance Level

**α = 0.05 (5%)**

Decision Rule:

* If p-value < 0.05:
  Reject the Null Hypothesis.

* If p-value ≥ 0.05:
  Fail to Reject the Null Hypothesis.

This significance level is commonly used in business experiments and provides a reasonable balance between confidence and business risk.

---

## Reason for Choosing Paid Conversion Rate

Paid Conversion Rate was chosen because:

1. It directly measures business growth.
2. The company operates on a subscription model where revenue depends on converting users to paid customers.
3. It represents the final outcome of the onboarding funnel.
4. Improvements in this metric have a direct impact on revenue and profitability.

Supporting metrics such as Trial Start Rate, Onboarding Completion Rate, and Engagement Score help explain user behavior but do not replace the final business outcome.

---

## Interpretation Logic

After performing the statistical test:

### Scenario 1: p-value < 0.05

The improvement in Paid Conversion Rate is statistically significant.

Conclusion:

* Reject H0
* Accept H1
* The treatment campaign performs better than the control group.
* Recommend considering a full rollout, subject to guardrail metrics remaining healthy.

---

### Scenario 2: p-value ≥ 0.05

The observed difference may be due to random variation.

Conclusion:

* Fail to Reject H0
* There is insufficient evidence that the new onboarding campaign improves paid conversion.
* Do not recommend a full rollout without additional experimentation.

---

## Connection to Business Decision

The outcome of this hypothesis test directly supports the business decision:

**Should the new onboarding and activation campaign be launched to all users?**

If the treatment significantly improves Paid Conversion Rate without negatively affecting guardrail metrics such as Refund Rate, Support Tickets, and User Engagement, the company can confidently proceed with a full rollout.


## Test Inputs

| Metric               | Control | Treatment |
| -------------------- | ------: | --------: |
| Total Users          |     693 |       715 |
| Paid Conversions     |      22 |        50 |
| Paid Conversion Rate |   3.17% |     6.99% |

Additional Test Statistics:

| Statistic                     |    Value |
| ----------------------------- | -------: |
| Difference in Conversion Rate |    3.82% |
| Pooled Conversion Rate        |    5.11% |
| Standard Error                |  0.01174 |
| Z Score                       |   3.2519 |
| One-tailed P-value            | 0.000573 |

---

## Test Result

The calculated p-value is:

**0.000573**

Since:

**0.000573 < 0.05**

the Null Hypothesis is rejected.

---

## Statistical Conclusion

There is statistically significant evidence that the Treatment group achieved a higher Paid Conversion Rate than the Control group.

The observed improvement is unlikely to be caused by random chance.

---

## Business Interpretation

The new onboarding and activation campaign increased the Paid Conversion Rate from:

* Control Group: **3.17%**
* Treatment Group: **6.99%**

This represents an absolute improvement of:

**3.82 percentage points**

and more than doubles the conversion performance compared to the existing onboarding experience.

Because the result is statistically significant and demonstrates a meaningful business improvement, the Treatment campaign shows strong potential for full deployment.

---

## Recommendation

Based on the A/B test results, the Treatment group significantly outperformed the Control group in terms of Paid Conversion Rate.

Therefore:

**Recommend proceeding with a broader rollout of the new onboarding campaign**, provided that guardrail metrics such as Refund Rate, Support Ticket Rate, and User Engagement remain within acceptable business thresholds.
