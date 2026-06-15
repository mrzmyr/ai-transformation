# REVIEW

Status: `Mature`

## Requirement

Risky changes define when to ask another model/tool, how to dry-run context, and how to cite results.

## Acceptance Criteria

- Trigger conditions.
- Dry-run/preview command.
- Approval boundary for paid/live calls.
- How to cite result.

## Automatable Checks

- Mature repos mention second-opinion workflow in agent docs.
- Paid/live model calls include dry-run guidance.

## Example

```md
Use a second model/tool for stuck bugs, high-risk architecture changes, security-sensitive changes, or large refactors. Preview context first and cite output path/session id in handoff.
```

## References

- [`steipete/oracle` coding-agent docs](https://github.com/steipete/oracle/blob/main/docs/agents.md)
- [`steipete/oracle` README](https://github.com/steipete/oracle/blob/main/README.md)
