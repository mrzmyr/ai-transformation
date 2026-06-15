# ARCHITECTURE

Status: `Service`

## Requirement

Backend layout separates routes/controllers, services, repositories, clients, workers, and generated code.

## Acceptance Criteria

- Routes/controllers validate inputs and call services.
- Services own business logic.
- Repositories own DB access.
- Clients own external API calls.
- Workers/jobs are separate from HTTP routes.
- Generated code has a clear boundary.

## Automatable Checks

- Service repos contain documented path map in `AGENTS.md` or `docs/architecture.md`.
- Generated path is documented if generated directory exists.

## Example

```md
- `src/routes/` - HTTP handlers, no business logic.
- `src/services/` - business logic.
- `src/db/` - repositories and migrations.
- `src/clients/` - external APIs; mock in normal tests.
- `src/workers/` - queue consumers and scheduled jobs.
```

## References

- [`steipete/deepsec` CONTRIBUTING.md](https://github.com/steipete/deepsec/blob/main/CONTRIBUTING.md)
- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
- [`steipete/stats-store` CLAUDE.md](https://github.com/steipete/stats-store/blob/main/CLAUDE.md)
