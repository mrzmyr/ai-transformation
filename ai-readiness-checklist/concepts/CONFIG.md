# CONFIG

Status: `Service`

## Requirement

Docs define required env vars, `.env.example`, config defaults, secret sources, and local-vs-production behavior.

## Acceptance Criteria

- `.env.example` exists and contains non-secret placeholders.
- Required vs optional env vars are marked.
- Local defaults are documented.
- Production secret source is documented.
- Test env behavior is documented.

## Automatable Checks

- `.env.example` exists for service repos.
- Docs mention required environment variables.
- `.env` files are gitignored.

## Example

```md
Required:
- `DATABASE_URL`: Postgres connection string.
- `WEBHOOK_SECRET`: HMAC secret. Use local dummy value only in tests.

Optional:
- `REDIS_URL`: defaults to local Docker Redis in dev.
```

## References

- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
- [`steipete/stats-store` CLAUDE.md](https://github.com/steipete/stats-store/blob/main/CLAUDE.md)
- [`steipete/ReleaseBar` AGENTS.md](https://github.com/steipete/ReleaseBar/blob/main/AGENTS.md)
