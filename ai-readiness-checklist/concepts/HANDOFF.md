# HANDOFF

Status: `General`

## Requirement

Agent handoff states what changed, what was verified, where proof lives, and which checks were skipped or remain risky.

## Acceptance Criteria

- Summary of intended behavior change.
- Important files or areas changed.
- Exact commands run.
- Pass/fail result for each command.
- Proof artifact for UI, API, service, or release changes.
- Skipped checks with reason.
- Known gaps or follow-up risks.

## Automatable Checks

- `AGENTS.md` contains a `Handoff` or `Final Response` section.
- PR template or agent rules contain `Summary`.
- PR template or agent rules contain `Verification`.
- PR template or agent rules require skipped checks to be listed.

## Example

```md
## Handoff

- Summary: fixed webhook retry backoff.
- Changed: `src/webhooks/retry.ts`, `tests/webhooks/retry.test.ts`.
- Verification: `pnpm vitest run tests/webhooks/retry.test.ts` passed; `pnpm check` passed.
- Proof: local test output in terminal.
- Skipped: no live webhook replay; unit coverage exercises retry schedule.
```

## References

- [`steipete/CodexBar` AGENTS.md](https://github.com/steipete/CodexBar/blob/main/AGENTS.md)
- [`steipete/summarize` AGENTS.md](https://github.com/steipete/summarize/blob/main/AGENTS.md)
- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
