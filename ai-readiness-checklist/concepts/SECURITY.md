# SECURITY

Status: `General`

## Requirement

`SECURITY.md` defines private vulnerability reporting, supported versions, scope, expectations, and confidentiality.

## Acceptance Criteria

- Private reporting channel.
- Supported versions.
- In-scope/out-of-scope.
- What to include.
- Response expectations.
- Confidentiality.

## Automatable Checks

- `SECURITY.md` exists.
- Contains `Reporting` or `Vulnerability`.
- Contains non-public reporting channel.

## Example

```md
Do not report vulnerabilities through public GitHub issues.
Email security@example.com with description, impact, reproduction steps, affected versions, and suggested fix if known.
```

## References

- [`steipete/cli` SECURITY.md](https://github.com/steipete/cli/blob/main/SECURITY.md)
- [`steipete/deepsec` SECURITY.md](https://github.com/steipete/deepsec/blob/main/SECURITY.md)
- [`steipete/desktop-api-cli` SECURITY.md](https://github.com/steipete/desktop-api-cli/blob/main/SECURITY.md)
