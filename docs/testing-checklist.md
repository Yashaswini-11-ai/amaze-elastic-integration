# Testing Checklist

## Authentication

- Verify base_url is reachable
- Verify bearer_token is valid
- Verify TLS verification setting works

## Alerts Stream

- list_tickets returns data
- list_tickets fields map correctly to ECS
- get_ticket returns detailed ticket information
- event.id mapping verified
- source.ip mapping verified
- destination.ip mapping verified
- event.severity mapping verified
- threat.technique.id mapping verified

## Logs Stream

- get_external_logs returns data
- get_internal_logs returns data
- get_ot_logs returns data
- get_ad_logs returns data
- get_ai_threats_logs returns data
- source.ip mapping verified
- network.protocol mapping verified
- event.severity mapping verified

## Audit Stream

- list_audit_log returns data
- actor mapped to user.email
- action mapped to event.action
- timestamp mapped to @timestamp

## Ingest Pipeline

- Source IP transformation works
- Destination IP transformation works
- Threat score transformation works
- MITRE TTP transformation works
- Timestamp transformation works

## Validation

- elastic-package lint passes
- Sample events are valid
- ECS sample