# APIsec Surface scan (customer trigger, pip-package variant)

One workflow file. It installs the `apisec-orgscan` package and calls its commands; the package holds all the scan logic, so updates arrive through the package version. GitHub Actions keeps only the matrix fan-out, runner selection and artifact storage.

## Setup

1. **Use this template** to create this repository in the organization to scan.
2. Org secrets: `APISEC_TOKEN` (required), `ORG_READ_TOKEN` (recommended; Contents: read and Metadata: read).
3. Org variable: `APISEC_ENDPOINT`.
4. Actions tab, **Run workflow**, tick `dry_run`, run once. The nightly schedule takes it from there.

Optional org variables: `APISEC_RUN_PROFILE` (`surface` default or `legacy`), `APISEC_LLM_ENRICHMENT` (`1` to opt in; off by default), `THROUGHPUT` (1 to 6), `ORCHESTRATOR_RUNNER` (`github-hosted` default or `self-hosted`), `TARGET_ORG`, `EXCLUDE_REPOS`, `APISEC_CLI_VERSION`, `ORGSCAN_VERSION` (package tag to install; default `v1`).

Source code is read only on this organization's runners and never reaches APIsec. Only the Surface analysis manifest is uploaded.
