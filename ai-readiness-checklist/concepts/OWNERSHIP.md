# OWNERSHIP

Status: `Mature`

## Requirement

Active public repos define default review ownership.

## Acceptance Criteria

- Default owner for all files.
- Optional owners for high-risk folders.

## Automatable Checks

- `.github/CODEOWNERS` exists for mature OSS repos.
- Contains `*` default owner rule.

## Example

```text
* @org/service-maintainers
/src/security/ @org/security-reviewers
/prisma/ @org/data-reviewers
```

## References

- [`steipete/cli` CODEOWNERS](https://github.com/steipete/cli/blob/main/.github/CODEOWNERS)
