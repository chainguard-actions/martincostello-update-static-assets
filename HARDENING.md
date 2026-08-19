<!-- markdownlint-disable -->

# Hardening Report: martincostello--update-static-assets/v4.0.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **martincostello--update-static-assets/v4.0.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### broad-permissions (severity: medium)

The workflow file ossf-scorecard.yml has a top-level `permissions: read-all` setting, which grants overly broad read access to all GitHub Actions scopes. Even though this is a common recommendation for OSSF Scorecard workflows, the check requires specific minimal permissions rather than the blanket `read-all` grant. It should be replaced with only the specific permissions actually needed (e.g., `id-token: write` and `security-events: write`).

Locations:

- `.github/workflows/ossf-scorecard.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** broad-permissions

**Notes:**

Replaced `permissions: read-all` at the top level of `.github/workflows/ossf-scorecard.yml` with `permissions: {}`. The job-level permissions block already contained the specific minimal permissions needed (`id-token: write` and `security-events: write`), so the workflow functionality is preserved while eliminating the overly broad read-all grant.

