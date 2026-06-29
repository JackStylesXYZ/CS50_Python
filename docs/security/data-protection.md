# Data Protection Standard

This document defines how data is classified, retained, and protected in this project.

## Data Classification

- **Public:** content safe for public display.
- **Internal:** operational metadata not intended for public exposure.
- **Sensitive:** authentication/session data, user account details, secrets, security events.

Default rule: treat unknown data as **Sensitive** until classified.

## Storage Rules

- Store only required data; avoid collecting unnecessary personal data.
- Never store plaintext passwords or secret keys.
- Use strong password hashing for credentials.
- Use DB constraints to preserve data integrity.

## Transmission Rules

- Use HTTPS/TLS for all non-local traffic.
- Avoid sending sensitive fields unless required by endpoint contract.

## Logging Rules

- Do not log secrets, session tokens, full auth payloads, or raw credentials.
- Redact sensitive fields in structured logs.
- Use correlation IDs for traceability without exposing private data.

## Retention And Deletion

- Define retention windows for user and security-related records.
- Implement deletion/cleanup behavior for expired sessions and stale security data.
- Document exceptions where legal/operational retention is required.

## Access Control

- Apply least privilege for service accounts and DB roles.
- Restrict production data access to authorized users only.
- Review access permissions periodically.

## Security Verification

Every data-impacting PR must confirm:
- Data classification impact.
- Retention/deletion impact.
- Logging redaction impact.
