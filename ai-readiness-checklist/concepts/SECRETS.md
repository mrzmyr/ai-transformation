# SECRETS

Status: `General`

## Requirement

Agent rules forbid secret logging, broad env dumps, unredacted auth headers, cookies, and private payloads.

## Acceptance Criteria

- No secret logging.
- No broad env dumps.
- No unredacted auth headers/cookies/private payloads.
- Public PR/issue text must be redacted.

## Automatable Checks

- `AGENTS.md` mentions secrets/tokens/cookies.
- `AGENTS.md` forbids broad env dumps or requires redaction.

## Example

```md
- Never run `env`, `set`, `export -p`, or broad secret regex scans.
- Query exact env vars only when needed and redact values.
- Never paste webhook payloads from production unless explicitly sanitized.
```

## References

- [`steipete/RepoBar` AGENTS.md](https://github.com/steipete/RepoBar/blob/main/AGENTS.md)
- [`steipete/CodexBar` AGENTS.md](https://github.com/steipete/CodexBar/blob/main/AGENTS.md)
- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
- [`steipete/agent-scripts` AGENTS.MD](https://github.com/steipete/agent-scripts/blob/main/AGENTS.MD)
