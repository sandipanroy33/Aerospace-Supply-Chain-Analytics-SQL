# Executive Summary — Aerospace Supply Chain Performance & Forecasting

**Prepared for:** CEO & Executive Stakeholders
**Prepared by:** Data Analytics Team
**Period covered:** Jan 2022 – Dec 2024 (3 fiscal years)
**Scope:** 300 parts · 40 suppliers · 6 sites · 29,666 purchase orders · 280,800 weekly inventory records

---

## 1. Business Problem

The company sources aerospace parts from 40 suppliers across 6 sites, holding flight-critical inventory that cannot afford stockouts. Leadership needs to know: **are we buying reliably, are we holding the right inventory, and where is risk concentrated?**

## 2. Key Findings

### 🔴 On-time-in-full (OTIF) delivery is a company-wide problem, not a one-supplier problem
Only **39.7%** of all purchase orders arrived both on time and in full quantity over the 3-year period. Even our *best* performing supplier (SUP032, 441 POs) only reaches **57.6% OTIF**. This is a systemic delivery reliability issue, not an isolated vendor problem.

**Worst performers (min. 50 POs):**
| Supplier | POs | OTIF % |
|---|---|---|
| SUP033 | 631 | 3.0% |
| SUP023 | 280 | 23.9% |
| SUP039 | 306 | 25.2% |
| SUP009 | 649 | 25.3% |

### 🟡 Flight-critical (Class A) parts are the most protected, but not immune
Stockout-week frequency by criticality class:
| Class | Stockout weeks % |
|---|---|
| A (flight critical) | 0.28% |
| B (major) | 0.60% |
| C (minor) | 1.14% |

The inverse relationship (A < B < C) shows current inventory policy is correctly prioritizing critical parts — but 124 stockout-weeks still occurred on Class A parts, which is the highest-consequence failure mode in the business.

### 🟡 Quality incidents skew toward high-severity outcomes
368 total incidents: 243 Minor, 91 Major, **34 Critical**. Critical incidents account for a disproportionate share of scrapped units relative to their count, meaning when quality fails on this dataset, it tends to fail expensively.

### 🔴 Six suppliers are simultaneously top-quartile spend AND top-quartile defect risk
SUP027, SUP038, SUP017, SUP024, SUP006, and SUP037 combined represent **~$153M** of the company's **$593M** total 3-year spend, and all sit in the highest-risk quadrant for quality incidents. This is the single highest-priority finding for procurement/vendor management — it names exactly which relationships carry the most concentrated financial and operational risk.

### 🟢 Total spend is gently declining, not growing
2022: $200.7M → 2023: $197.8M → 2024: $194.1M. PO volume held roughly flat (~9,800–10,000/year). Spend efficiency appears to be improving slightly year over year, worth validating against unit cost/inflation trends.

### 🟡 Backorder exposure varies by site
SITE02 (0.92%) and SITE01 (0.88%) run hotter than SITE04 (0.75%) — a ~20% relative gap that's worth investigating for local planning/ordering cadence differences.

### 🟢 Forecasting is directionally reasonable but has room to improve
Average forecast error is ~1.45 units against an average weekly consumption of ~2.23 units per part — roughly **65% relative error**. This is a meaningful forecasting accuracy gap worth a dedicated demand-planning initiative.

## 3. Actionable Recommendations

1. **Launch a formal supplier OTIF improvement program**, starting with SUP033 (3% OTIF) — investigate root cause before renewing/expanding that contract.
2. **Prioritize the 6 high-spend/high-defect suppliers** (SUP027, SUP038, SUP017, SUP024, SUP006, SUP037) for immediate quality audits — they represent concentrated financial exposure.
3. **Investigate the 124 stockout-weeks on Class A parts** individually — even rare stockouts on flight-critical parts carry outsized operational/safety risk.
4. **Review SITE02 and SITE01 replenishment policy** against SITE04's better-performing baseline.
5. **Invest in demand forecasting model improvements** — current ~65% relative forecast error signals an opportunity to reduce both excess inventory and backorder risk simultaneously.

## 4. Methodology Note

All figures were derived from raw transactional data (purchase orders, weekly inventory snapshots, quality incident logs, and parts master) using SQL joins, CTEs, and window functions — full query logic is version-controlled in `/sql`. No figures were estimated or assumed; every number above traces to a specific, reproducible query.
