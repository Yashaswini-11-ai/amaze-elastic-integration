# AMaze Elastic Integration Status

## Project Summary

This project aims to build a native Elastic Integration Package for MirrorMire AMaze.

The integration will allow AMaze alerts, logs, and audit events to be collected, transformed into ECS format, and ingested into Elasticsearch.

---

## Completed

### Research

- Elastic Integration Research
- Okta Integration Analysis
- CrowdStrike Integration Analysis
- Fortinet Integration Analysis

### AMaze Analysis

- AMaze API Analysis
- ECS Mapping Design
- API Inventory

### Package Implementation

- Package Manifest
- Changelog
- Alert Data Stream
- Logs Data Stream
- Audit Data Stream
- Package Icon (`img/amaze-logo.svg`)
- Alerts Overview Dashboard (`kibana/dashboard/amaze-alerts-overview.json`)

### Data Processing

- ECS Field Definitions
- Sample AMaze Events
- Sample ECS Events
- Ingest Pipeline Design
- HTTPJSON Stream Configuration

### Validation

- elastic-package v0.126.0 installed from official GitHub release
- `elastic-package lint` PASSED (fixed 15 validation errors found by the real tooling)
- `elastic-package build` PASSED → `build/packages/amaze-0.1.0.zip`

---

## Data Streams

### Alerts

Source APIs:

- list_tickets
- get_ticket

Purpose:

Collect AMaze alerts and ticket information.

### Logs

Source API:

- get_external_logs

Purpose:

Collect external threat activity and detection logs.

### Audit

Source API:

- list_audit_log

Purpose:

Collect AMaze audit trail events.

---

## ECS Mapping Highlights

| AMaze Field | ECS Field |
|------------|------------|
| src_ip | source.ip |
| dst_ip | destination.ip |
| protocol | network.protocol |
| threat_score | event.severity |
| ttp | threat.technique.id |
| title | event.action |
| status | event.outcome |
| created_at | @timestamp |

---

## Validation Status

Status: PASSED (reproducible with real tooling)

Commands:

```bash
elastic-package lint
elastic-package build
```

- `elastic-package lint` and `elastic-package build` are installed from the official
  [elastic-package](https://github.com/elastic/elastic-package) release `v0.126.0`.
- Lint output: `Done` (clean).
- Build output: `build/packages/amaze-0.1.0.zip` (includes `img/` and `kibana/dashboard/`).

---

## Package Assets

### Icon

- `img/amaze-logo.svg` — 32x32 SVG, registered in `manifest.yml` under `icons`.

### Dashboard

- `kibana/dashboard/amaze-alerts-overview.json` — **AMaze Alerts Overview**.
- Modern by-value panels (Lens + Markdown), filtered to `data_stream.dataset: amaze.alerts`.
- Panels: alerts by action (donut), alerts over time (bar), top MITRE ATT&CK techniques (table), and a welcome markdown panel.
- Follows the package-spec v3 requirements: by-value visualizations (SVR00004), dashboard filter present (SVR00001/SVR00002), no dangling object IDs (SVR00003).

---

## Recommended Next Steps (before registry publishing)

- Run `elastic-package test` against a live stack (requires Docker) to verify ingest pipelines and dashboard rendering end-to-end.
- When MirrorMire obtains an **Elastic partnership**, switch `owner.type` in `package/manifest.yml` from `community` to `partner` (requires an actual partnership — left as `community` for now).
- Add a `_dev/` folder with system tests before publishing to the public registry.