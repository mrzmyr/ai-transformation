# Security And Live System Details

## SECURITY_POLICY

Where: `SECURITY.md`.

Acceptance:

- Private reporting channel.
- Supported versions.
- In-scope/out-of-scope.
- What to include.
- Response expectations.
- Confidentiality.

Example:

```md
Do not report vulnerabilities through public GitHub issues.
Email security@example.com with description, impact, reproduction steps, affected versions, and suggested fix if known.
```

## SECRET_HANDLING

Where: `AGENTS.md`, `docs/security-model.md`.

Acceptance:

- No secret logging.
- No broad env dumps.
- No unredacted auth headers/cookies/private payloads.
- Public PR/issue text must be redacted.

Example:

```md
- Never run `env`, `set`, `export -p`, or broad secret regex scans.
- Query exact env vars only when needed and redact values.
- Never paste webhook payloads from production unless explicitly sanitized.
```

## LIVE_SYSTEM_GATES

Where: `AGENTS.md`, `docs/testing.md`, CI.

Acceptance:

- Normal `check` does not hit live services.
- Live tests have explicit env var gates.
- Live tests require user approval for agent runs.
- CI live jobs are manual or separate.

Example:

```md
Live provider tests live in `tests/live/**` and require both `PROVIDER_LIVE_TEST=1` and explicit approval in the current task.
```

## AI_PROVIDER_PREFLIGHT

Where: `README.md`, `docs/testing.md`, `AGENTS.md`.

Acceptance:

- Paid/provider calls have dry-run or doctor command.
- Route/config diagnostics are redacted.
- File/context report exists for model calls.
- Session or output path is recorded.

Example:

```md
- Preview: `oracle --dry-run summary --files-report -p "<task>" --file "src/**/*.ts"`
- Redacted readiness: `oracle doctor --providers`
- Route only: `oracle --route --model gpt-5.5-pro`
```
