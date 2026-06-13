# Reporting

Goal: make fast decisions by keeping metrics, owners, and escalation paths explicit.

## Decision Loops

- [ ] List recurring decisions that are slow, ambiguous, or escalation-heavy.
- [ ] Define decision owner and backup owner.
- [ ] Define input metrics, source systems, and freshness expectations.
- [ ] Define decision cadence: real-time, daily, weekly, monthly, quarterly.
- [ ] Define what evidence is enough to decide.

## Metric Model

- [ ] Map company, product, customer, operational, and engineering metrics.
- [ ] Assign owner per metric.
- [ ] Document source of truth and query/report link.
- [ ] Define metric contract: definition, grain, filters, exclusions, latency.
- [ ] Add data quality checks for critical metrics.

## AI Support

- [ ] Identify reports where AI can summarize movement, anomalies, risks, or next actions.
- [ ] Require source links for generated summaries.
- [ ] Separate facts, interpretation, and recommendation.
- [ ] Add confidence or freshness warning when source data is incomplete.
- [ ] Keep generated decisions reviewable by owner.

## Verify

- [ ] Compare AI summary with source dashboard or query.
- [ ] Test missing data, stale data, and contradictory signals.
- [ ] Attach proof artifact: dashboard link, query result, summary diff, or decision log.

## Operate

- [ ] Review decision cycle time.
- [ ] Track decisions reversed because source data or interpretation was wrong.
- [ ] Remove reports that do not change decisions.
- [ ] Keep executive view short and source-backed.

