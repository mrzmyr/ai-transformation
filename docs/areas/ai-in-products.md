# AI in Products

Goal: identify where AI should become part of the product experience, then turn that into safe, measurable product work.

## Discovery

- [ ] List customer jobs where AI can reduce effort, increase quality, or create a new capability.
- [ ] Identify existing product surfaces where AI output can be reviewed before action.
- [ ] Map user trust requirements per surface.
- [ ] Define data inputs, data boundaries, and retention rules.
- [ ] Decide whether capability is recommendation, generation, classification, retrieval, agent action, or automation.

## Spec

- [ ] Define expected user outcome.
- [ ] Define failure modes and fallback behavior.
- [ ] Define human review point for high-risk actions.
- [ ] Define eval set from real user scenarios.
- [ ] Define product metric and guardrail metric.

## Build

- [ ] Choose model/provider/runtime.
- [ ] Add prompt, tool, retrieval, and output contracts to version control.
- [ ] Add structured output validation.
- [ ] Add telemetry for input class, output class, latency, cost, and errors.
- [ ] Add feature flag and rollout controls.

## Verify

- [ ] Run eval set before release.
- [ ] Test unsafe, ambiguous, low-context, and adversarial inputs.
- [ ] Verify logs do not expose sensitive data.
- [ ] Verify user can understand, accept, reject, or correct AI output.
- [ ] Attach proof artifact: eval report, screenshots, test logs, or rollout notes.

## Ship

- [ ] Start with narrow cohort or internal dogfood.
- [ ] Monitor quality, latency, cost, user edits, and opt-out signals.
- [ ] Add rollback path.
- [ ] Add owner for prompt/eval maintenance.

