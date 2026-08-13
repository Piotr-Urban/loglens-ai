# LogLens AI — Log format

## Input format

The first version of LogLens AI accepts files in JSON Lines format (`.jsonl`).
Each line contains one independent JSON object representing a log entry.

## Example

```json
{"timestamp":"2026-08-13T10:15:30Z","level":"ERROR","service":"payments-api","message":"Database connection timeout","trace_id":"tr-91","environment":"demo"}

```
## Required fields

| Field | Type | Description |
|---|---|---|
| `timestamp` | ISO 8601 string | Time when the event occurred |
| `level` | string | Log severity |
| `service` | string | Name of the service producing the log |
| `message` | string | Human-readable log message |

## Optional fields

| Field | Type | Description |
|---|---|---|
| `trace_id` | string or null | Identifier connecting related operations |
| `request_id` | string or null | Identifier of an HTTP request |
| `environment` | string or null | Environment such as demo, staging, or production |
| `metadata` | JSON object or null | Additional structured information |

## Accepted log levels

- `DEBUG`
- `INFO`
- `WARNING`
- `ERROR`
- `CRITICAL`

The backend will convert log levels to uppercase before validation.

## Validation rules

- `timestamp` must contain a valid ISO 8601 date and time.
- `level` must be one of the accepted values.
- `service` cannot be empty.
- `message` cannot be empty.
- Unknown fields may be stored inside `metadata`.
- One malformed line must not stop the entire file import.
- Malformed lines must be counted and reported in the import result.

## Example file

```jsonl
{"timestamp":"2026-08-13T10:15:28Z","level":"INFO","service":"checkout-api","message":"Checkout request started","trace_id":"tr-91"}
{"timestamp":"2026-08-13T10:15:30Z","level":"ERROR","service":"payments-api","message":"Database connection timeout","trace_id":"tr-91"}
{"timestamp":"2026-08-13T10:15:32Z","level":"ERROR","service":"checkout-api","message":"Payment request failed","trace_id":"tr-91"}
```