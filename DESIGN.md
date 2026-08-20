# Design: eu-ai-act-compliance-grade

This document describes the design of the EU AI Act Compliance Grade tool: a single-page HTML assessment tool that grades AI systems against EU AI Act obligations: the actors, the actions
they perform, and the data flow. It accompanies
[THREAT-ASSESSMENT.md](THREAT-ASSESSMENT.md) (threat model) and
[TESTING.md](TESTING.md) (test policy).

## Purpose

The eu ai act compliance grade tool: a single-page html assessment tool that grades ai systems against eu ai act obligations.

## Actors

| Actor | Description |
| --- | --- |
| Assessor | Uses index.html to grade an AI system against EU AI Act articles. |
| Content steward | Maintains index.html. |

## Actions

| Action | Performed by | Implemented in |
| --- | --- | --- |
| Run assessment | Assessor | `index.html` |
| Validate files | CI | `docs-ci.yml` |

## Data flow

```
repository (main branch)
        │
        ▼
CI (on push / pull_request) ──► validate / test / security jobs
        │
        ▼
tagged release ──► build artifacts + CycloneDX SBOM + Sigstore signatures + SHA256SUMS
```

## Design invariants

1. **Open by construction.** The content is freely licensed and version-controlled.
2. **Minimal dependencies.** Fewer dependencies means a smaller attack surface.
3. **Tamper-evident releases.** Where releases exist, assets carry Sigstore signatures and checksums.
