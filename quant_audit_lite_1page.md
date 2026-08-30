# Quant Strategy Audit — Lite (Free 1-Page)

**Purpose:** Kill bad strategies before you deploy them. This is the 8-gate filter that killed 800+ Edge OS configs (V04-V19). Use it on any backtest in 10 minutes.

| # | Kill-Gate | Check (PASS = 1, FAIL = 0) | Your Score |
|---|-----------|-----------------------------|------------|
| 1 | **Cost Model** | Did you include 0.15% / 0.30% / 0.50% round-trip and funding/borrow? Re-run at 0.50% — still positive? | /1 |
| 2 | **Baseline** | Did you beat Buy & Hold (or 60/40) on the SAME period/costs? Strategy +20% vs Buy & Hold +22% = FAIL | /1 |
| 3 | **OOS Split** | Is your TEST (last 20%) untouched until final run? No peeking, no re-tuning after seeing TEST | /1 |
| 4 | **Funding/Carry Edge Split** | Decompose P&L: price vs carry/funding. Funding edge >0? S07 max +0.08% proves price-driven "carry" is fake | /1 |
| 5 | **Leakage / PIT** | No future info: no close[0] as signal for close[0], timestamps are PIT, delisting/survivorship handled? | /1 |
| 6 | **Walk-Forward** | Rolling 60/20 window: median OOS still >0 after costs? Single split success = overfit | /1 |
| 7 | **Friction Robustness** | Spread + slippage + borrow + fee sensitivity table (see S07). Funding/BOM bug? (V19 BOM killed S07 JSON) | /1 |
| 8 | **Kill-Gate Economics** | Net / human hour > $6/hr and net >4% RFR after fees/infra/shadow cost? If $500 * 4% = $20/yr hurdle fails, KILL | /1 |

**Scoring:** 8/8 PASS → CONDITIONAL (needs 12mo live). 6-7/8 → CONDITIONAL with fix list. ≤5/8 → **KILL**. Edge OS: S05 0/324 survived (all VAL negative), S07 funding edge negative for all — pure beta.

**What this lite misses:** Full checklists have 5-10 sub-items per gate, worksheets, and reporting template.

---
**CTA:** **Quant Strategy Audit Pack ($39)** — Full pack: 8 expanded checklists + cost model worksheet + walk-forward template + kill-gate scorer + result reporting template. Built from Edge OS V04-V26 (800+ configs, 15 market frontiers). No alpha claims. Gumroad: `gumroad.com/l/quant-audit-pack` (placeholder — live Day 0 of V28).
