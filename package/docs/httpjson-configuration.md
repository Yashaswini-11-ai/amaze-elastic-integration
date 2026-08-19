# HTTPJSON Configuration

The AMaze integration uses the Elastic Agent `httpjson` input to poll the
MirrorMire AMaze REST API (v3) on a configurable interval.

## Endpoints

| Data stream | Endpoint | Method | Pagination |
|-------------|----------|--------|------------|
| `alerts` | `{{base_url}}/tickets` | GET | Cursor (`from`, `limit`) |
| `audit` | `{{base_url}}/audit-log` | GET | Cursor (`from`, `limit`) |
| `logs` | `{{base_url}}/external/logs` | GET | Page (`page`, `limit`) |

`{{base_url}}` includes the API path, e.g.
`https://dashboard.mirrormire.ai/api/v3`.

## Authentication

Bearer token (JWT or API token), sent as:

```http
Authorization: Bearer <token>
```

The token must have permission to read the resources above. Audit collection
additionally requires an admin/auditor role.

## TLS Verification

By default the client verifies the server certificate (`verify: true`). Set
**Verify TLS Certificates** to `false` only for self-signed or on-prem
instances.

## Polling Interval

Each data stream polls on the configured **Collection Interval** (default
`5m`). On the first poll, the `alerts` and `audit` streams look back the
**Initial Collection Interval** (default `24h`) using the `from` parameter.
Subsequent polls use a cursor of the last seen timestamp to only fetch new
events.

The `logs` stream is page-paginated (`page`/`limit`); because the logs API has
no timestamp filter, re-polling may return the same recent events.

## Response Processing

AMaze API
      ↓
HTTPJSON Input
      ↓
Ingest Pipeline
      ↓
ECS Mapping
      ↓
Elastic Data Stream