# AI Readiness Checklist Extracted From Steipete Top 30 Repos

Date: 2026-06-13

Scope: top 30 public `steipete` repositories by GitHub `stargazers_count`, from GitHub REST API, default branches cloned shallow and scanned locally. "AI readiness" here means: how ready a repo is for an AI coding agent to understand, change, verify, and hand off work safely.

## Topline

- 13/30 repos have agent-readable instructions (`AGENTS.md`, `CLAUDE.md`, or Copilot instructions).
- 16/30 repos have GitHub Actions workflows.
- 12/30 repos have obvious test files.
- 28/30 repos have build manifests or project files.
- Strongest AI-ready patterns show up in active/newer repos: `CodexBar`, `summarize`, `oracle`, `RepoBar`, `Trimmy`, `poltergeist`, `agent-scripts`.
- Most gaps are older archived Objective-C repos. For those, "AI ready" often means clear archival status, build caveats, and low-risk maintenance boundaries rather than modern CI.

## Extracted Checklist

### 1. Agent Entry Point

- [ ] Add root `AGENTS.md` or `CLAUDE.md`.
- [ ] Include project purpose, directory map, package manager/runtime, build/test commands, style rules, PR expectations, release rules, and security caveats.
- [ ] Keep repo-local instructions short, with links to detailed docs.
- [ ] Use shared rules where useful, but keep repo-specific rules outside shared blocks.

Evidence: `CodexBar`, `RepoBar`, `Trimmy`, `summarize`, `oracle`, `agent-scripts`, `poltergeist`.

### 2. One Green Gate

- [ ] Provide one command that agents can run before handoff: `pnpm check`, `make check`, `swift test` plus lint/format, or `go test ./...` plus lint.
- [ ] Make the green gate mirror CI as closely as practical.
- [ ] Include focused commands for faster local iteration.
- [ ] Document which checks are mandatory after code changes.

Evidence: `summarize` uses `format:check`, lint, typecheck, coverage under `pnpm check`; `RepoBar` wraps Swift checks in `pnpm check`; `Trimmy` exposes Swift format/lint/test commands; `CodexBar` has `make check` and `swift test`; `sag` and `tmuxwatch` expose Go build/test/lint scripts.

### 3. Fast Dev Loop

- [ ] Provide scripts that build, package, run, and restart local apps without stale binaries.
- [ ] For UI/menu-bar apps, document exact launch path and how to verify the running binary.
- [ ] Prefer repo scripts over ad-hoc shell commands.
- [ ] Make long-running or brittle validation observable.

Evidence: `CodexBar`, `RepoBar`, and `Trimmy` all document `compile_and_run.sh` or `pnpm start/restart` style loops.

### 4. Testable Architecture

- [ ] Put tests in standard, discoverable folders (`Tests`, `tests`, `__tests__`).
- [ ] Tell agents where to add regression tests.
- [ ] Prefer deterministic fixtures/mocks over live services.
- [ ] For UI or platform-specific behavior, expose model/parser/service layers that can be tested without fragile UI automation.

Evidence: `CodexBar`, `RepoBar`, `Trimmy`, `summarize`, `oracle`, `poltergeist`.

### 5. Verification Proof

- [ ] Require PRs or handoffs to list commands run.
- [ ] Require screenshots/clips for UI changes.
- [ ] Require regression tests for bug fixes when feasible.
- [ ] State when manual proof is acceptable.
- [ ] Define "done" for releases and user-visible fixes.

Evidence: `poltergeist` PR template requires tests, lint, typecheck, self-review, docs, and manual testing notes. `CodexBar`, `RepoBar`, and `Trimmy` ask for commands run and UI screenshots/clips when relevant. `Trimmy` release docs define end-to-end release proof.

### 6. Secrets, Accounts, And Live Systems

- [ ] Explicitly forbid secret logging.
- [ ] Mark live account/provider tests opt-in.
- [ ] Prefer stubs, fixtures, dry-runs, redacted diagnostics, or no-UI keychain queries.
- [ ] Document when browser cookies, Keychain, Accessibility, Full Disk Access, or real provider probes are allowed.
- [ ] Keep API keys in env or secure stores, never argv or docs.

Evidence: `CodexBar` forbids checks that can trigger Keychain prompts unless explicitly requested. `oracle` documents redacted `doctor`, `--preflight`, and `--route` provider checks. `RepoBar` documents token storage and no token logging.

### 7. AI/Provider Preflight

- [ ] Add dry-run or preflight modes for expensive or external AI calls.
- [ ] Print redacted route/config diagnostics before spending tokens or touching live sessions.
- [ ] Persist sessions/artifacts so agents can reattach and audit results.
- [ ] Provide file-size caps and excludes for large context bundles.

Evidence: `oracle` has `--dry-run`, `doctor --providers`, `--preflight`, `--route`, session replay, file reports, and multi-model partial-success output files.

### 8. Machine-Readable Interfaces

- [ ] Offer `--json` or `--plain` output for CLIs.
- [ ] Document exit codes.
- [ ] Keep commands non-interactive by default.
- [ ] Add status commands for caches, daemons, sessions, or background work.

Evidence: `RepoBar` CLI exposes `--json`/`--plain`; `Trimmy` documents exit codes; `oracle` persists sessions and status commands; `summarize` has daemon status/restart commands.

### 9. CI And Repo Automation

- [ ] Add `.github/workflows` for build/test/lint.
- [ ] Add PR templates and bug templates for active projects.
- [ ] Keep local scripts and CI aligned.
- [ ] Avoid requiring unavailable secrets for ordinary PR checks.

Evidence: 16/30 scanned repos have workflows. `poltergeist` has PR and issue templates. Active TypeScript/Swift repos generally expose both local scripts and CI.

### 10. Release Readiness

- [ ] Keep release process in docs.
- [ ] Require changelog update for user-visible changes.
- [ ] Verify version continuity and release notes.
- [ ] Verify CI green before release.
- [ ] Verify artifacts after publish: signatures, notarization where relevant, downloads return 200, app/update path works.
- [ ] Make releases explicit-request only for agents.

Evidence: `Trimmy` release docs are the clearest example. `CodexBar`, `VibeMeter`, `summarize`, and `agent-scripts` also encode release verification expectations.

### 11. Dependency And Tooling Policy

- [ ] State package manager/runtime versions.
- [ ] Forbid swapping package managers or adding deps without approval.
- [ ] Require quick health checks before new dependencies.
- [ ] Keep lockfiles and generated files policy explicit.

Evidence: `RepoBar`, `summarize`, `poltergeist`, `agent-scripts`.

### 12. Generated Artifacts And Project Files

- [ ] Mark generated files and bundles as generated.
- [ ] Tell agents which files not to hand edit.
- [ ] Provide regeneration commands.
- [ ] For Xcode/GraphQL/generated APIs, call out source-of-truth files.

Evidence: `RepoBar` says not to hand-edit generated GraphQL files. `Trimmy` and `CodexBar` say not to edit generated bundles directly.

### 13. Multi-Agent Git Safety

- [ ] Tell agents how to handle dirty trees and unfamiliar changes.
- [ ] Forbid destructive resets/cleans unless explicitly requested.
- [ ] Keep commits scoped and conventional.
- [ ] Define branch/push/release consent.

Evidence: `agent-scripts` and `summarize` contain the richest multi-agent git guardrails.

### 14. Second-Opinion Workflow

- [ ] Document when to ask another model/tool for review.
- [ ] Include exact command and context-bundling guidance.
- [ ] Require preview/dry-run before large context or paid runs.
- [ ] Persist outputs and cite the model/session in handoff when used.

Evidence: `oracle` docs are built around this pattern and include suggested `AGENTS.md` wiring for coding agents.

### 15. Archive/Maintenance State

- [ ] For archived repos, say clearly whether maintenance is closed, minimal, or security-only.
- [ ] Document last known build environment and known breakage.
- [ ] Keep README enough for users, but avoid inviting broad modernization if not desired.
- [ ] Point obsolete AI rules to current canonical rules.

Evidence: many top-starred repos are archived Objective-C projects. `agent-rules` README points users to `agent-scripts` as newer work.

## Minimum Viable AI-Ready Repo

Use this as the shortest useful baseline:

- [ ] `README.md` with install, dev setup, and project purpose.
- [ ] `AGENTS.md` with repo map, exact commands, style, tests, security, PR/handoff rules.
- [ ] One green gate command.
- [ ] CI workflow that runs the green gate or close equivalent.
- [ ] Test folder and instructions for adding regression tests.
- [ ] PR template requiring summary, proof, commands run, and screenshots for UI.
- [ ] Secret/live-system policy.
- [ ] Release/changelog rule for user-visible changes.

## Top 30 Repo Signal Table

Column definitions: agent docs = `AGENTS.md`, `CLAUDE.md`, or Copilot instructions. CI = `.github/workflows` count. Test files = files under common test folders. Build manifests = package/project/build descriptors such as `package.json`, `Package.swift`, `go.mod`, `Makefile`, Xcode projects, podspecs.

| # | Repo | Stars | Archived | Lang | Agent docs | CI | Test files | Build manifests |
|---:|---|---:|---|---|---:|---:|---:|---:|
| 1 | [CodexBar](https://github.com/steipete/CodexBar) | 14716 | no | Swift | 2 | 3 | 405 | 5 |
| 2 | [Aspects](https://github.com/steipete/Aspects) | 8426 | yes | Objective-C | 0 | 0 | 0 | 7 |
| 3 | [summarize](https://github.com/steipete/summarize) | 6184 | no | TypeScript | 1 | 3 | 583 | 3 |
| 4 | [agent-rules](https://github.com/steipete/agent-rules) | 5687 | yes | Shell | 0 | 0 | 0 | 0 |
| 5 | [agent-scripts](https://github.com/steipete/agent-scripts) | 4863 | no | Shell | 1 | 1 | 0 | 1 |
| 6 | [PSTCollectionView](https://github.com/steipete/PSTCollectionView) | 2535 | yes | Objective-C | 0 | 0 | 0 | 11 |
| 7 | [oracle](https://github.com/steipete/oracle) | 2391 | no | TypeScript | 2 | 3 | 165 | 1 |
| 8 | [RepoBar](https://github.com/steipete/RepoBar) | 2081 | no | Swift | 1 | 1 | 104 | 4 |
| 9 | [PSStackedView](https://github.com/steipete/PSStackedView) | 1947 | yes | Objective-C | 0 | 0 | 0 | 3 |
| 10 | [claude-code-mcp](https://github.com/steipete/claude-code-mcp) | 1299 | yes | JavaScript | 2 | 2 | 12 | 1 |
| 11 | [AFDownloadRequestOperation](https://github.com/steipete/AFDownloadRequestOperation) | 1050 | yes | Objective-C | 0 | 0 | 0 | 1 |
| 12 | [InterposeKit](https://github.com/steipete/InterposeKit) | 1023 | yes | Swift | 0 | 6 | 10 | 9 |
| 13 | [PSPDFTextView](https://github.com/steipete/PSPDFTextView) | 870 | yes | Objective-C | 0 | 0 | 0 | 3 |
| 14 | [macos-automator-mcp](https://github.com/steipete/macos-automator-mcp) | 820 | no | TypeScript | 1 | 2 | 3 | 1 |
| 15 | [birdclaw](https://github.com/steipete/birdclaw) | 813 | no | TypeScript | 0 | 3 | 3 | 1 |
| 16 | [PSTAlertController](https://github.com/steipete/PSTAlertController) | 734 | yes | Objective-C | 0 | 0 | 0 | 3 |
| 17 | [Trimmy](https://github.com/steipete/Trimmy) | 711 | no | Swift | 2 | 2 | 14 | 3 |
| 18 | [PSPushPopPressView](https://github.com/steipete/PSPushPopPressView) | 607 | yes | Objective-C | 0 | 0 | 0 | 3 |
| 19 | [SDURLCache](https://github.com/steipete/SDURLCache) | 598 | yes | Objective-C | 0 | 0 | 0 | 1 |
| 20 | [PSFoundation](https://github.com/steipete/PSFoundation) | 568 | yes | Objective-C | 0 | 0 | 0 | 1 |
| 21 | [sag](https://github.com/steipete/sag) | 559 | no | Go | 1 | 3 | 0 | 2 |
| 22 | [poltergeist](https://github.com/steipete/poltergeist) | 414 | no | TypeScript | 2 | 3 | 129 | 13 |
| 23 | [steipete.me](https://github.com/steipete/steipete.me) | 412 | no | Astro | 2 | 2 | 0 | 1 |
| 24 | [VibeMeter](https://github.com/steipete/VibeMeter) | 383 | yes | Swift | 2 | 3 | 0 | 3 |
| 25 | [PSTDelegateProxy](https://github.com/steipete/PSTDelegateProxy) | 258 | yes | Objective-C | 0 | 0 | 13 | 1 |
| 26 | [Demark](https://github.com/steipete/Demark) | 233 | no | Swift | 0 | 1 | 8 | 4 |
| 27 | [speaking](https://github.com/steipete/speaking) | 212 | no | n/a | 0 | 0 | 0 | 0 |
| 28 | [tmuxwatch](https://github.com/steipete/tmuxwatch) | 209 | no | Go | 1 | 2 | 0 | 3 |
| 29 | [PSYouTubeExtractor](https://github.com/steipete/PSYouTubeExtractor) | 193 | yes | Objective-C | 0 | 0 | 0 | 1 |
| 30 | [PSMenuItem](https://github.com/steipete/PSMenuItem) | 179 | yes | Objective-C | 0 | 0 | 0 | 2 |

## Best Source Repos To Copy From

- `CodexBar`: comprehensive Swift/macOS agent instructions, UI/runtime validation, keychain safety, release docs.
- `RepoBar`: clean SwiftPM plus `pnpm` wrapper pattern, local app launch verification, CLI/debug commands.
- `Trimmy`: compact `AGENTS.md`, clear build/test/release commands, strong release checklist.
- `summarize`: monorepo guardrails, shared rules, strong green gate, daemon/extension specifics.
- `oracle`: second-opinion workflow, dry-run/preflight, session persistence, provider readiness.
- `poltergeist`: PR template, issue template, quality policy, TypeScript plus macOS app guidance.
- `agent-scripts`: canonical multi-agent workflow and release/git guardrails.

## Gap Notes

- Active repos with CI but weak or missing agent docs: `birdclaw`, `Demark`. Add root `AGENTS.md`.
- Active Go repos with agent docs but no obvious test files in scan: `sag`, `tmuxwatch`. Add tests or document why coverage is not expected.
- Website/content repos: `steipete.me`, `speaking`. AI readiness can be lighter: build/check command, content style, preview rules.
- Archived Objective-C repos: add a minimal `AGENTS.md` only if future agent maintenance is expected. Otherwise README archival status is enough.

## Sources

- GitHub API repo list: https://api.github.com/users/steipete/repos?per_page=100&type=owner
- [CodexBar AGENTS.md](https://github.com/steipete/CodexBar/blob/main/AGENTS.md)
- [CodexBar README](https://github.com/steipete/CodexBar)
- [RepoBar AGENTS.md](https://github.com/steipete/RepoBar/blob/main/AGENTS.md)
- [RepoBar README](https://github.com/steipete/RepoBar)
- [Trimmy AGENTS.md](https://github.com/steipete/Trimmy/blob/main/AGENTS.md)
- [Trimmy release docs](https://github.com/steipete/Trimmy/blob/main/docs/release.md)
- [summarize AGENTS.md](https://github.com/steipete/summarize/blob/main/AGENTS.md)
- [oracle AGENTS.md](https://github.com/steipete/oracle/blob/main/AGENTS.md)
- [oracle README](https://github.com/steipete/oracle)
- [oracle coding-agent docs](https://github.com/steipete/oracle/blob/main/docs/agents.md)
- [poltergeist PR template](https://github.com/steipete/poltergeist/blob/main/.github/pull_request_template.md)
- [poltergeist CONTRIBUTING](https://github.com/steipete/poltergeist/blob/main/CONTRIBUTING.md)
- [agent-scripts AGENTS.MD](https://github.com/steipete/agent-scripts/blob/main/AGENTS.MD)
- [agent-rules README](https://github.com/steipete/agent-rules)
