# GitHub Workflow Details

## PR_PROOF

Where: `.github/PULL_REQUEST_TEMPLATE.md`.

Acceptance:

- What changed.
- Why.
- Verification commands.
- Docs/changelog decision.
- Reviewer notes.

Example:

```md
## Verification

- [ ] `pnpm check` passed
- [ ] Focused regression: `<command>`
- [ ] Docs/changelog updated or not needed because: `<reason>`
- [ ] No live secrets/accounts used
```

## ISSUE_INTAKE

Where: `.github/ISSUE_TEMPLATE/*.yml`.

Acceptance:

- Exact repro.
- Expected vs actual.
- Version.
- Platform.
- Logs with redaction reminder.

Example:

```yaml
- type: textarea
  id: repro
  attributes:
    label: Steps to reproduce
    description: Include exact commands.
```

## DEPENDENCY_GOVERNANCE

Where: `.github/dependabot.yml`, `AGENTS.md`.

Acceptance:

- Ecosystems listed.
- Update cadence.
- Grouping.
- Open PR limits.
- New dependency approval rule.

Example:

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

## CODEOWNERS

Where: `.github/CODEOWNERS`.

Acceptance:

- Default owner for all files.
- Optional owners for high-risk folders.

Example:

```text
* @org/service-maintainers
/src/security/ @org/security-reviewers
/prisma/ @org/data-reviewers
```
