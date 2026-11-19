# Responsible Data Card — Customer Churn Training Data

## Dataset identity
Filename: `customer-churn-training.csv`  
Rows: 12 customers (records)  
Columns: 7  
Missing values: none detected in this supplied file.

## Provenance, collection, and consent
The provided file contains no source/provenance, collection method, consent, or licensing documentation. These details are unknown and must be verified with the data provider before any real-world use.

## Fields
- `customer_id`: customer identifier; exclude from model features.
- `tenure_months`: customer tenure in months.
- `support_tickets`: ticket count.
- `monthly_spend_inr`: monthly spend in INR.
- `last_login_days`: days since last login.
- `plan_type`: Basic / Standard / Pro plan.
- `churned`: label (1/0); meaning is inferred from field name and should be confirmed with the provider.

## Intended use
Educational, offline baseline model demonstration only. The sample is too small for operational customer targeting.

## Sensitive attributes
No explicit sensitive demographic attributes appear in the supplied columns. This does not prove the data is non-sensitive; customer-level records and identifiers can still be personal data.

## Quality and limitations
- Only 12 rows, so statistical results are highly unstable.
- No missing values in this sample.
- No timestamps or documented label window.
- No description of sampling, representativeness, or class-label quality.
- Feature definitions/measurement timing are not documented.
- `customer_id` is an identifier and should not be used as a feature.
- The churn label semantics and timeframe need confirmation.

## Risks
Potential privacy risk, unknown consent/provenance, leakage due to unclear temporal definition, false positives/false negatives, poor generalization, and fairness concerns that cannot be assessed with the available sample.

## Access and retention
Access should be restricted to authorized project users. Retention and deletion schedule are not specified; document these before any deployment.

## Required follow-up
Confirm provenance, lawful basis/consent, definitions, feature timing, label window, sampling strategy, and appropriate retention policy.
