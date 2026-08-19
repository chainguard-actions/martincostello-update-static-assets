<!-- markdownlint-disable -->

# Hardening Report: martincostello--update-static-assets/v4.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **martincostello--update-static-assets/v4.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### broad-permissions (severity: medium)

The workflow file ossf-scorecard.yml has a top-level `permissions: read-all` setting. This grants overly broad read access across all scopes and should be replaced with specific minimal permissions (e.g., `contents: read`, `security-events: write`, `id-token: write`) rather than the blanket `read-all` grant.

Locations:

- `.github/workflows/ossf-scorecard.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** broad-permissions

**Notes:**

Replaced `permissions: read-all` at the top level of `.github/workflows/ossf-scorecard.yml` with specific minimal permissions: `contents: read` and `actions: read`. The job-level permissions (`id-token: write` and `security-events: write`) were already correctly scoped and were left unchanged.

