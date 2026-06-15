# LICENSE

Status: `Open Source`

## Requirement

Public repos declare distribution terms in a standard root license file and keep package metadata consistent with it.

## Acceptance Criteria

- Root `LICENSE`, `LICENSE.md`, or `COPYING` exists.
- Package metadata license matches the root license when metadata exists.
- README, package metadata, docs, and release artifacts do not make contradictory license claims.
- Required notices are preserved for redistributed third-party code or generated artifacts.

## Automatable Checks

- License file exists in repo root.
- Known manifest fields match the detected license, e.g. `package.json#license`, `Cargo.toml#package.license`, `pyproject.toml#project.license`, gemspec license fields.
- README does not mention a different common license string than the root license.

## Example

```json
{
  "license": "MIT"
}
```

```text
LICENSE
README.md
package.json
```

## References

- [`steipete/CodexBar` LICENSE](https://github.com/steipete/CodexBar/blob/main/LICENSE)
- [`steipete/summarize` LICENSE](https://github.com/steipete/summarize/blob/main/LICENSE)
- [`steipete/RepoBar` LICENSE](https://github.com/steipete/RepoBar/blob/main/LICENSE)
