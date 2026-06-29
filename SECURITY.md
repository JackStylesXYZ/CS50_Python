# Security Policy

## Supported Scope

This repository is actively maintained and security issues are triaged for the current `main` branch.

## Reporting A Vulnerability

Please do not open public issues for suspected vulnerabilities.

Report privately with:
- A clear description of the issue.
- Affected component/path.
- Reproduction steps or proof-of-concept.
- Potential impact and suggested remediation.

## Triage SLA Targets

- **Critical:** acknowledge within 24 hours.
- **High:** acknowledge within 2 business days.
- **Medium/Low:** acknowledge within 5 business days.

These targets are best-effort and may change as project staffing evolves.

## Disclosure Workflow

1. Receive and acknowledge report.
2. Validate impact and affected scope.
3. Prepare and test remediation.
4. Release fix and communicate remediation guidance.
5. Publish post-fix summary when appropriate.

## Secrets And Key Rotation

- Never commit production secrets to git.
- Rotate exposed secrets immediately.
- Rotate long-lived secrets on a scheduled basis where practical.
- Track secret ownership and rotation responsibility in deployment docs.
