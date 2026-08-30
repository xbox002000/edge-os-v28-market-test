# Funding Rate API — Docs (Mock / Demo)

**Version:** v1-demo (static sample). Production would be v1-live with 3-exchange normalization.

## Schema

| Field | Type | Notes |
|-------|------|-------|
| exchange | string | `binance` (sample); prod: `binance`/`bybit`/`okx` |
| symbol | string | `BTCUSDT`, `ETHUSDT` |
| fundingTime | int64 ms | PIT settlement time, BOM-stripped |
| fundingRate | string | Raw as exchange sends (e.g., "-0.00012359") |
| fundingRatePct | number | `fundingRate * 100` for readability |
| pitTimestamp | int64 | = fundingTime, explicit PIT |
| normalized | bool | true if cross-venue normalized |
| demo | bool | true for sample; false for live |

**PIT guarantee:** `pitTimestamp` is settlement, not mark. V19 lesson: raw had BOM — demo strips BOM on load. Check `file -b` if adding BYBIT.

## Endpoints (demo)

- `GET /sample_funding_rates.json` — 300 rows
- `GET /sample_funding_rates.csv`
- `GET /v1/funding?symbol=BTCUSDT&exchange=binance&limit=N` — mock filter on sample (client-side)

## Funding edge note

From V19 S07 audit (72 configs, 5 technical survivors, funding edge negative for all, max +0.08%): funding/carry is **microscopic** vs price trend. This API surfaces the split:

```
Total PnL = Price PnL + Funding PnL
Funding edge = sum(fundingRate) over holding window
If Funding edge <=0, your "carry" is price beta — kill it per Gate 4.
```

Use this sample to compute funding edge before claiming carry.

## Rate limits (demo)

500 calls/mo on sample (static, $0 infra). Production Basic 10k $9/mo, Pro 100k $29/mo + alerts (RapidAPI 25% take [FACT] baked into net $1.00/hr calc).

## Anti-misrepresentation

Every response includes `"demo": true` and header `X-Demo: true`. Docs front page: "Demo / sample data. Not live." Do not represent static as live.

## Next step if V28 passes

If E1 ≥50 trials + ≥3 pricing views, build production crawler for Bybit/OKX with same normalized schema + status page. Budget $20 VPS, 15hr build, 3-5hr/week support — violates <5hr unless docs exceptional, so support shadow cost must stay proven.

