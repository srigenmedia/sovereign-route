# 14-Day Shadow Audit Guide

Run SovereignRoute in `shadow` mode (`X-SovereignRoute-Mode: shadow`) to measure exact token cost savings and PII redaction coverage before switching to `enforce` mode.

## Quickstart

```bash
curl -sS -X POST "https://route.srigenmedia.com/api/v1/classify" \
  -H "Authorization: Bearer ${SOVEREIGN_ROUTE_API_KEY}" \
  -H "X-SovereignRoute-Policy: INDIA_DPDP_STRICT" \
  -H "X-SovereignRoute-Mode: shadow" \
  -H "Content-Type: application/json" \
  -d '{"prompt":"Summarize this JSON payload into 3 bullet points."}'
```

## Proof-of-Savings Endpoints

- `GET /api/v1/savings/report` — Returns 14-day `baseline_usd`, `actual_usd`, `savings_usd`, `fee_12pct_usd`, and `net_roi_multiple`.
- `GET /api/v1/telemetry/stream` — Real-time Server-Sent Events (SSE) snapshot stream.
- `POST /api/v1/shadow/export` — Exports a SHA-256 hash-chained, signed JSON audit bundle.
