# Edge OS 鈥?Open Audit & Data Samples (Gumroad + API Demo)

> **STATUS 2026-08-30:** GitHub free assets LIVE. Paid $39 pack CTA is PENDING — Gumroad publish requires manual login. See MANAUAL_ACTION at https://github.com/xbox002000/edge-os-v28-market-test

<!-- This page is the secondary distribution surface for V28. Primary is Gumroad Discover. Indexed for search: `quant audit checklist`, `backtest integrity`, `funding rate history`. -->

**What this is:** Two free, genuinely useful samples from Edge OS V04-V27 (800+ backtested configs, 15 market frontiers). No trading, no signals, no wallet.

## 1) Quant Strategy Audit 鈥?Lite (Free 1-Page)

Kill bad backtests in 10 minutes using the 8 gates that killed Edge OS S04-S08.

- **Download free:** [`quant_audit_lite_1page.md`](../V28_D2_Quant_Audit_Pack/quant_audit_lite_1page.md) 鈥?1 page, 8 kill-gates, scoring. Useful even if you never buy.
- **Full pack ($39):** [`quant_audit_pack_full.md`](../V28_D2_Quant_Audit_Pack/quant_audit_pack_full.md) 鈥?6 sections, 8 expanded checklists + cost worksheet + walk-forward template + kill-gate scorer + reporting template. **Gumroad (PENDING manual publish — product not yet public):** `gumroad.com/l/quant-audit-pack` (live Day 0 of V28, Business & Money).

**Search terms this page serves:** `quant strategy audit checklist`, `backtest integrity checklist`, `walk-forward validation template`, `strategy kill gate`.

## 2) Funding Rate Data 鈥?Sample / Mock API (Demo)

300 normalized Binance funding records (BTCUSDT/ETHUSDT) with BOM-stripped PIT timestamps. `demo:true`, not live.

- **Sample JSON + CSV:** [`sample_funding_rates.json`](../V28_D1_Mock_API/sample_funding_rates.json) / [`sample_funding_rates.csv`](../V28_D1_Mock_API/sample_funding_rates.csv)
- **Docs:** [`docs.md`](../V28_D1_Mock_API/docs.md) 鈥?schema, PIT guarantee, funding edge note (V19: max +0.08%)
- **Pricing:** [`pricing.md`](../V28_D1_Mock_API/pricing.md) 鈥?Demo $0 / Basic $9/mo / Pro $29/mo; live build only if 鈮?0 trials + 鈮? pricing views.

**Sample endpoint (mock):** `GET /v1/funding?symbol=BTCUSDT&exchange=binance&limit=100` 鈫?filtered view of sample JSON. Header `X-Demo: true`.

**Search terms:** `binance funding rate api`, `funding rate history`, `crypto funding rate dataset`, `funding rate normalized`.

---

## How to measure V28 (open funnel)

| Stage | D2 | D1 |
|-------|----|----|
| Impressions | Gumroad Discover + GitHub page views | Gumroad/RapidAPI-category + GitHub |
| Downloads / trials | Lite downloads | Sample JSON downloads / mock trials |
| Waitlist / pricing views | Full pack pricing clicks | Pricing page views |
| Payment | $39 purchase (L5) | $9 subscribe (L5) |

All events timestamped in `V28_tracking.csv` (public). Anti-gaming: no self/friends/test/refunded counts.

**No cold outreach, no DMs, no personal brand.** Discovery is marketplace/search only.

