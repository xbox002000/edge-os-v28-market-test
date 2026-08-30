# Quant Strategy Audit Pack — Full ($39)

**Positioning:** "The checklist that killed 800+ configs so you don't deploy one." Not a strategy. Not alpha. A kill-gate system.

**Source:** Edge OS V04-V26 — 800+ strategy configs (S04 trend, S05 cross-sectional momentum, S06 vol regime, S07 carry, S08 event), 154 V23 markets, 4-market V22 frontier, FX V21, 12-family V26. All killed or CONDITIONAL below $10k except savings + E1/E2. Every gate below is the reason.

**License:** Personal / team internal use. No resale.

---

## Section 1 — Quantitative Strategy Audit Checklist (8 Gates)

*Each gate: purpose, checklist, scoring, Edge OS example. PASS/ CONDITIONAL/ KILL per V25 Edge Admission Gate (all 7 must PASS for EDGE_CANDIDATE).*

### G1 Cost Model — Do not trust gross
- Purpose: Separate edge from friction. Edge OS destroyed 87% "winners" when costs added.
- Checklist:
  1. Round-trip modeled at 0.15% / 0.30% / 0.50% (crypto) or spread+swap (FX from V21 OANDA: EUR/USD 1.04bps, take 25% if API).
  2. Funding/borrow/swap explicit (S07 funding edge decomposition).
  3. Slippage per turnover (S05 churn killed net).
  4. Re-run at 3x cost — still >0?
  5. Fee tier verified (maker/taker, VIP, funding interval 8h vs 1h).
- Scoring: PASS if >0 at 0.50% AND >RFR. CONDITIONAL if >0 at 0.15% only. KILL if fails at 0.15%.
- Example: S07 best gross +87%, funding edge -3% — carry is illusion.
### G2 Baseline Comparison — Beat the dumb alternative
- Checklist: Buy & Hold same asset/period, 60/40, random entry. S04 best +20.83% vs Buy & Hold +22.58% = KILL.
### G3 OOS Discipline — Do not peek
- Checklist: Last 20% untouched, no re-tuning after TEST, pre-registration (V18 p70/p75/p80), multiple-testing correction (S05 324 configs expected 3 false positives).
### G4 Funding/Carry Edge Split
- Decompose: total = price_trend + funding_carry. Require funding_carry >0. V19 S07 5 survivors all funding edge ≤0.
### G5 Leakage / PIT / Survivorship
- Checklist: No close[0] as signal, timestamps PIT, delisting handled, BOM/encoding bug check (V19 S07 JSON BOM killed parse), look-ahead in rolling features.
### G6 Walk-Forward Persistence
- Rolling 60 train / 20 test. Require median net >0 and hit-rate >55% across windows. V18 ETH vol compression 59.3% 5D win rate failed when top 10% trimmed.
### G7 Friction Robustness
- Table: net at 0.15 / 0.30 / 0.50 + spread 0.5x/1x/2x. S05 -0.02% at 0.15% already negative — fragile.
### G8 Economics / Human-Time
- Net / human hour > $6/hr (B1 $6.67/hr wins at 10 cust) and net >4% RFR after take (25% RapidAPI / 13.2% Gumroad) + infra + shadow cost ($10/hr * hours).

**Master scoring:** 8/8 PASS → CONDITIONAL (needs 12mo live). 6-7 → CONDITIONAL with fix list. ≤5 → KILL.

---

## Section 2 — Backtest Integrity Checklist

| Risk | Probe | Fix |
|------|-------|-----|
| Survivorship | Asset list from start of period includes delisted? (XRP 2018 survivors only?) | Use point-in-time universe |
| Look-ahead | Signal uses close[0] to trade close[0]? EMA(15,40) cross at close -> next open trade only | Lag 1 bar |
| PIT | Funding CSV has BOM? Timestamp is settlement vs mark? V19 BOM bug re-parse with BOM strip | Verify raw bytes |
| Leakage | Feature = future vol regime? Label = forward return using close that was also feature? | Strict time split |
| Overlap | Cross-sectional rank uses same bar's return as label | Rank at T, label T+1 |

Scoring: Any unchecked = KILL until fixed and re-tested OOS.

---

## Section 3 — Cost / Friction Model Worksheet

**Fill:**

```
Notional per trade: $____
Round-trips / year: ____
Gross per trade: ____%
Cost per trade: 0.15% → net ____% | 0.30% → ____% | 0.50% → ____%
Funding per holding day: ____% (funding edge = funding_sum / trades)
Swap/overnight annual (FX): ____% (OANDA table V21)
Take: RapidAPI 25% / Gumroad 13.2% effective [FACT]
Infra: VPS $20/mo, Spread $0.10/turn (V21)
Shadow: hours/yr ____ * $10 = $____
NET = gross - costs - take - infra/365 - shadow/trades
NET / HR = (net * notional * trades) / hours
Hurdle: NET > 4% RFR and NET/HR > $6?
```

Example: D1 at 10 cust gross $288/yr → take $72 + processing $8 + infra $240 → net $156 → $1.00/hr (fails).

---

## Section 4 — Walk-Forward + Baseline Worksheet

**Template (fill per split):**

| Window | Train net (0.30%) | Test net | Buy&Hold same window | Excess | Hit rate |
|--------|-------------------|----------|----------------------|--------|----------|
| 2018-19 / 2020 |  |  |  |  |  |
| 2019-20 / 2021 |  |  |  |  |  |
| Median |  |  |  |  |  |

Rule: median excess >0 and test net >0 at 0.30% required. S05 median test net -1.2% — KILL even though best window +43%.

---

## Section 5 — Strategy Kill-Gate Worksheet

**Decision:** For each candidate score 0-5 on: economic existence, retail implementability, cost robustness, OOS, human-time <5hr/week, tail risk, distribution. 7 must PASS for EDGE_CANDIDATE per V25 §8. Any 2 FAIL → KILL. One FAIL → CONDITIONAL.

**Score your candidate:**

| Criterion | 0-5 | Threshold PASS | Evidence needed |
|-----------|-----|----------------|-----------------|
| Economic edge exists |  | ≥4 with split funding/price |  |
| Retail implementable |  | ≥4 OANDA $1 / IBKR fractional, not IBKR 20k min [FACT V21] |  |
| Cost robust (0.50%) |  | ≥4 |  |
| OOS survives |  | ≥4 |  |
| <5hr/week |  | ≥4 (D2 1hr/week 71% vs D1 3-5hr 53%) |  |
| Tail not >2x edge |  | ≥4 (FX -12% Jan 1998 kills 5.28% 3x [FACT V21]) |  |
| Distribution automatable |  | ≥4 marketplace search not personal brand |  |

---

## Section 6 — Result Reporting Template

**Copy this table for every candidate — mandatory, no commingling:**

```
Candidate: ______________  Date: ________  Period: ________
VAL net (0.30%): ____% | TEST net: ____% | Buy&Hold TEST: ____% | Excess: ____%
Funding edge: ____% | Price edge: ____% | Cost per trade: ____%
Walk-forward median excess: ____% | Hit rate: ____%
Impressions: ___ | Qualified: ___ | Trials/Downloads: ___ | Pricing views: ___ | Payments: ___ | Refunds: ___
Gross: $___ | Take: $___ | Infra: $___ | Net: $___ | Hours: ___ | Net/hr: $___
Verdict: PASS / CONDITIONAL / KILL | Gate that killed: ___
Evidence tag per line: [FACT]/[RESEARCH EVIDENCE]/[INFERENCE]/[UNVERIFIED] — no TAM-as-proof
```

**Non-goals:** This pack does not provide alpha. It prevents false alpha. If your strategy survives these 8 gates, proceed to 12-month paper; if not, KILL and return to savings + E1/E2 per V25.

**Updates:** Pack is versioned. Free Lite is always current free; $39 pack includes 12mo updates via Gumroad.

