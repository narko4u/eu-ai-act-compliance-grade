# WitnessOS EU AI Act Compliance Grade

[![OpenSSF Best Practices - Baseline 1](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fwww.bestpractices.dev%2Fprojects%2F14147.json&query=badge_percentage_baseline_1&label=OpenSSF%20Baseline%201&suffix=%25&color=success)](https://www.bestpractices.dev/projects/14147) [![OpenSSF Best Practices - Baseline 2](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fwww.bestpractices.dev%2Fprojects%2F14147.json&query=badge_percentage_baseline_2&label=OpenSSF%20Baseline%202&suffix=%25&color=success)](https://www.bestpractices.dev/projects/14147) [![OpenSSF Best Practices - Baseline 3](https://img.shields.io/badge/dynamic/json?url=https%3A%2F%2Fwww.bestpractices.dev%2Fprojects%2F14147.json&query=badge_percentage_baseline_3&label=OpenSSF%20Baseline%203&suffix=%25&color=success)](https://www.bestpractices.dev/projects/14147)

**Status:** DRAFT — Ready for Sovereign review and deployment to empirelabs.site/witnessos/grade

## Overview

A self-contained single-page HTML tool that helps enterprises assess their AI agent governance readiness against the EU AI Act — with 19 days to enforcement (2 August 2026).

**Strategy:** Proven lead-gen format (personal, quantifiable, shareable compliance grade). No competitor has published a self-assessment tool. 73% of enterprises lack AI runtime security — this creates the fear hook. Captures emails for warm follow-up without cold outreach.

## Features

- **Countdown timer** to EU AI Act enforcement date (2 August 2026), updated every second client-side
- **6 yes/no questions** mapping to specific EU AI Act articles (Art 2, 9, 10, 12, 14, 28)
- **A–F scoring algorithm** based on 6 weighted compliance dimensions:
  - Real-time agent monitoring (Art 14)
  - Credential-level access controls (Art 10)
  - Event-sourced audit trails (Art 12)
  - Decommissioning policy (Art 9)
  - Vendor governance requirements (Art 28)
  - EU-facing operations scope (Art 2 — guidance, not scored)
- **Shareable scorecard** — exports as PNG image via HTML Canvas
- **Email capture** with enterprise context (company size, role, agent count, industry)
- **Client-side only** — zero server dependencies, no API calls
- **LocalStorage persistence** — submissions stored locally (ready for server-side capture)

## What's in this directory

| File | Purpose |
|------|---------|
| `index.html` | Self-contained single-page compliance grade assessment tool |
| `README.md` | This file — setup instructions |
| `.github/workflows/test.yml` | CI workflow (HTML validation, content checks) |
| `test_compliance_grade.py` | Validation tests |

## How to deploy

### Option A: empirelabs.site
1. Copy `index.html` to `/mnt/c/VaultSentinel/HermesGenesis/site/witnessos/grade/index.html`
2. Verify the path exists and is served by the site's static file handler
3. Test: visit `https://empirelabs.site/witnessos/grade`
4. Submit a test assessment to verify grade calculation + email capture

### Option B: GitHub Pages / Netlify
1. Push directory to GitHub
2. Configure GitHub Pages or Netlify to serve from the directory
3. Set custom domain if needed

### Post-deployment
1. Verify the countdown timer displays correctly
2. Submit a test with all "no" answers — should return grade F
3. Submit a test with all "yes" answers — should return grade A
4. Test PNG export works in Chrome, Firefox, Safari
5. Test email capture — verify submission is stored

## Acceptance criteria

- [ ] Deployed and accessible at empirelabs.site/witnessos/grade
- [ ] Countdown timer to 2 Aug 2026 displays and updates
- [ ] All 6 questions functional (yes/no radio buttons)
- [ ] Scoring algorithm returns correct grade for each input combination
- [ ] PNG scorecard export works
- [ ] Share link copies to clipboard
- [ ] Email + context fields captured on submission
- [ ] Reset function clears all selections

## Edge cases

| Edge case | Handling |
|-----------|----------|
| Invalid email | Form blocks submission with error message |
| Missing questions | Form blocks submission — all 6 required |
| Deadline passed | Timer shows "DEADLINE PASSED" message |
| Browser without Canvas | Scorecard export hidden gracefully |
| Mobile devices | Responsive layout with stacked radio buttons |
| EU AI Act delay | Update deadline in code if enforcement is postponed |

## Scoring Algorithm

| Score | Grade | Label |
|-------|-------|-------|
| 6/6 (90%+) | A | Strong Compliance — Ahead of deadline |
| 5/6 (70%+) | B | Good Compliance — Minor gaps remain |
| 4/6 (50%+) | C | Moderate Compliance — Action needed |
| 3/6 (30%+) | D | Below Standard — Significant gaps |
| 2/6 (15%+) | E | Weak Compliance — Urgent action |
| 0-1/6 (<15%) | F | Non-Compliant — Critical gaps |

Note: Q1 (EU-facing ops) is guidance-only and not scored. Effective max score is 5/5 on scored questions.

## Cost

$0. Static HTML, zero dependencies. 24h build effort.


---

<sub>Part of the [WitnessOS launch family](https://github.com/narko4u/witnessos): [witnessos-alpha](https://github.com/narko4u/witnessos-alpha) · [eu-ai-act-compliance-grade](https://github.com/narko4u/eu-ai-act-compliance-grade) · [witnessos-verifier](https://github.com/narko4u/witnessos-verifier) · [agent-interaction-specs](https://github.com/narko4u/agent-interaction-specs) · [aci-spec](https://github.com/narko4u/aci-spec) · [aip-spec](https://github.com/narko4u/aip-spec) · [ajson](https://github.com/narko4u/ajson) — [Empire Labs Pty Ltd](https://www.empirelabs.com.au)</sub>