# LIVE

Status: `General`

## Requirement

Normal checks avoid live accounts; live tests require explicit opt-in env vars and user approval.

## Acceptance Criteria

- Normal `check` does not hit live services.
- Live tests have explicit env var gates.
- Live tests require user approval for agent runs.
- CI live jobs are manual or separate.

## Automatable Checks

- `check` script does not include live-test env vars.
- `tests/live` docs mention required env var.
- Live workflow uses `workflow_dispatch` or separate trigger.

## Example

```md
Live provider tests live in `tests/live/**` and require both `PROVIDER_LIVE_TEST=1` and explicit approval in the current task.
```

## References

- [`steipete/oracle` AGENTS.md](https://github.com/steipete/oracle/blob/main/AGENTS.md)
- [`steipete/CodexBar` AGENTS.md](https://github.com/steipete/CodexBar/blob/main/AGENTS.md)
- [`steipete/deepsec` CONTRIBUTING.md](https://github.com/steipete/deepsec/blob/main/CONTRIBUTING.md)
