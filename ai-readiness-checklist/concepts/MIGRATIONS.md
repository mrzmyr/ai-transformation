# MIGRATIONS

Status: `Conditional`

## Requirement

Schema changes have migration commands, validation commands, rollback/forward policy, and test database guidance.

## Acceptance Criteria

- Create migration command.
- Validate migration command.
- Apply local migration command.
- Test DB guidance.
- Release/deploy migration policy.

## Automatable Checks

- If `prisma/`, `migrations/`, or ORM config exists, package scripts include migration/check commands or docs mention them.

## Example

```json
{
  "scripts": {
    "db:migrate": "prisma migrate dev",
    "db:check": "prisma validate",
    "migrate:check": "prisma migrate diff --from-migrations prisma/migrations --to-schema-datamodel prisma/schema.prisma --exit-code"
  }
}
```

## References

- [`steipete/stats-store` CLAUDE.md](https://github.com/steipete/stats-store/blob/main/CLAUDE.md)
- [`steipete/deepsec` CONTRIBUTING.md](https://github.com/steipete/deepsec/blob/main/CONTRIBUTING.md)
