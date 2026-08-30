# Edge OS — Systematic Strategy Audit & Data Infrastructure

[![Status: Live](https://img.shields.io/badge/Status-LIVE-10B981?style=flat-square)](https://gumroad.com/l/yjpxkw)
[![Framework: 8 Kill--Gates](https://img.shields.io/badge/Framework-8_Kill--Gates-00F0FF?style=flat-square)](quant_audit_lite_1page.md)
[![Format: Markdown & Notion](https://img.shields.io/badge/Format-Markdown_%26_Notion-F59E0B?style=flat-square)](https://gumroad.com/l/yjpxkw)
[![Audited: 800+ Configs](https://img.shields.io/badge/Tested-800%2B_Configs-8B5CF6?style=flat-square)](https://gumroad.com/l/yjpxkw)

![Quant Strategy Audit Pack Cover](assets/gumroad_cover.png)

> **🎯 WHO THIS IS FOR:** Quantitative researchers, systematic traders, and crypto/equity/FX backtesters running trend, momentum, funding carry, statistical arbitrage, or mean-reversion models who need to know if an edge is real before risking capital.

> **⚠️ ANTI-GURU DISCLAIMER:** This product does **NOT** promise alpha, trading signals, or "get-rich" algorithms. It is a ruthless falsification and stress-testing system designed to kill unprofitable backtests before you lose real capital.

---

## 🛑 The Core Problem: Why Backtests Fail in Production

Most backtested strategies collapse when deployed live due to silent structural traps:
- **Timestamp & Lookahead Leakage:** Exact-timestamp matching and survivorship bias.
- **Friction & Fee Denial:** Assuming zero taker fees or unrealistically tight fills.
- **Negative Carry Bleed:** Price momentum being eaten alive by continuous funding payments.

The **8 Kill-Gates Framework** enables you to audit and **kill false edges in 10 minutes** before risking a single dollar.

![The 8 Kill Gates Funnel](assets/preview_kill_gates_funnel.png)

---

## 📥 Instant Free Download (No Email Required)

Get the complete 8-gate scoring table immediately:

👉 [**Download Free 1-Page Audit Lite (`quant_audit_lite_1page.md`)**](quant_audit_lite_1page.md)  
*(1 page, 8 falsification gates, instant scoring. Free forever.)*

---

## 📦 Full Institutional Audit Pack ($39 USD)

The complete systematic falsification toolkit including 6 comprehensive modules:

1. **8 Quantitative Kill-Gates Checklist** (With hard PASS / CONDITIONAL / KILL criteria)
2. **Backtest Integrity & Data Hygiene Checklist** (Encoding, timestamp alignment, look-ahead checks)
3. **Interactive Cost & Friction Model Worksheet** (3-tier taker fees + borrow + carry decomposition)
4. **Walk-Forward & Regime Persistence Worksheet** (Rolling 60/20 window matrix)
5. **7-Criteria Strategy Kill-Gate Scorer** (Standardized 0–5 falsification engine)
6. **Strategy Post-Mortem & Reporting Template** (Audit-ready executive documentation)

👉 [**Direct Buy Full Audit Pack ($39 on Gumroad)**](https://gumroad.com/l/yjpxkw)  
*(Instant Download • Notion & Markdown Ready • 30-Day Money-Back Guarantee)*

---

## 📊 The Friction & Carry Reality Check

A real case study from Edge OS: How naive "Gross +87.4%" backtests evaporate into Net -14.2% losses under institutional friction:

![Cost & Friction Model Reality](assets/preview_cost_worksheet.png)

---

## ⚡ Normalized Funding Rate Dataset (Sample / Mock API)

300 point-in-time normalized Binance funding records (BTCUSDT/ETHUSDT) with verified UTF-8 encoding and zero look-ahead bias:

- **Sample Datasets:** [`sample_funding_rates.json`](sample_funding_rates.json) / [`sample_funding_rates.csv`](sample_funding_rates.csv)
- **API Documentation:** [`docs.md`](docs.md) — PIT guarantees, normalized schema, and funding carry edge analysis.
- **Pricing & Tier Roadmap:** [`pricing.md`](pricing.md) — Demo $0 / Basic $9/mo / Pro $29/mo.

**Mock Endpoint:** `GET /v1/funding?symbol=BTCUSDT&exchange=binance&limit=100`

---

## 📈 Transparent Funnel Tracking

| Funnel Stage | D2: Quant Audit Pack ($39) | D1: Normalized Data API ($9) |
|---|---|---|
| **Discovery** | Gumroad Discover + GitHub Pages | RapidAPI Category + GitHub Docs |
| **Free Evaluation** | [Download 1-Page Lite](quant_audit_lite_1page.md) | [Sample JSON / CSV](sample_funding_rates.json) |
| **Full Version** | [**Gumroad Direct ($39)**](https://gumroad.com/l/yjpxkw) | [API Pricing Tiers](pricing.md) |

*All experiments and conversion events are publicly timestamped in `V28_tracking.csv`.*

<script>
// Dynamic Referral Attribution: Forward ?src= to Gumroad purchase links
document.addEventListener("DOMContentLoaded", function() {
    const urlParams = new URLSearchParams(window.location.search);
    const src = urlParams.get('src');
    if (src) {
        document.querySelectorAll('a[href*="gumroad.com/l/yjpxkw"]').forEach(function(link) {
            const separator = link.href.includes('?') ? '&' : '?';
            link.href = link.href + separator + 'wanted=true&ref=' + encodeURIComponent(src);
        });
    }
});
</script>

