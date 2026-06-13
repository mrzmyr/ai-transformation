# AI Readiness Checklist

Date: 2026-06-13

Basis: original top 30 public `steipete` repos by stars, plus expanded scan of active public repos for newer agent, CI, SECURITY, PR, and service patterns. The extraction notes and top-30 evidence table live in [`research/steipete-top30.md`](research/steipete-top30.md).

Goal: one canonical checklist that can later become an automated repo-readiness test. Detailed examples live in linked Markdown files, not in this checklist.

Status labels:

- `REQUIRED`: every active repo.
- `SERVICE`: web server, TypeScript backend, worker, API, or deployed service.
- `OSS`: public/open-contribution repo.
- `IF_APPLICABLE`: required only when that surface exists.
- `MATURE`: useful for larger or high-risk repos, not baseline.

## Checklist

- [ ] `REPO_PURPOSE` `REQUIRED`: `README.md` defines product purpose, install path, user-facing usage, and dev quick start. [Details](details/01-repo-contract.md#repo_purpose)
- [ ] `FILE_CONTRACT` `REQUIRED`: Repo has one documented place for each concern: agent rules, contributing, security, testing, release, generated files. [Details](details/01-repo-contract.md#file_contract)
- [ ] `AGENT_ENTRYPOINT` `REQUIRED`: root `AGENTS.md` defines exact agent operating rules, repo map, commands, verification, and safety caveats. [Details](details/01-repo-contract.md#agent_entrypoint)
- [ ] `SHARED_RULES_BOUNDARY` `IF_APPLICABLE`: shared rules are in a clearly delimited generated block; repo-local rules stay outside that block. [Details](details/01-repo-contract.md#shared_rules_boundary)
- [ ] `MAINTENANCE_STATE` `IF_APPLICABLE`: archived or maintenance-only repos state support status, accepted change types, and replacement project. [Details](details/01-repo-contract.md#maintenance_state)

- [ ] `RUNTIME_TOOLING` `REQUIRED`: repo pins or documents runtime, package manager, install command, and lockfile policy. [Details](details/02-runtime-service.md#runtime_tooling)
- [ ] `CHECK_SCRIPT` `REQUIRED`: primary green gate is named `check` and runs format check, lint/static analysis, typecheck/build, and tests. [Details](details/03-verification.md#check_script)
- [ ] `CI_CHECK` `REQUIRED`: CI runs the same `check` command or a documented strict superset. [Details](details/03-verification.md#ci_check)
- [ ] `FOCUSED_COMMANDS` `REQUIRED`: docs list focused commands for common change surfaces, but still require `check` before handoff. [Details](details/03-verification.md#focused_commands)
- [ ] `VERIFICATION_MATRIX` `REQUIRED`: `AGENTS.md` maps change type to required proof and exact commands. [Details](details/03-verification.md#verification_matrix)
- [ ] `TEST_STRATEGY` `REQUIRED`: `docs/testing.md` or `AGENTS.md` defines test types, fixture locations, naming pattern, and live-test gates. [Details](details/03-verification.md#test_strategy)

- [ ] `SERVICE_BOUNDARIES` `SERVICE`: backend layout separates routes/controllers, services, repositories, clients, workers, and generated code. [Details](details/02-runtime-service.md#service_boundaries)
- [ ] `LOCAL_DEV_LOOP` `SERVICE`: docs define commands to start dependencies, run server/worker, stop services, and verify health. [Details](details/02-runtime-service.md#local_dev_loop)
- [ ] `CONFIG_ENV_CONTRACT` `SERVICE`: docs define required env vars, `.env.example`, config defaults, secret sources, and local-vs-production behavior. [Details](details/02-runtime-service.md#config_env_contract)
- [ ] `DATABASE_MIGRATIONS` `SERVICE IF_APPLICABLE`: schema changes have migration commands, validation commands, rollback/forward policy, and test database guidance. [Details](details/02-runtime-service.md#database_migrations)
- [ ] `HEALTHCHECK_SMOKE` `SERVICE`: deployed or local services expose health/readiness smoke commands suitable for CI or handoff proof. [Details](details/02-runtime-service.md#healthcheck_smoke)
- [ ] `MACHINE_INTERFACE` `IF_APPLICABLE`: CLIs and service tools expose stable `--json`, `--plain`, status, exit codes, or health endpoints. [Details](details/02-runtime-service.md#machine_interface)

- [ ] `SECURITY_POLICY` `REQUIRED`: `SECURITY.md` defines private vulnerability reporting, supported versions, scope, expectations, and confidentiality. [Details](details/04-security-live-systems.md#security_policy)
- [ ] `SECRET_HANDLING` `REQUIRED`: agent rules forbid secret logging, broad env dumps, unredacted auth headers, cookies, and private payloads. [Details](details/04-security-live-systems.md#secret_handling)
- [ ] `LIVE_SYSTEM_GATES` `REQUIRED`: normal checks avoid live accounts; live tests require explicit opt-in env vars and user approval. [Details](details/04-security-live-systems.md#live_system_gates)
- [ ] `AI_PROVIDER_PREFLIGHT` `IF_APPLICABLE`: paid or external AI/provider calls have dry-run/preflight/doctor commands and redacted diagnostics. [Details](details/04-security-live-systems.md#ai_provider_preflight)

- [ ] `PR_PROOF` `OSS`: PR template requires what changed, why, exact verification commands, docs/changelog decision, and reviewer notes. [Details](details/05-github-workflow.md#pr_proof)
- [ ] `ISSUE_INTAKE` `OSS`: issue templates require exact repro, version, platform, expected vs actual, and redacted logs. [Details](details/05-github-workflow.md#issue_intake)
- [ ] `DEPENDENCY_GOVERNANCE` `OSS MATURE`: dependency update policy and Dependabot config define ecosystems, cadence, grouping, and PR limits. [Details](details/05-github-workflow.md#dependency_governance)
- [ ] `CODEOWNERS` `OSS MATURE`: active public repos define default review ownership. [Details](details/05-github-workflow.md#codeowners)

- [ ] `GENERATED_ARTIFACTS` `IF_APPLICABLE`: generated files are listed with source-of-truth inputs, regeneration command, and "do not hand edit" rule. [Details](details/06-delivery-maintenance.md#generated_artifacts)
- [ ] `RELEASE_DELIVERY` `IF_APPLICABLE`: release docs define version bumps, artifact/package publish, deploy, smoke proof, and failure handling. [Details](details/06-delivery-maintenance.md#release_delivery)
- [ ] `CHANGELOG_POLICY` `IF_APPLICABLE`: user-visible changes have a documented changelog rule and location. [Details](details/06-delivery-maintenance.md#changelog_policy)
- [ ] `SECOND_OPINION` `MATURE`: risky changes define when to ask another model/tool, how to dry-run context, and how to cite results. [Details](details/06-delivery-maintenance.md#second_opinion)

## Minimal Baseline

For an active TypeScript backend/service, the non-negotiable subset is:

- `REPO_PURPOSE`
- `FILE_CONTRACT`
- `AGENT_ENTRYPOINT`
- `RUNTIME_TOOLING`
- `CHECK_SCRIPT`
- `CI_CHECK`
- `FOCUSED_COMMANDS`
- `VERIFICATION_MATRIX`
- `TEST_STRATEGY`
- `SERVICE_BOUNDARIES`
- `LOCAL_DEV_LOOP`
- `CONFIG_ENV_CONTRACT`
- `HEALTHCHECK_SMOKE`
- `SECURITY_POLICY`
- `SECRET_HANDLING`
- `LIVE_SYSTEM_GATES`

## Automation Target

This checklist should become a linter that can fail CI. The linter should check file existence, required scripts, CI command parity, required headings, forbidden vague phrases, and explicit live-test gates. Human review remains needed for quality of prose, but structure should be machine-testable.
