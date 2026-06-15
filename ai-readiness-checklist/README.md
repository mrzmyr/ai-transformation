<p align="center">
  <img src="assets/checklist-clipboard.png" alt="AI Readiness Checklist" width="160">
</p>

# AI Readiness Checklist

### General

Applies to every active repo.

| Concept | Requirement |
|---|---|
| 🎯 [`PURPOSE`](concepts/PURPOSE.md) | `README.md` defines:<br>- product purpose<br>- install path<br>- user-facing usage<br>- dev quick start |
| 🗂️ [`FILES`](concepts/FILES.md) | repo defines canonical files for:<br>- agent rules<br>- contributing<br>- security<br>- testing<br>- release<br>- generated files |
| 🤖 [`AGENTS`](concepts/AGENTS.md) | root `AGENTS.md` defines:<br>- repo map<br>- exact commands<br>- verification rules<br>- safety caveats |
| 🧰 [`TOOLING`](concepts/TOOLING.md) | repo pins or documents:<br>- runtime<br>- package manager<br>- install command<br>- lockfile policy |
| ✅ [`CHECK`](concepts/CHECK.md) | primary green gate:<br>- is named `check`<br>- runs format/lint/typecheck/build/tests<br>- needs no secrets/live accounts |
| 🔁 [`CI`](concepts/CI.md) | CI runs:<br>- same `check` command<br>- or documented strict superset |
| ⌨️ [`COMMANDS`](concepts/COMMANDS.md) | docs list:<br>- focused commands by change surface<br>- rule that `check` is still required before handoff |
| 🧾 [`VERIFICATION_MATRIX`](concepts/VERIFICATION_MATRIX.md) | `AGENTS.md` maps:<br>- change type<br>- required proof<br>- exact command |
| 🤝 [`HANDOFF`](concepts/HANDOFF.md) | agent handoff includes:<br>- summary<br>- files changed<br>- commands run<br>- proof artifacts<br>- skipped checks/known gaps |
| 🧪 [`TESTING`](concepts/TESTING.md) | docs define:<br>- test types<br>- fixture locations<br>- naming pattern<br>- live-test gates |
| 🛡️ [`SECURITY`](concepts/SECURITY.md) | `SECURITY.md` defines:<br>- private vulnerability reporting<br>- supported versions<br>- scope<br>- response expectations<br>- confidentiality |
| 🔐 [`SECRETS`](concepts/SECRETS.md) | agent rules forbid:<br>- secret logging<br>- broad env dumps<br>- unredacted auth headers/cookies<br>- private payload leaks |
| ⚡ [`LIVE`](concepts/LIVE.md) | normal checks avoid live accounts; live tests require:<br>- explicit env opt-in<br>- user approval |

### Service

Applies to web servers, TypeScript backends, workers, APIs, or deployed services.

| Concept | Requirement |
|---|---|
| 🏗️ [`ARCHITECTURE`](concepts/ARCHITECTURE.md) | backend layout separates:<br>- routes/controllers<br>- services<br>- repositories<br>- clients<br>- workers<br>- generated code |
| 🛠️ [`DEVELOPMENT`](concepts/DEVELOPMENT.md) | docs define commands to:<br>- start dependencies<br>- run server/worker<br>- stop services<br>- verify health |
| ⚙️ [`CONFIG`](concepts/CONFIG.md) | docs define:<br>- required env vars<br>- `.env.example`<br>- config defaults<br>- secret sources<br>- local-vs-production behavior |
| 🩺 [`HEALTHCHECK`](concepts/HEALTHCHECK.md) | service exposes smoke checks for:<br>- local readiness<br>- deployed readiness<br>- handoff/CI proof |

### Open Source

Applies to public or open-contribution repos.

| Concept | Requirement |
|---|---|
| 📜 [`LICENSE`](concepts/LICENSE.md) | public repo defines:<br>- root license file<br>- matching package metadata<br>- no contradictory README/package claims |
| 🔀 [`PULL_REQUEST`](concepts/PULL_REQUEST.md) | PR template requires:<br>- what changed<br>- why<br>- verification commands<br>- docs/changelog decision<br>- reviewer notes |
| ❗ [`ISSUES`](concepts/ISSUES.md) | issue templates require:<br>- exact repro<br>- version<br>- platform<br>- expected vs actual<br>- redacted logs |

### Conditional

Applies only when the repo has the matching surface.

| Concept | Requirement |
|---|---|
| 🧹 [`MAINTENANCE`](concepts/MAINTENANCE.md) | archived/maintenance-only repos state:<br>- support status<br>- accepted change types<br>- replacement project |
| 🔄 [`MIGRATIONS`](concepts/MIGRATIONS.md) | schema changes define:<br>- migration commands<br>- validation commands<br>- rollback/forward policy<br>- test DB guidance |
| 🚀 [`RELEASE`](concepts/RELEASE.md) | release docs define:<br>- version bumps<br>- artifact/package publish<br>- deploy<br>- smoke proof<br>- failure handling |
| 📝 [`CHANGELOG`](concepts/CHANGELOG.md) | user-visible changes have:<br>- documented changelog rule<br>- changelog location |

### Mature

Useful for larger, high-risk, or heavily maintained repos.

| Concept | Requirement |
|---|---|
| 🧱 [`DEPENDENCIES`](concepts/DEPENDENCIES.md) | dependency policy defines:<br>- ecosystems<br>- cadence<br>- grouping<br>- PR limits |
| 👥 [`OWNERSHIP`](concepts/OWNERSHIP.md) | active public repos define:<br>- default review ownership<br>- high-risk area ownership |
| 👀 [`REVIEW`](concepts/REVIEW.md) | risky changes define:<br>- when to ask another model/tool<br>- dry-run context command<br>- result citation |
