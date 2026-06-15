# VERIFICATION_MATRIX

Status: `General`

## Requirement

`AGENTS.md` maps change type to required proof and exact commands.

## Acceptance Criteria

- Maps change type to exact proof.
- Covers docs, logic, API, worker, DB, auth/security, generated code, release.

## Automatable Checks

- `AGENTS.md` contains a Markdown table under `Verification`.
- Table contains `pnpm check` or equivalent.

## Example

```md
| Change | Required proof |
|---|---|
| API route | Focused integration test + `pnpm check` |
| DB schema | Migration check + repository test + `pnpm check` |
| Auth/security | Stubbed tests only unless live approval is explicit |
```

## References

- [`steipete/deepsec` PR template](https://github.com/steipete/deepsec/blob/main/.github/PULL_REQUEST_TEMPLATE.md)
- [`steipete/poltergeist` PR template](https://github.com/steipete/poltergeist/blob/main/.github/pull_request_template.md)
- [`steipete/RepoBar` AGENTS.md](https://github.com/steipete/RepoBar/blob/main/AGENTS.md)
