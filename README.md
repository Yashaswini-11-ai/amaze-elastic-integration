# MirrorMire AMaze Elastic Integration

This repository contains research and implementation planning for building a native Elastic Integration Package for MirrorMire AMaze.

## Research Completed

- Okta Integration Analysis
- CrowdStrike Integration Analysis
- Fortinet FortiGate Integration Analysis
- ECS Mapping Research
- Elastic Package Structure Study

## Key Findings

- Elastic integrations follow a standard package structure.
- Packages use manifest.yml, data streams, ECS mappings, dashboards, and validation assets.
- AMaze currently does not support OpenTelemetry.
- API-based (httpjson) and Webhook-based ingestion are the recommended approaches.

## Proposed AMaze Package Structure

packages/amaze/

├── manifest.yml
├── changelog.yml
├── validation.yml
├── data_stream/
│   └── alerts/
├── kibana/
├── docs/
└── img/

## Repository Contents

research/
- integration-study.md
- ecs-mapping.md

## Next Steps

1. Complete AMaze ECS mappings
2. Create package skeleton
3. Build ingest pipeline
4. Create Kibana dashboards
5. Validate using elastic-package
6. Build proof of concept (POC)

## Goal

Enable AMaze to become a native Elastic Integration that can eventually be published through the Elastic Package Registry and installed from the Kibana Integrations Catalog.
