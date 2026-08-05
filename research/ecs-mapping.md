# AMaze to ECS Mapping

## Initial ECS Mapping

| AMaze Field | ECS Field | Type |
|------------|------------|------|
| event_id | event.id | keyword |
| timestamp | @timestamp | date |
| attacker_ip | source.ip | ip |
| severity | event.severity | long |
| protocol | network.protocol | keyword |
| mitre_attack | threat.technique.id | keyword |
| decoy_name | host.name | keyword |
| session_duration | event.duration | long |

## Additional Metadata

observer.vendor = mirrormire

observer.product = amaze

event.kind = alert