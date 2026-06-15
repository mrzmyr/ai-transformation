# TESTING

Status: `General`

## Requirement

`docs/testing.md` or `AGENTS.md` defines test types, fixture locations, naming pattern, and live-test gates.

## Acceptance Criteria

- Test folders are named.
- Fixtures are named.
- Live tests are env-gated.
- Test naming pattern is stated.
- Regression-test expectation is stated.

## Automatable Checks

- `tests/` or equivalent exists.
- `AGENTS.md` or `docs/testing.md` mentions fixtures or test folder.
- Live test env vars are documented if `tests/live` exists.

## Example

```md
- `tests/integration/**`: HTTP routes with test server.
- `tests/services/**`: service tests with mocked clients.
- `tests/db/**`: repository tests with test database.
- `tests/live/**`: skipped unless `PROVIDER_LIVE_TEST=1`.
```

## References

- [`steipete/deepsec` CONTRIBUTING.md](https://github.com/steipete/deepsec/blob/main/CONTRIBUTING.md)
- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
- [`steipete/summarize` AGENTS.md](https://github.com/steipete/summarize/blob/main/AGENTS.md)
