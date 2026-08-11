# AMaze Ingestion Plan

## Source APIs

- list_tickets
- get_ticket
- get_external_logs
- list_audit_log

## Data Flow

AMaze API
    ↓
Elastic Integration
    ↓
alerts data stream
    ↓
Elasticsearch
    ↓
Kibana

## ECS Transformation

src_ip → source.ip

dst_ip → destination.ip

threat_score → event.severity

ttp → threat.technique.id

created_at → @timestamp