# AMaze Elastic Integration Design

## Objective

Build a native Elastic Integration Package for MirrorMire AMaze.

The integration will collect AMaze security events and make them available inside Elastic Security and Kibana.

---

## APIs Used

The following APIs were identified from the existing AMaze Shuffle application:

### Ticket APIs

- list_tickets
- get_ticket
- update_ticket
- delete_ticket

### Log APIs

- get_external_logs

### Audit APIs

- list_audit_log

### Report APIs

- list_report_runs

---

## Initial MVP Scope

The first Elastic integration version should focus on:

- Ticket ingestion
- Detection log ingestion
- Audit log ingestion

This provides immediate visibility into AMaze detections.

---

## Proposed Data Stream

data_stream/alerts

Purpose:

- Store AMaze alerts
- Store ticket information
- Store threat activity

---

## ECS Mapping

Reference:

research/ecs-mapping.md

Important mappings:

- src_ip → source.ip
- dst_ip → destination.ip
- threat_score → event.severity
- ttp → threat.technique.id
- created_at → @timestamp

---

## Proposed Package Structure

packages/amaze/

├── manifest.yml

├── changelog.yml

├── validation.yml

├── data_stream/
│   └── alerts/

├── kibana/

├── docs/

└── img/

---

## Future Scope

Future versions may support:

- Honeytokens
- Neural Echo
- GateKeeper
- AI-SCA
- Advanced dashboards
- Automated detections

---

## Next Steps

1. Finalize ECS mappings
2. Create package skeleton
3. Create fields.yml
4. Build ingest pipeline
5. Create dashboards
6. Validate package
7. Build proof of concept