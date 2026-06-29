# Secure Coding Standard

This standard defines mandatory secure coding practices for this repository.

## Authentication And Session Security

- Use strong password hashing (for example Argon2 or bcrypt with modern work factor).
- Store only password hashes, never plaintext or reversible encrypted passwords.
- Session cookies must always set:
  - `HttpOnly=true`
  - `Secure=true` (except explicit local development override)
  - `SameSite=Lax` or stricter
- Rotate session identifiers on login and privilege changes.
- Enforce idle timeout and absolute session expiration.
- Invalidate session on logout server-side.

## Anti-Abuse Controls

- Apply rate limiting on authentication and sensitive endpoints.
- Use lockout/backoff strategy after repeated failed login attempts.
- Enforce input size limits on body, query, and headers.
- Use request schema validation for all external inputs.

## Input Handling And Validation

- Treat all external data as untrusted.
- Validate and normalize inputs at API boundaries.
- Reject unexpected fields and invalid enum values.
- Avoid dynamic code execution patterns.

## SQL And Data Access

- Use parameterized queries/ORM binding only.
- Never concatenate user input into SQL.
- Keep DB roles least-privileged by environment.
- Wrap multi-step writes in explicit transactions.

## Secrets And Configuration

- Never hardcode secrets in source code or tests.
- Keep secrets in environment variables or dedicated secret stores.
- Add placeholders only to `.env.example`; never commit real secret values.

## Logging And Error Handling

- Never log secrets, tokens, or full credential payloads.
- Return safe user-facing errors; keep internal details in structured logs.
- Include request correlation IDs in logs when possible.

## Dependency And Supply Chain Hygiene

- Pin or lock dependencies according to project policy.
- Run dependency security scanning in CI.
- Remove unused dependencies promptly.

## Pull Request Security Requirements

Each PR must confirm:
- Security impact reviewed (or explicitly none).
- New/changed auth flows validated.
- New SQL paths are parameterized.
- No sensitive data exposure in logs or code.
