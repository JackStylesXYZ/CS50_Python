# Contributing Guide

## Workflow

- Use feature branches by default: `feature/<short-topic>`.
- Open a pull request to `main`.
- Keep PRs small and focused.
- Do not push directly to `main` unless explicitly requested by the maintainer.

## Required Pull Request Checks

A PR is merge-ready only when:
- Quality CI checks pass (lint/type/tests).
- Security CI checks pass (dependency/static/secret/container).
- PR template checklist is fully completed.
- Threat-model impact is documented for security-relevant changes.

## Security Review Expectations

For security-relevant changes, include:
- Threat-model impact note.
- Evidence of negative-path testing (auth/input/authorization).
- Confirmation of session/cookie controls where applicable.
- Confirmation that SQL paths use parameterization.

## Coding Standards

- Follow Python style and typing best practices.
- Keep code simple, maintainable, and testable.
- Prefer small functions and explicit error handling.
- Use environment variables for runtime configuration and secrets.

## Branch Protection (Repository Settings)

Configure `main` with:
- Required pull request reviews (at least 1 approval).
- Required status checks (quality + security workflows).
- Block force pushes.
- Restrict direct pushes to protected branch.
