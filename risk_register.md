# Risk Register — Customer Churn Baseline

| Risk | Impact | Mitigation / control | Monitoring / rollback trigger |
|---|---|---|---|
| Very small sample (12 rows) | Unstable model and metrics | Collect larger, representative historical dataset; validate on later time period | Do not deploy; keep manual baseline |
| Unknown data provenance and consent | Privacy/compliance uncertainty | Document source, lawful basis, consent/notice, retention and access controls | Block use until provenance review is complete |
| Target leakage / unclear label timing | Inflated performance | Define feature snapshot and future churn window; exclude post-outcome fields | Rebuild if timing cannot be verified |
| Identifier leakage | Memorization | Drop `customer_id` from features | Audit feature list before training |
| False positives | Unnecessary outreach/annoyance | Human review; threshold based on outreach capacity and costs | Reduce outreach or revert if complaint rate rises |
| False negatives | Missed retention opportunity | Review recall and costs; test alternative thresholds | Reassess policy if churn misses increase |
| Distribution drift | Model becomes less accurate | Monitor feature and outcome distributions over time | Suspend predictions if drift/performance breaches agreed limits |
| Unequal performance across groups | Unfair service | Evaluate appropriate groups only where lawful, ethical, and adequately sized | Do not deploy if material disparities cannot be mitigated |
| Automation overreach | Customers treated adversely without explanation | Model is advisory; no automated service restrictions | Stop automated action; retain human decision |
