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

### Data Processing

- ECS Field Definitions
- Sample AMaze Events
- Sample ECS Events
- Ingest Pipeline Design
- HTTPJSON Stream Configuration

### Validation

- Go Installation
- elastic-package Installation
- Package Validation
- elastic-package lint PASSED

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

Status: PASSED

Command:

```bash
elastic-package lint