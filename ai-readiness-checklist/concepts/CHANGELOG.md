# CHANGELOG

Status: `Conditional`

## Requirement

User-visible changes have a documented changelog rule and location.

## Acceptance Criteria

- User-visible changes require changelog entry.
- Internal-only/test-only changes may skip with reason.
- Format is documented.

## Automatable Checks

- `CHANGELOG.md` exists for released repos.
- `AGENTS.md` or `CONTRIBUTING.md` mentions changelog policy.

## Example

```md
Update `CHANGELOG.md` for user-visible behavior, config, CLI flags, API shape, migrations, or release changes.
```

## References

- [`steipete/Trimmy` AGENTS.md](https://github.com/steipete/Trimmy/blob/main/AGENTS.md)
- [`steipete/summarize` AGENTS.md](https://github.com/steipete/summarize/blob/main/AGENTS.md)
- [`steipete/InterposeKit` CONTRIBUTING.md](https://github.com/steipete/InterposeKit/blob/master/CONTRIBUTING.md)
