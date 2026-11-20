# Security Policy

## Fail-Closed Guarantees

1. **Zero-PII Volatile Processing:** Raw prompts and unredacted PII (Verhoeff-validated 12-digit IDs, PAN, Luhn-validated payment cards, IFSC, Indian mobile numbers, UPI handles, and API/Bearer tokens) remain strictly in volatile request memory and are never logged or persisted to D1, Durable Objects, or audit archives.
2. **India DPDP / RBI Sovereign Geo-Pinning:** Under `INDIA_DPDP_STRICT` and `RBI_SOVEREIGN`, all upstream calls are pinned exclusively to verified Indian regions (`asia-south1`, `ap-south-1`, `asia-south2`, `ap-south-2`). If all Indian endpoints are unavailable, SovereignRoute fails closed with `HTTP 503 SOVEREIGN_ENDPOINT_UNAVAILABLE` with zero cross-border fallback.
3. **AP2 Mandate Cryptography:** Supports Ed25519 and ES256 (P-256) chained `Intent -> Cart -> Payment` bundles with `HTTP 401` on invalid signatures, `HTTP 403` on expired TTL or ceiling breaches, and `HTTP 409` on D1 nonce replay.
4. **Zero-Custody Safe-Harbor:** Holds `₹0.00` customer funds; B2B SaaS plans are billed under SAC 998315 (INR 18% GST) or 0% Export LUT (USD).

## Reporting a Vulnerability

Email `security@srigenmedia.com` with reproduction details. Do not open public GitHub issues for sensitive security reports.
