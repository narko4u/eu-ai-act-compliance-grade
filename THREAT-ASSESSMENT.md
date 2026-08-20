# Security Assessment

Status: assessment performed for the current release. This document records
the most likely and impactful potential security problems for this project and
the mitigations in place. It is reviewed before each release.

## What this project is

The eu ai act compliance grade tool: a single-page html assessment tool that grades ai systems against eu ai act obligations.

## Assets

1. **Content/specification integrity** - the published content must not silently change.
2. **Tool correctness** - any shipped tooling must not be tricked into wrong output.
3. **No foothold from use** - consuming the content or running the tooling must not compromise the user's host.

## Likely and impactful problems

| # | Problem | Likelihood | Impact | Mitigation |
|---|---------|------------|--------|------------|
| Misleading grade output | Medium | High | Single authoritative HTML; version-controlled; CI validates |

## Threat model scope

- **In scope:** content integrity, tooling input handling, release integrity.
- **Explicitly out of scope:** transport security of external endpoints the user chooses to reach.

## Attack surface analysis

- Components: index.html (assessment tool).
- CI workflows: least-privilege `contents: read` permissions (plus scoped `security-events: write` for SAST).
