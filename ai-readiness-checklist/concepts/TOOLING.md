# TOOLING

Status: `General`

## Requirement

Repo pins or documents runtime, package manager, install command, and lockfile policy.

## Acceptance Criteria

- Runtime version is pinned or documented.
- Package manager is explicit.
- Install command is exact.
- Lockfile policy is clear.
- `check` script exists.

## Automatable Checks

- `package.json` exists for Node repos.
- Lockfile matches declared package manager.
- Runtime version exists in `package.json#engines`, `.nvmrc`, `mise.toml`, or docs.

## Example

```md
- Node 24, pnpm 10 via Corepack.
- Use `pnpm install --frozen-lockfile`.
- Do not use npm/yarn/bun unless changing package-manager support.
```

## References

- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
- [`steipete/inngest` AGENTS.md](https://github.com/steipete/inngest/blob/main/AGENTS.md)
- [`steipete/deepsec` CONTRIBUTING.md](https://github.com/steipete/deepsec/blob/main/CONTRIBUTING.md)
