# ISSUES

Status: `Open Source`

## Requirement

Issue templates require exact repro, version, platform, expected vs actual, and redacted logs.

## Acceptance Criteria

- Exact repro.
- Expected vs actual.
- Version.
- Platform.
- Logs with redaction reminder.

## Automatable Checks

- `.github/ISSUE_TEMPLATE/` exists.
- Bug template contains repro/version/platform/logs fields.

## Example

```yaml
- type: textarea
  id: repro
  attributes:
    label: Steps to reproduce
    description: Include exact commands.
```

## References

- [`steipete/cli` bug issue template](https://github.com/steipete/cli/blob/main/.github/ISSUE_TEMPLATE/bug_report.yml)
- [`steipete/deepsec` bug issue template](https://github.com/steipete/deepsec/blob/main/.github/ISSUE_TEMPLATE/bug.md)
- [`steipete/stats-store` bug issue template](https://github.com/steipete/stats-store/blob/main/.github/ISSUE_TEMPLATE/bug_report.md)
