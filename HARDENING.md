<!-- markdownlint-disable -->

# Hardening Report: martincostello--update-static-assets/v4.0.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **martincostello--update-static-assets/v4.0.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### broad-permissions (severity: medium)

The workflow file ossf-scorecard.yml has a top-level `permissions: read-all` which grants overly broad read access to all scopes. Even though this is a common recommendation for OSSF Scorecard, the check requires specific minimal permissions rather than `read-all` or `write-all`.

Locations:

- `.github/workflows/ossf-scorecard.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** broad-permissions

**Notes:**

Replaced the top-level `permissions: read-all` in `.github/workflows/ossf-scorecard.yml` with specific minimal permissions: `contents: read` and `actions: read`. The job-level permissions (`id-token: write` and `security-events: write`) were already properly scoped and were left unchanged. The zizmor ignore comment was also removed since the permissions are now properly minimal.

