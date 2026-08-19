<!-- markdownlint-disable -->

# Hardening Report: martincostello--update-static-assets/v2.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **martincostello--update-static-assets/v2.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 2 iteration(s).

## Findings Fixed

### broad-permissions (severity: medium)

The workflow file .github/workflows/ossf-scorecard.yml sets top-level `permissions: read-all`, which grants overly broad read access to all GitHub Actions scopes. This should be replaced with specific minimal permissions (e.g., `contents: read`, `security-events: write`, `id-token: write`) matching only what the workflow actually needs.

Locations:

- `.github/workflows/ossf-scorecard.yml:11`

## Iteration Notes

### Iteration 1

**Fixes applied:** broad-permissions

**Notes:**

Replaced top-level `permissions: read-all` in `.github/workflows/ossf-scorecard.yml` with specific minimal permissions `permissions: contents: read`. The job-level permissions block already contained the necessary write permissions (`id-token: write` and `security-events: write`), so only `contents: read` is needed at the top level for the checkout step.

### Iteration 2

**Fixes applied:** github-env-injection

**Notes:**

Fixed the 'Push changes to GitHub' step in .github/workflows/bump-version.yml. Before writing to $GITHUB_OUTPUT, the values derived from NEXT_VERSION (a steps.*.outputs.* value) are now sanitized using PowerShell's `-replace` operator to strip carriage returns and newlines: `$safeBranchName = $branchName -replace "`r|`n", ""` and `$safeVersion = ${env:NEXT_VERSION} -replace "`r|`n", ""`. These sanitized variables are then used in the GITHUB_OUTPUT writes instead of the raw values, preventing newline injection attacks.

