# AMaze to ECS Mapping

| AMaze Field | ECS Field | Type |
|------------|------------|------|
| id | event.id | keyword |
| created_at | @timestamp | date |
| src_ip | source.ip | ip |
| dst_ip | destination.ip | ip |
| protocol | network.protocol | keyword |
| threat_score | event.severity | long |
| ttp | threat.technique.id | keyword |
| title | event.action | keyword |
| status | event.outcome | keyword |

## Additional Metadata

observer.vendor = mirrormire

observer.product = amaze

event.kind = alert