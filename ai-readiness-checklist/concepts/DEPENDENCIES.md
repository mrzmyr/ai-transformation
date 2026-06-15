# DEPENDENCIES

Status: `Mature`

## Requirement

Dependency update policy and Dependabot config define ecosystems, cadence, grouping, and PR limits.

## Acceptance Criteria

- Ecosystems listed.
- Update cadence.
- Grouping.
- Open PR limits.
- New dependency approval rule.

## Automatable Checks

- `.github/dependabot.yml` exists.
- Config includes repo package ecosystem and GitHub Actions.

## Example

```yaml
version: 2
updates:
  - package-ecosystem: npm
    directory: "/"
    schedule:
      interval: weekly
    groups:
      dependencies:
        patterns: ["*"]
```

## References

- [`steipete/oracle` Dependabot config](https://github.com/steipete/oracle/blob/main/.github/dependabot.yml)
- [`steipete/summarize` Dependabot config](https://github.com/steipete/summarize/blob/main/.github/dependabot.yml)
- [`steipete/stats-store` Dependabot config](https://github.com/steipete/stats-store/blob/main/.github/dependabot.yml)
