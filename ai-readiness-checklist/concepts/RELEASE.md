# RELEASE

Status: `Conditional`

## Requirement

Release docs define version bumps, artifact/package publish, deploy, smoke proof, and failure handling.

## Acceptance Criteria

- Version bump locations.
- Changelog source.
- Build/publish/deploy commands.
- Artifact or registry verification.
- Deployed health smoke.
- Failure handling.

## Automatable Checks

- If release workflow exists, release docs exist.
- Release docs mention `check`.
- Release docs mention artifact or deployment verification.

## Example

```md
- Run `pnpm check`.
- Publish package: `pnpm publish --access public`.
- Verify: `npm view <pkg>@<version>`.
- Deploy: `pnpm deploy`.
- Smoke: `curl -fsS https://api.example.com/healthz`.
```

## References

- [`steipete/Trimmy` release docs](https://github.com/steipete/Trimmy/blob/main/docs/release.md)
- [`steipete/ReleaseBar` AGENTS.md](https://github.com/steipete/ReleaseBar/blob/main/AGENTS.md)
- [`steipete/summarize` AGENTS.md](https://github.com/steipete/summarize/blob/main/AGENTS.md)
- [`steipete/agent-scripts` AGENTS.MD](https://github.com/steipete/agent-scripts/blob/main/AGENTS.MD)
