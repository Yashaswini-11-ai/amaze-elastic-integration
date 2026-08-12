# Live API Testing

## Tickets API

Status: PASS

Result:
Successfully retrieved live ticket data.

Authentication:
Bearer token validated.

---

## Audit API

Status: PARTIAL PASS

Result:
Endpoint reachable.

Response:
Insufficient role.

Conclusion:
Endpoint exists and authentication works, but current service token lacks required permissions.


# Live API Testing

## Authentication

PASS

Bearer token validated successfully.

## Tickets API

PASS

Live ticket data retrieved from AMaze.

Fields verified:

- id
- title
- status
- src_ip
- protocol
- threat_score
- ttp
- created_at

ECS mappings validated.

## Audit API

Tested.

Endpoint reachable.

Current service token lacks required permissions.

Per discussion, audit validation is not required for MVP completion.

## Overall Result

Live API connectivity verified.

Package validation successful.

elastic-package lint: PASS