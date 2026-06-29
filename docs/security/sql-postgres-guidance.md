# SQL And PostgreSQL Security Guidance

This project uses a security-first posture for database design and query execution.

## Query Safety

- Use parameterized queries only.
- Never build SQL strings with untrusted input.
- Prefer query builders/ORM parameter binding where possible.
- Validate sort/filter fields against explicit allowlists.

## Privilege Model

- Use separate DB roles for application runtime and migrations.
- Grant least privilege required for each role.
- Avoid using superuser roles in application runtime.

## Connection And Transport

- Enforce encrypted transport when available (`sslmode=require` in non-local environments).
- Use connection pooling with bounded limits.
- Fail fast on auth/connection errors and retry with bounded backoff.

## Schema And Migration Discipline

- Every schema change must be delivered via migration.
- Review destructive migrations explicitly (drop/rename/high-lock operations).
- Include rollback or mitigation notes for risky migrations.

## Data Integrity And Transactions

- Use explicit transactions for multi-step state changes.
- Define foreign keys and constraints to enforce integrity.
- Use unique constraints to prevent duplicate security-sensitive records.

## Sensitive Data Handling

- Minimize stored sensitive data; avoid storing unnecessary PII.
- Never store plaintext credentials or tokens.
- Apply retention and deletion policy from `data-protection.md`.

## Operational Safety

- Log query failures without exposing raw secrets/user payloads.
- Use maintenance windows and migration verification for production changes.
- Monitor failed auth attempts and unusual query error spikes.
