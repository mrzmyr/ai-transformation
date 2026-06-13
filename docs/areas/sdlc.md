# SDLC

Goal: make AI readiness visible per repo across the full software delivery lifecycle.

## Feature

### Spec

- [ ] Use planning mode for non-trivial changes.
- [ ] Use service ownership from Backstage, GitHub, or CODEOWNERS.
- [ ] Use service dependencies from Backstage or architecture docs.
- [ ] Use API schemas and async contracts from source systems.
- [ ] Use scaffolding for cloud resources.
- [ ] Use tech radar or agreed platform standards.
- [ ] Use code context from repository, `constitution.md`, and `AGENTS.md`.
- [ ] Use customer requests from Linear, Zendesk, or support channels.
- [ ] Use design context from Figma.
- [ ] Use company data and product analytics when relevant.
- [ ] Use incidents, auth config, architecture decisions, roadmap, and IaC when relevant.
- [ ] Define definition of done.
- [ ] Define metrics, errors, unit tests, and acceptance checks.

### Develop

- [ ] Use LLM coding tools with repo context.
- [ ] Use cloud agents for isolated work when useful.
- [ ] Use feature flags.
- [ ] Use CI.
- [ ] Use preview deployments.
- [ ] Use pre-commit hooks for lint, format, and typecheck.
- [ ] Keep prompt, eval, and generated-code assumptions visible in commits or PR notes.

### Verify

- [ ] Model must prove the solution with artifacts.
- [ ] Use unit, integration, or e2e tests.
- [ ] Use screenshots or before/after video for UI changes.
- [ ] Use AI PR reviews where available.
- [ ] Use security analysis where relevant.
- [ ] Use staging data safely.
- [ ] Use device tests for frontend and mobile surfaces.

### Ship

- [ ] Use deployments through approved systems.
- [ ] Use logs during rollout.
- [ ] Use release PRs, semver, and changelog where applicable.
- [ ] Use IaC for infrastructure changes.
- [ ] Define rollback path.
- [ ] Confirm feature flag, alerting, and owner before broad rollout.

### Operate

- [ ] Use logs.
- [ ] Use alerts.
- [ ] Use dashboards.
- [ ] Use SLOs.
- [ ] Use incidents and on-call schedules.
- [ ] Use cost monitoring.
- [ ] Review AI-related quality, latency, cost, and failure patterns.

### Measure

- [ ] Use logs and product analytics.
- [ ] Compare intended metric with actual movement.
- [ ] Track adoption and user correction signals.
- [ ] Feed learnings back into specs, evals, and prompts.

## Fix

### Spec

- [ ] Define expected behavior.
- [ ] Define actual behavior.
- [ ] Use security scans where relevant.
- [ ] Use logs.
- [ ] Use screenshots.
- [ ] Identify blast radius and affected users.

### Reproduce

- [ ] Use logs.
- [ ] Use preview deployments or staging.
- [ ] Use device tests where relevant.
- [ ] Capture minimal reproduction.

### Develop

- [ ] Create focused fix.
- [ ] Add regression test.
- [ ] Avoid unrelated refactors.
- [ ] Document changed assumption if AI-generated code caused or influenced the bug.

### Verify

- [ ] Prove expected behavior now holds.
- [ ] Prove actual broken behavior is gone.
- [ ] Prove no adjacent regression in critical path.
- [ ] Attach proof artifact.

### Ship

- [ ] Deploy through approved path.
- [ ] Monitor logs and alerts.
- [ ] Update incident, ticket, or release note.

