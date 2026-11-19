# ML Problem-Framing Memo — Customer Churn

## Decision to support
Prioritize customers for a human-reviewed retention outreach campaign. The model is a decision-support tool only; it must not automatically cancel, restrict, or change a customer's service.

## Prediction target
`churned` (1 = churned, 0 = retained), as provided in the training CSV.

## Unit of observation
One customer row in the supplied training dataset. `customer_id` is an identifier and must not be used as a predictive feature.

## Prediction/action window
The dataset does not document when features were measured relative to churn or the prediction horizon. For a real deployment, define a fixed snapshot date and predict churn within a clearly specified future window (for example, the next 30 days) before training. This example cannot validate such a horizon.

## Features available in the supplied file
- `tenure_months`
- `support_tickets`
- `monthly_spend_inr`
- `last_login_days`
- `plan_type`

## Non-ML baseline
Use a simple rule or majority-class baseline first. A practical initial rule for exploration could be to review customers with recent inactivity and/or multiple support tickets. The threshold must be chosen with business owners and evaluated; it is not established by this tiny sample. The notebook also compares a majority-class DummyClassifier.

## Intended use
Learning exercise and offline demonstration using the supplied small sample. It is not approved for production decisions or individual customer treatment.

## Error costs
- False positive (predict churn for a customer who stays): unnecessary outreach and possible annoyance/cost.
- False negative (miss a customer who churns): missed retention opportunity.
The business should decide the relative cost of these errors before setting a threshold.

## Metrics
Report confusion matrix, precision, recall, F1, and accuracy alongside the majority baseline. For retention outreach, recall may matter, but precision and outreach capacity also matter. Do not select a metric/threshold without stakeholder input.

## Human review and safeguards
- Keep outreach decisions human-reviewed.
- Allow the model to abstain when confidence is low.
- Monitor drift and subgroup performance if relevant, using lawful and appropriate data.
- Stop use and revert to the manual baseline if performance or data quality degrades.
- Do not use sensitive attributes or customer identifiers.

## Limitations
The dataset has only 12 rows, no documented provenance/consent, no timestamps or prediction horizon, and no subgroup/fairness fields. Metrics from this dataset are highly unstable and cannot establish generalization.
