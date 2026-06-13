# Repository Contract Details

## REPO_PURPOSE

Where: `README.md`.

Acceptance:

- First screen explains what the project does and who uses it.
- Install or run command is present.
- Dev quick start is present.
- For services, local URL or API entrypoint is present.

Example:

```md
# Event API

Event API receives partner webhooks, validates them, normalizes payloads, and stores events in Postgres for downstream workers.

## Development

pnpm install
pnpm dev:deps
pnpm dev
curl -fsS http://127.0.0.1:3000/healthz
```

## FILE_CONTRACT

Where: checklist plus actual files.

Acceptance:

- `README.md`: product and user/dev quick start.
- `AGENTS.md`: agent instructions.
- `SECURITY.md`: vulnerability reporting.
- `.github/workflows/ci.yml`: green gate.
- `.github/PULL_REQUEST_TEMPLATE.md`: proof requirements.
- `docs/testing.md`: deeper test strategy when tests are non-trivial.
- `docs/release.md`: release/deploy flow when repo ships.

Do not put everything in `AGENTS.md`. Keep `AGENTS.md` operational and link deeper docs.

## AGENT_ENTRYPOINT

Where: root `AGENTS.md`.

Acceptance:

- Project purpose in one sentence.
- Repo map with real paths.
- Runtime/package manager.
- Exact commands.
- Verification matrix.
- Security/live-system rules.
- Generated-file rules if applicable.

Example:

```md
## Commands

- Install: `pnpm install --frozen-lockfile`
- Green gate: `pnpm check`
- Focused webhook test: `pnpm vitest run tests/integration/webhooks.test.ts`
```

## SHARED_RULES_BOUNDARY

Where: `AGENTS.md`.

Acceptance:

- Shared/generated block has begin/end markers.
- Repo-local rules are outside the block.
- Precedence is explicit.

Example:

```md
Repo-local rules above override shared-agent-rules below.

<!-- BEGIN shared-agent-rules: DO NOT EDIT HERE -->
...
<!-- END shared-agent-rules -->
```

## MAINTENANCE_STATE

Where: `README.md`; optional `AGENTS.md`.

Acceptance:

- Archived/maintenance-only status is visible near top.
- Accepted change types are stated.
- Replacement project is linked if relevant.

Example:

```md
> Maintenance status: security-only. Feature PRs are not accepted. For new work use `new-service`.
```
