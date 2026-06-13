# Runtime And Service Details

## RUNTIME_TOOLING

Where: `package.json`, `.nvmrc`, `mise.toml`, `README.md`, `AGENTS.md`.

Acceptance:

- Runtime version is pinned or documented.
- Package manager is explicit.
- Install command is exact.
- Lockfile policy is clear.
- `check` script exists.

Example:

```md
- Node 24, pnpm 10 via Corepack.
- Use `pnpm install --frozen-lockfile`.
- Do not use npm/yarn/bun unless changing package-manager support.
```

## SERVICE_BOUNDARIES

Where: `AGENTS.md` repo map and `docs/architecture.md`.

Acceptance:

- Routes/controllers validate inputs and call services.
- Services own business logic.
- Repositories own DB access.
- Clients own external API calls.
- Workers/jobs are separate from HTTP routes.
- Generated code has a clear boundary.

Example:

```md
- `src/routes/` - HTTP handlers, no business logic.
- `src/services/` - business logic.
- `src/db/` - repositories and migrations.
- `src/clients/` - external APIs; mock in normal tests.
- `src/workers/` - queue consumers and scheduled jobs.
```

## LOCAL_DEV_LOOP

Where: `README.md`, `AGENTS.md`, `docs/development.md`.

Acceptance:

- Start dependency services.
- Apply migrations.
- Start API.
- Start worker if needed.
- Stop dependencies.
- Health check command.

Example:

```md
- Start deps: `pnpm dev:deps`
- Migrate: `pnpm db:migrate`
- Start API: `pnpm dev:api`
- Start worker: `pnpm dev:worker`
- Health: `curl -fsS http://127.0.0.1:3000/healthz`
- Stop deps: `pnpm dev:deps:down`
```

## CONFIG_ENV_CONTRACT

Where: `.env.example`, `docs/development.md`, `docs/security-model.md`.

Acceptance:

- `.env.example` exists and contains non-secret placeholders.
- Required vs optional env vars are marked.
- Local defaults are documented.
- Production secret source is documented.
- Test env behavior is documented.

Example:

```md
Required:
- `DATABASE_URL`: Postgres connection string.
- `WEBHOOK_SECRET`: HMAC secret. Use local dummy value only in tests.

Optional:
- `REDIS_URL`: defaults to local Docker Redis in dev.
```

## DATABASE_MIGRATIONS

Where: `docs/development.md`, `docs/release.md`, package scripts.

Acceptance:

- Create migration command.
- Validate migration command.
- Apply local migration command.
- Test DB guidance.
- Release/deploy migration policy.

Example:

```json
{
  "scripts": {
    "db:migrate": "prisma migrate dev",
    "db:check": "prisma validate",
    "migrate:check": "prisma migrate diff --from-migrations prisma/migrations --to-schema-datamodel prisma/schema.prisma --exit-code"
  }
}
```

## HEALTHCHECK_SMOKE

Where: `README.md`, `AGENTS.md`, CI, release docs.

Acceptance:

- Local health command exists.
- Deployed health command exists if service deploys.
- Critical route smoke is documented.

Example:

```md
- Local: `curl -fsS http://127.0.0.1:3000/healthz`
- Staging: `curl -fsS https://staging.example.com/healthz`
- Webhook smoke: `pnpm smoke:webhook -- --base-url http://127.0.0.1:3000`
```

## MACHINE_INTERFACE

Where: `README.md`, `docs/cli.md`, tests.

Acceptance:

- CLI supports `--json` or `--plain`.
- Exit codes are documented.
- Service exposes health/status endpoint.
- Long-running commands print job/session id.

Example:

```md
Exit codes: `0` success, `1` input error, `2` no-op, `3` external dependency unavailable.
```
