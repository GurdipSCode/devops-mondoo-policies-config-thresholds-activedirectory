# devops-mondoo-policies-config-thresholds-ad-domaincontrollers

Runtime threshold values for **ad-domaincontrollers** Mondoo scans.
Security team owns these values. Platform team owns the MQL checks.

## Contents

| File | Purpose |
|------|---------|
| `base/ad-domaincontrollers-runtime.yaml` | Default thresholds for all environments |
| `production/ad-domaincontrollers-runtime.yaml` | Production overrides (optional) |
| `staging/ad-domaincontrollers-runtime.yaml` | Staging overrides (optional) |

## How it works

The `mondoo-runner` fetches these at scan time, merges base + environment
override via `yq`, and passes the result to `cnspec` as `--props`.
MQL checks reference values like `props.ad-domaincontrollers.tls.min_tls_version`
instead of hardcoding numbers.