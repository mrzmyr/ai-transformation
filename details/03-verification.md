# Verification Details

## CHECK_SCRIPT

Where: `package.json`.

Acceptance:

- Script is named exactly `check`.
- Runs format check, lint/static analysis, typecheck/build, and tests.
- Requires no secrets/live accounts.
- Exits nonzero on failure.

Example:

```json
{
  "scripts": {
    "format:check": "oxfmt --check .",
    "lint": "oxlint --deny-warnings src tests",
    "typecheck": "tsgo --noEmit",
    "test": "vitest run",
    "build": "tsgo -p tsconfig.build.json",
    "check": "pnpm format:check && pnpm lint && pnpm typecheck && pnpm test && pnpm build"
  }
}
```

## CI_CHECK

Where: `.github/workflows/ci.yml`.

Acceptance:

- CI installs same package manager/runtime.
- CI runs `pnpm check` or a documented strict superset.
- CI has no local absolute paths.
- Live tests are separate.

Example:

```yaml
- uses: pnpm/action-setup@v4
  with:
    version: 10
- uses: actions/setup-node@v4
  with:
    node-version: 24
    cache: pnpm
- run: pnpm install --frozen-lockfile
- run: pnpm check
```

## FOCUSED_COMMANDS

Where: `AGENTS.md`, `docs/testing.md`.

Acceptance:

- Common change surfaces have focused commands.
- Focused commands are faster than `check`.
- Docs say `check` is still required before handoff.

Example:

```md
- API route: `pnpm vitest run tests/integration/webhooks.test.ts`
- Service: `pnpm vitest run tests/services/billing.test.ts`
- DB repo: `pnpm vitest run tests/db/events-repository.test.ts`
- Contract: `pnpm vitest run tests/contracts/public-api.test.ts`
```

## VERIFICATION_MATRIX

Where: `AGENTS.md`, PR template.

Acceptance:

- Maps change type to exact proof.
- Covers docs, logic, API, worker, DB, auth/security, generated code, release.

Example:

```md
| Change | Required proof |
|---|---|
| API route | Focused integration test + `pnpm check` |
| DB schema | Migration check + repository test + `pnpm check` |
| Auth/security | Stubbed tests only unless live approval is explicit |
```

## TEST_STRATEGY

Where: `docs/testing.md` or `AGENTS.md`.

Acceptance:

- Test folders are named.
- Fixtures are named.
- Live tests are env-gated.
- Test naming pattern is stated.
- Regression-test expectation is stated.

Example:

```md
- `tests/integration/**`: HTTP routes with test server.
- `tests/services/**`: service tests with mocked clients.
- `tests/db/**`: repository tests with test database.
- `tests/live/**`: skipped unless `PROVIDER_LIVE_TEST=1`.
```
