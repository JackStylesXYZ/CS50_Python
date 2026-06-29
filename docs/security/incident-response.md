# Incident Response Runbook

This runbook defines a minimal incident response flow for this project.

## 1) Detect

Identify potential incidents via:
- Security CI failures.
- Secret leak detections.
- Authentication abuse spikes.
- Runtime error anomalies suggesting compromise.

## 2) Triage

- Classify severity (Critical/High/Medium/Low).
- Identify affected systems, users, and data.
- Assign an incident owner.

## 3) Contain

- Revoke/rotate potentially exposed secrets.
- Disable vulnerable endpoints/features when needed.
- Isolate affected runtime components.

## 4) Eradicate And Recover

- Patch root cause.
- Validate remediation with tests and scans.
- Restore normal service with monitoring.

## 5) Post-Incident Review

- Document timeline and impact.
- Capture root cause and contributing factors.
- Record corrective actions with owners and due dates.

## Communication Principles

- Share facts, not speculation.
- Avoid disclosing sensitive exploit details publicly before mitigation.
- Notify affected stakeholders promptly based on severity.
