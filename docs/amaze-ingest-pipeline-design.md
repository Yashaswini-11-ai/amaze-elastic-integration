# AMaze Ingest Pipeline Design

## Source APIs

- list_tickets
- get_ticket
- get_external_logs
- list_audit_log

## ECS Transformations

src_ip -> source.ip

dst_ip -> destination.ip

threat_score -> event.severity

ttp -> threat.technique.id

created_at -> @timestamp

status -> event.outcome

title -> event.action