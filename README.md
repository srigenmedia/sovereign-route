# SovereignRoute + AP2 (`io.github.srigenmedia/sovereign-route`)

[![mcptry](https://mcptry.com/badge/io.github.srigenmedia/sovereign-route)](https://mcptry.com/servers/io.github.srigenmedia/sovereign-route)

**India DPDP/RBI Geo-Pinned `<5ms` LLM Router with AP2 Mandates, `x402`/`MPP` Billing & 12% FinOps (`https://route.srigenmedia.com`)**

SovereignRoute routes AI inference across Indian sovereign cloud endpoints (`asia-south1`, `ap-south-1`, `asia-south2`, `ap-south-2`), scrubs regulated Indian PII in volatile request memory before upstream dispatch, enforces cryptographic AP2 (`Intent -> Cart -> Payment`) mandates, and caps runaway agent spend atomically.

## Endpoints

- **FinOps Cockpit:** `https://route.srigenmedia.com`
- **Streamable HTTP MCP Endpoint:** `https://route.srigenmedia.com/mcp`
- **OpenAI-Compatible Chat Completions:** `https://route.srigenmedia.com/v1/chat/completions`
- **Health Check:** `https://route.srigenmedia.com/health`

## MCP Client Configuration (`mcp_config.json`)

```json
{
  "mcpServers": {
    "sovereign-route": {
      "type": "streamable-http",
      "url": "https://route.srigenmedia.com/mcp",
      "headers": {
        "Authorization": "Bearer ${SOVEREIGN_ROUTE_API_KEY}"
      }
    }
  }
}
```

## Available MCP Tools

1. `route_classify_prompt` — Scrub regulated Indian PII in volatile memory, classify prompt complexity in `<5ms`, and resolve a DPDP/RBI geo-pinned upstream region.
2. `route_get_savings_ledger` — Inspect live `RouteBudgetCoordinatorDO` daily/monthly USD spend and freeze state.
3. `route_verify_ap2_mandate` — Verify an Ed25519 or ES256 chained AP2 `Intent -> Cart -> Payment` mandate bundle against TTL, ceiling, and D1 anti-replay nonces.
4. `route_trigger_budget_freeze` — Atomically freeze/unfreeze a tenant spend coordinator and dispatch a `<50ms` Kavach KYA kill-switch sync.

## 14-Day Shadow Audit & License

See [docs/14-day-shadow-audit.md](docs/14-day-shadow-audit.md) for the 14-day zero-risk shadow audit guide and [SECURITY.md](SECURITY.md) for our zero-PII and fail-closed security architecture. Released under the [MIT License](LICENSE).
