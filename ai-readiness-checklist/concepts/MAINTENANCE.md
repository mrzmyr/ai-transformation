# MAINTENANCE

Status: `Conditional`

## Requirement

Archived or maintenance-only repos state support status, accepted change types, and replacement project.

## Acceptance Criteria

- Archived/maintenance-only status is visible near top.
- Accepted change types are stated.
- Replacement project is linked if relevant.

## Automatable Checks

- If GitHub repo is archived, `README.md` contains `archived`, `maintenance`, or `unmaintained`.

## Example

```md
> Maintenance status: security-only. Feature PRs are not accepted. For new work use `new-service`.
```

## References

- [`steipete/agent-rules` README](https://github.com/steipete/agent-rules/blob/main/README.md)
- [`steipete/VibeMeter` CLAUDE.md](https://github.com/steipete/VibeMeter/blob/main/CLAUDE.md)
