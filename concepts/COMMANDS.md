# COMMANDS

Status: `General`

## Requirement

Docs list focused commands for common change surfaces, but still require `check` before handoff.

## Acceptance Criteria

- Common change surfaces have focused commands.
- Focused commands are faster than `check`.
- Docs say `check` is still required before handoff.

## Automatable Checks

- `AGENTS.md` or `docs/testing.md` contains focused command examples.
- Same doc mentions `check` before handoff.

## Example

```md
- API route: `pnpm vitest run tests/integration/webhooks.test.ts`
- Service: `pnpm vitest run tests/services/billing.test.ts`
- DB repo: `pnpm vitest run tests/db/events-repository.test.ts`
- Contract: `pnpm vitest run tests/contracts/public-api.test.ts`
```

## References

- [`steipete/deepsec` CONTRIBUTING.md](https://github.com/steipete/deepsec/blob/main/CONTRIBUTING.md)
- [`steipete/oracle` AGENTS.md](https://github.com/steipete/oracle/blob/main/AGENTS.md)
- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
