# splunk-terraform-resources -- TOML resource specs for Splunk

> **★★★ CSE / Knowable Construction.** This repo operates under **Constructive Substrate Engineering** — canonical specification at [`pleme-io/theory/CONSTRUCTIVE-SUBSTRATE-ENGINEERING.md`](https://github.com/pleme-io/theory/blob/main/CONSTRUCTIVE-SUBSTRATE-ENGINEERING.md). The Compounding Directive (operational rules: solve once, load-bearing fixes only, idiom-first, models stay current, direction beats velocity) is in the org-level pleme-io/CLAUDE.md ★★★ section. Read both before non-trivial changes.


Declarative TOML specifications for 4 Splunk Terraform resources. Same pattern
as `akeyless-terraform-resources`. Consumed by iac-forge and pangea-forge to
generate code for all IaC platforms.

## Structure

```
provider.toml              # Provider config (url, username, password)
resources/
  apps/
    apps_local.toml        # splunk_apps_local
  indexes/
    indexes.toml           # splunk_indexes
  inputs/
    http_event_collector.toml  # splunk_inputs_http_event_collector
  saved_searches/
    saved_searches.toml    # splunk_saved_searches
```

## Usage

```bash
# Generate Terraform provider code
iac-forge-cli generate --specs . --backend terraform

# Generate Pangea Ruby resources
iac-forge-cli generate --specs . --backend pangea

# Generate all backends
iac-forge-cli generate --specs . --backend all
```

## TOML Spec Format

Same schema as `akeyless-terraform-resources`. Each `.toml` file defines one
resource with `[resource]` metadata and `[resource.attributes.*]` for fields.

## Provider Auth

```toml
[provider.auth]
url      = { type = "String", required = true, env = "SPLUNK_URL" }
username = { type = "String", required = true, env = "SPLUNK_USERNAME" }
password = { type = "String", required = true, sensitive = true, env = "SPLUNK_PASSWORD" }
```

## Resources (4)

apps_local, indexes, http_event_collector (HEC), saved_searches.
