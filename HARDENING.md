<!-- markdownlint-disable -->

# Hardening Report: martincostello--update-static-assets/v3.0.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **martincostello--update-static-assets/v3.0.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### broad-permissions (severity: medium)

The workflow file ossf-scorecard.yml sets top-level `permissions: read-all`, which grants overly broad read access to all GitHub Actions scopes. This should be replaced with specific minimal permissions required by each job. (Note: a zizmor suppression comment is present, but the broad permission grant remains a security concern.)

Locations:

- `.github/workflows/ossf-scorecard.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** broad-permissions

**Notes:**

Replaced the top-level `permissions: read-all` in ossf-scorecard.yml with `permissions: contents: read` (specific minimal permission). Also added `contents: read` to the job-level permissions block (which already had `id-token: write` and `security-events: write`) since job-level permissions completely override top-level ones, ensuring the checkout step has the access it needs. The zizmor suppression comment was removed as it is no longer needed.

