# Threat Model

This document captures the security assumptions for this project and must be updated whenever we add:
- Authentication or session behavior changes.
- New external integrations (for example exchange APIs/websockets).
- New data flows or storage.

## 1) System Context

Primary components:
- Web/API application (Python).
- PostgreSQL database.
- External market data providers (REST + WebSocket).
- Browser clients.

Primary trust boundaries:
- Public internet -> application.
- Application -> database.
- Application -> third-party APIs.
- CI/CD pipeline -> deployed artifacts.

## 2) Assets

Security-sensitive assets:
- User account records and password hashes.
- Session identifiers and auth cookies.
- API credentials/secrets.
- Application logs and audit-relevant events.
- Deployment artifacts and dependency graph.

## 3) Threat Actors

- Anonymous internet attacker.
- Authenticated but malicious user.
- Compromised third-party dependency.
- Insider or accidental operational misconfiguration.

## 4) High-Risk Abuse Cases

- Credential stuffing and brute-force against login.
- Session theft (cookie replay or insecure attributes).
- SQL injection through untrusted input.
- SSRF-like misuse via external API parameters.
- Secret leakage in source code, logs, or CI output.
- Supply-chain compromise from vulnerable dependencies.

## 5) Mitigation Baseline

Required controls:
- Parameterized SQL only; no string-built queries.
- Strong password hashing and safe session management.
- Rate limiting and lockout/backoff for auth endpoints.
- Input validation and strict schema validation.
- Least privilege DB users and restricted network access.
- Secret management via environment/secret stores only.
- Continuous dependency and image scanning in CI.

## 6) Residual Risks

- Third-party API reliability and data integrity issues.
- Operational mistakes during early project stages.

Track accepted residual risks in PR descriptions with an explicit rationale and follow-up action.

## 7) Change Trigger Checklist

Update this threat model when a PR introduces:
- New endpoint handling auth/session data.
- New DB tables containing user/security-relevant fields.
- New background workers or message flows.
- New container/service or deployment topology changes.
