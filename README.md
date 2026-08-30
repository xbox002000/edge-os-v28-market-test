# Funding Rate Data — Sample / Mock API (Demo)

**Status:** Demo / sample data. Explicitly labeled `demo: true`. Not live.

**Source sample:** 300 normalized records from Edge OS V17 `btc_funding_rates_full.json` + `eth_funding_rates_full.json` (Binance, fundingTime 1577836800000 window). Normalized fields: `fundingRatePct`, `exchange`, `normalized`, `pitTimestamp`. Original raw had BOM — stripped (see V19 BOM bug).

**What this demo proves:** Unified schema that avoids the V19 pitfall (BOM, drift, rateType). A production API would add Bybit/OKX normalized history + live 8h poll with PIT guarantee. This sample is static to keep infra $0.

## Sample Endpoint (mock)

```
GET /v1/funding?symbol=BTCUSDT&exchange=binance&limit=100

Headers: X-Demo: true
Response: 200 application/json (sample_funding_rates.json filtered)
```

**Sample response (truncated):**

```json
[
  {
    "exchange": "binance",
    "symbol": "BTCUSDT",
    "fundingTime": 1577836800000,
    "fundingRate": "-0.00012359",
    "fundingRatePct": -0.012359,
    "pitTimestamp": 1577836800000,
    "normalized": true,
    "demo": true
  }
]
```

**Use case example — Backtest cost check:**

```js
// fetch sample, compute funding edge
const rows = await fetch('/sample_funding_rates.json').then(r=>r.json());
const fundingEdge = rows.reduce((s,r)=> s + parseFloat(r.fundingRate), 0);
console.log('funding edge sample (300 rows):', fundingEdge); // ~ +0.001 (microscopic, matches S07 +0.08% max [FACT V19])
// Compare price edge: strategy gross must beat this
```

**Documentation:** See `docs.md` for schema, PIT guarantee, rate limits, and funding edge note (V19: carry microscopic, price dominates).

**Pricing (CTA):**

| Plan | Calls/mo | Price | For |
|------|----------|-------|-----|
| Free (demo) | 500 (static sample) | $0 | Integration test with sample |
| Basic | 10k | $9/mo | Single strategy backtest |
| Pro | 100k + alerts | $29/mo | Monitor + history |

Billing via RapidAPI (25% take) [FACT] or direct Stripe — no infra beyond static JSON + docs. Live API build only if V28 E1 ≥50 trials + ≥3 pricing views.

**Anti-misrepresentation:** This endpoint is labeled Demo/sample and serves static JSON. Live docs state "Demo — sample data, not live" prominently.

## Files
- `sample_funding_rates.json` — 300 records, normalized, demo:true
- `sample_funding_rates.csv` — same
- `docs.md` — schema + PIT + funding edge note
- `pricing.md` — pricing page copy
