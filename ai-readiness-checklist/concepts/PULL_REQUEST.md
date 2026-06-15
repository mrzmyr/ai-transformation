# PULL_REQUEST

Status: `Open Source`

## Requirement

PR template requires what changed, why, exact verification commands, docs/changelog decision, and reviewer notes.

## Acceptance Criteria

- What changed.
- Why.
- Verification commands.
- Docs/changelog decision.
- Reviewer notes.

## Automatable Checks

- `.github/PULL_REQUEST_TEMPLATE.md` exists.
- Contains `Verification`.
- Contains command checklist or `check`.

## Example

```md
## Verification

- [ ] `pnpm check` passed
- [ ] Focused regression: `<command>`
- [ ] Docs/changelog updated or not needed because: `<reason>`
- [ ] No live secrets/accounts used
```

## References

- [`steipete/deepsec` PR template](https://github.com/steipete/deepsec/blob/main/.github/PULL_REQUEST_TEMPLATE.md)
- [`steipete/poltergeist` PR template](https://github.com/steipete/poltergeist/blob/main/.github/pull_request_template.md)
- [`steipete/stats-store` PR template](https://github.com/steipete/stats-store/blob/main/.github/pull_request_template.md)
