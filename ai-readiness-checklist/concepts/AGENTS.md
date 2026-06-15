# AGENTS

Status: `General`

## Requirement

Root `AGENTS.md` defines exact agent operating rules, repo map, commands, verification, and safety caveats.

## Acceptance Criteria

- Project purpose in one sentence.
- Repo map with real paths.
- Runtime/package manager.
- Exact commands.
- Verification matrix.
- Security/live-system rules.
- Generated-file rules if applicable.
- Assistant-specific files either do not exist or only point back to `AGENTS.md`.
- Nested `AGENTS.md` files exist only when subtree rules differ.
- Shared/global guardrail blocks stay separate from repo-specific rules.

## Automatable Checks

- `AGENTS.md` exists at repo root.
- Contains `Commands`.
- Contains `Verification` or `Verification Matrix`.
- Contains `Security` or `Secrets`.
- If `CLAUDE.md`, `.github/copilot-instructions.md`, or similar files exist, they mention `AGENTS.md`.

## Example

```md
## Commands

- Install: `pnpm install --frozen-lockfile`
- Green gate: `pnpm check`
- Focused webhook test: `pnpm vitest run tests/integration/webhooks.test.ts`

## Assistant Routing

- `AGENTS.md` is the source of truth for coding agents.
- `CLAUDE.md` and Copilot instructions must link here instead of duplicating rules.
- Add nested `AGENTS.md` files only when a subtree has different commands, generated files, or safety rules.
```

## References

- [`steipete/sweetlink` AGENTS.md](https://github.com/steipete/sweetlink/blob/main/AGENTS.md)
- [`steipete/RepoBar` AGENTS.md](https://github.com/steipete/RepoBar/blob/main/AGENTS.md)
- [`steipete/Trimmy` AGENTS.md](https://github.com/steipete/Trimmy/blob/main/AGENTS.md)
- [`steipete/oracle` AGENTS.md](https://github.com/steipete/oracle/blob/main/AGENTS.md)
