---
template: spec
purpose: Technical specification for MWG FY2025 ratio model and analysis — defines scope, inputs, formulas, validation, and analysis requirements precisely enough that any competent executor (human or LLM) can produce correct output
audience: Adam Stauffer (BUS-629 instructor); EMBA peers
title: "Mobile World Investment Corporation (MWG) — FY2025 Performance Ratios Technical Specification"
author: Nguyen Manh Thai
date: 2026-05-25
version: "1.4"
company: "Mobile World Investment Corporation (MWG, HOSE)"
ticker: MWG
exchange: HOSE
course: BUS-629
reporting_standard: VAS
currency: VND billions
fiscal_year: "FY2025"
naming_convention: YYYY-MM-DD-{slug}.md
notes: >
  Version 1.4: Added 6 YAML fields (ticker, exchange, course, reporting_standard, currency,
  fiscal_year) per instructor Stage 4 feedback; added Validation Rule V7 documenting CF
  reconciliation gap (CFO+CFI+CFF = +103B vs. BS cash change +4,653B, ~4,550B from
  reclassification between cash and short-term financial investments).
  Version 1.3: (1) Named Range Map extracted into standalone Part A section; (2) Pharmacity added
  as second pharmacy benchmark alongside Long Châu; (3) Winmart+ and Co.opmart added as BHX grocery
  benchmarks; (4) YAML frontmatter cleaned. Version 1.2 added segment-specific benchmarks
  (FRT/Long Châu), ALM stress-test (Du Pont §8), Board-level + national-policy guardrail
  (§9), and logistics cost context clarification (§7). Version 1.1 corrected the share_price
  unit mismatch (÷1,000 factor for market capitalisation).
---

# MWG FY2025 Performance Ratios — Technical Specification

**Author:** Nguyen Manh Thai
**Date:** 2026-05-25
**Version:** 1.4 (Stage 4 instructor feedback — YAML fields + V7 CF reconciliation rule)
**Company:** Mobile World Investment Corporation · Ticker: MWG · Exchange: Ho Chi Minh Stock Exchange (HOSE)

---

## 1. Scope & Objective

This specification fully defines the Excel ratio model and the analytical work for Mobile World Investment Corporation (MWG, HOSE) using audited FY2025 consolidated financial statements.

- **Company:** Mobile World Investment Corporation (Công ty Cổ phần Đầu tư Thế Giới Di Động)
- **Ticker / Exchange:** MWG · HOSE
- **Fiscal Period:** FY2025 (January 1 – December 31, 2025); prior-year comparative is FY2024
- **Reporting Standard:** Vietnamese Accounting Standards (VAS). Critical VAS–IFRS difference: VAS does not require operating lease capitalisation (no IFRS 16 equivalent). Consequently, long-term debt = 0 and no right-of-use assets are recorded. The LT debt ratio and LT debt-to-equity ratio are structurally zero and should be interpreted as N/A rather than as low-leverage signals.
- **Reporting Currency:** VND billions (1 VND billion = 10⁹ VND). All balance sheet, income statement, and cash flow figures are in VND billions unless otherwise noted.
- **Share Price Unit Exception:** The share price input (`share_price`) is in raw VND per share (not VND billions). See Section 5 Derived Inputs for the unit-corrected market capitalisation formula.
- **Analytical Objective:** Compute 25+ performance ratios across six categories (Performance, Profitability, Efficiency, Leverage, Liquidity, Du Pont), interpret the results against segment-specific domestic benchmarks and Q1/2026 macroeconomic conditions, and deliver 4 Board-level strategic recommendations.
- **Intended Audience:** BUS-629 instructor (Adam Stauffer), Shidler College of Business / UH Mānoa EMBA cohort, and any LLM executor running Stage 5 analysis using this spec as sole input.

---

## Part A — Model Specification

### 2. Model Architecture

**Tab layout (6 worksheets):**

| Tab | Contents | Role |
|---|---|---|
| Cover | Project metadata, company info block (rows 43–53), 10-item spot-check table (rows 56–67) | Reference / submission cover |
| Balance Sheet | Assets (rows 7–20), Liabilities & Equity (cols G–H, rows 7–20), Totals (row 23) | Input data |
| Income Statement | Revenue through net income (rows 6–19) | Input data |
| Cash Flow Statement | CFO, CFI, CFF (rows 7–29) | Input data |
| Ratios | Four inputs (rows 6–11), derived intermediates (rows 15–38), ratio outputs (rows 43–76) | Calculation |
| Notes | Source documentation, VAS adjustments, rounding notes | Reference |

**Color coding:**
- Green (#00704F) fill, white font: section headers
- Yellow (#FFFACD) fill: manual input cells (share price, shares outstanding, WACC, tax rate)
- Light gray (#F2F2F2) fill: formula-driven cells (no direct input)
- White: descriptive labels

**Data flow:** Balance Sheet, Income Statement, and Cash Flow Statement tabs feed Ratios tab exclusively via named ranges. No values are hard-coded in ratio formulas. Cover tab spot-check table is manually populated for source documentation; it does not feed ratio calculations.

**Input / calculation / output separation:**
- *Inputs:* Financial statement tabs + four Ratios tab assumption cells (C8:C11)
- *Calculations:* Ratios tab rows 12–38 (derived inputs) and rows 43–76 (ratio formulas)
- *Outputs:* Ratio values in Ratios!C43:C76; Cover tab spot-check table

---

### 3. Named Range Map

All named ranges follow consistent prefix conventions. The Stage 5 executor must use these exact strings when referencing model values — do not substitute cell addresses.

| Prefix | Tab | Scope | Example |
|---|---|---|---|
| `BAL_[item]_curr` | Balance Sheet | Current-year balance sheet line item | `BAL_assets_total_curr`, `BAL_inventories_curr` |
| `BAL_[item]_prior` | Balance Sheet | Prior-year balance sheet line item | `BAL_equity_shareholders_prior`, `BAL_receivables_prior` |
| `INC_[item]` | Income Statement | Income statement line item | `INC_sales`, `INC_ebit`, `INC_net`, `INC_interest_expense` |
| `CASH_[item]` | Cash Flow Statement | Cash flow line item | `CASH_operating`, `CASH_investments`, `CASH_financing` |
| `startYear_[item]` | Ratios | Alias for prior-year balance sheet value | `startYear_equity` ≡ `BAL_equity_shareholders_prior` |
| `currentYear_[item]` | Ratios | Current-year balance or derived figure | `currentYear_assets_total`, `currentYear_after_tax_operating_income` |
| `avg_[item]` | Ratios | Simple average of start and current year | `avg_total_assets`, `avg_equity` |
| `RATIO_[name]` | Ratios | Computed ratio reused in Du Pont decomposition | `RATIO_asset_turnover`, `RATIO_leverage`, `RATIO_debt_burden` |

**Analyst assumption inputs (no prefix, Ratios tab C8:C11):**

| Named Range | Cell | Description | Unit |
|---|---|---|---|
| `share_price` | C8 | Closing price Dec 31, 2025 — raw VND per share, **not** VND billions | VND/share |
| `shares_outstanding` | C9 | Shares outstanding | Millions |
| `cost_capital` | C10 | WACC (country-risk-adjusted) | % |
| `tax_rate` | C11 | Statutory income tax rate | % |

> **Unit alert:** `share_price` is the sole input not denominated in VND billions. The derived `market_capitalization` must apply a ÷1,000 conversion (see Section 5). All other Ratios tab inputs and outputs are in VND billions.

---

### 4. Data Inputs

All values are sourced from MWG Audited Consolidated Financial Statements FY2025 (primary) and CafeF.vn historical price feed (share price). All figures in VND billions unless the Unit column specifies otherwise.

#### Balance Sheet Inputs

| Named Range | Description | FY2025 (curr) | FY2024 (prior) | Unit |
|---|---|---:|---:|---|
| `BAL_cash_marketable_securities_curr` / `_prior` | Cash & short-term financial investments | 38,874 | 34,221 | VND B |
| `BAL_receivables_curr` / `_prior` | Trade and other receivables | 10,183 | 8,826 | VND B |
| `BAL_inventories_curr` / `_prior` | Inventories | 27,267 | 22,245 | VND B |
| `BAL_other_current_assets_curr` / `_prior` | Other current assets | 878 | 544 | VND B |
| `BAL_assets_current_curr` / `_prior` | Total current assets (sum) | 77,202 | 65,836 | VND B |
| `BAL_ppe_gross_curr` / `_prior` | PP&E gross | 19,568 | 19,265 | VND B |
| `BAL_accumulated_depreciation_curr` / `_prior` | Accumulated depreciation | 16,970 | 15,678 | VND B |
| `BAL_fixed_assets_net_curr` / `_prior` | Net tangible fixed assets | 2,598 | 3,587 | VND B |
| `BAL_intangibles_curr` / `_prior` | Intangible assets / goodwill | 0 | 0 | VND B |
| `BAL_other_assets_curr` / `_prior` | Other long-term assets | 4,146 | 1,014 | VND B |
| `BAL_assets_total_curr` / `_prior` | **Total Assets** | **83,946** | **70,437** | VND B |
| `BAL_debt_short_term_curr` / `_prior` | Short-term bank borrowings | 29,931 | 27,300 | VND B |
| `BAL_accounts_payable_curr` / `_prior` | Accounts payable | 13,114 | 9,180 | VND B |
| `BAL_other_current_liabilities_curr` / `_prior` | Other current liabilities | 7,725 | 5,836 | VND B |
| `BAL_liabilities_current_curr` / `_prior` | Total current liabilities (sum) | 50,770 | 42,316 | VND B |
| `BAL_debt_long_term_curr` / `_prior` | Long-term debt | 0 | 0 | VND B |
| `BAL_other_long_term_liabilities_curr` / `_prior` | Other long-term liabilities | 0 | 0 | VND B |
| `BAL_common_stock_curr` / `_prior` | Common stock (paid-in capital) | 14,532 | 15,174 | VND B |
| `BAL_retained_earnings_curr` / `_prior` | Retained earnings (incl. NCI) | 18,644 | 12,947 | VND B |
| `BAL_equity_shareholders_curr` / `_prior` | **Total shareholders' equity** | **33,176** | **28,121** | VND B |
| `BAL_liabilities_total_curr` / `_prior` | Total liabilities | 50,770 | 42,316 | VND B |

> **Model note:** Model total assets (83,946 / 70,437) differs slightly from audited consolidated totals (84,066 / 70,416) because the simplified template does not capture all sub-line items. The balance sheet equation holds within the model: Assets = Liabilities + Equity (83,946 = 50,770 + 33,176 ✓).

#### Income Statement Inputs

| Named Range | Description | FY2025 | Unit |
|---|---|---:|---|
| `INC_sales` | Net revenue | 155,928 | VND B |
| `INC_cost_goods_sold` | Cost of goods sold | 124,926 | VND B |
| `INC_sga` | SG&A expenses (excl. D&A) | 22,036 | VND B |
| `INC_depreciation` | Depreciation & amortisation | 1,891 | VND B |
| `INC_ebit` | EBIT (= Sales − COGS − SG&A − D&A) | 7,075 | VND B |
| `INC_other_income` | Other income (financial income incl.) | 3,107 | VND B |
| `INC_interest_expense` | Interest expense | 1,471 | VND B |
| `INC_taxable_income` | Taxable income (EBT) | 8,711 | VND B |
| `INC_taxes` | Income taxes | 1,638 | VND B |
| `INC_net` | **Net income** | **7,073** | VND B |
| `INC_dividends` | Dividends paid | 1,478 | VND B |
| `INC_addition_retained_earnings` | Addition to retained earnings | 5,595 | VND B |

#### Cash Flow Inputs

| Named Range | Description | FY2025 | Unit |
|---|---|---:|---|
| `CASH_operating` | Cash provided by operations (CFO) | 6,096 | VND B |
| `CASH_investments` | Cash used for investments (CFI) | −6,661 | VND B |
| `CASH_financing` | Cash from financing activities (CFF) | 668 | VND B |

> **CF reconciliation:** CFO + CFI + CFF = 6,096 − 6,661 + 668 = +103B ✓

---

### 5. Derived Inputs

All derived inputs are computed in Ratios tab rows 12–38.

| Named Range | Formula | Value | Unit |
|---|---|---:|---|
| `market_capitalization` | `share_price × shares_outstanding / 1,000` ¹ | 129,921.5 | VND B |
| `startYear_equity` | `BAL_equity_shareholders_prior` | 28,121 | VND B |
| `startYear_receivables` | `BAL_receivables_prior` | 8,826 | VND B |
| `startYear_inventory` | `BAL_inventories_prior` | 22,245 | VND B |
| `startYear_total_assets` | `BAL_assets_total_prior` | 70,437 | VND B |
| `startYear_total_capitalization` | `BAL_debt_long_term_prior + BAL_equity_shareholders_prior` | 28,121 | VND B |
| `currentYear_after_tax_operating_income` | `INC_net + INC_interest_expense × (1 − tax_rate)` | 8,249.8 | VND B |
| `currentYear_daily_sales_average` | `INC_sales / 365` | 427.2 | VND B/day |
| `currentYear_cost_goods_sold_daily` | `INC_cost_goods_sold / 365` | 342.3 | VND B/day |
| `currentYear_equity` | `BAL_equity_shareholders_curr` | 33,176 | VND B |
| `currentYear_cash_marketable_securities` | `BAL_cash_marketable_securities_curr` | 38,874 | VND B |
| `currentYear_assets_current` | `BAL_assets_current_curr` | 77,202 | VND B |
| `currentYear_liabilities_current` | `BAL_liabilities_current_curr` | 50,770 | VND B |
| `currentYear_working_capital_net` | `currentYear_assets_current − currentYear_liabilities_current` | 26,432 | VND B |
| `currentYear_debt_long_term` | `BAL_debt_long_term_curr` | 0 | VND B |
| `currentYear_assets_total` | `BAL_assets_total_curr` | 83,946 | VND B |
| `currentYear_liabilities_total` | `BAL_liabilities_total_curr` | 50,770 | VND B |
| `currentYear_total_capitalization` | `BAL_debt_long_term_curr + BAL_equity_shareholders_curr` | 33,176 | VND B |
| `avg_equity` | `(currentYear_equity + startYear_equity) / 2` | 30,648.5 | VND B |
| `avg_total_assets` | `(currentYear_assets_total + startYear_total_assets) / 2` | 77,191.5 | VND B |
| `avg_total_capitalization` | `(currentYear_total_capitalization + startYear_total_capitalization) / 2` | 30,648.5 | VND B |

> ¹ **Unit-mismatch correction (HIL v1.1):** Raw template formula `share_price × shares_outstanding = 88,400 × 1,469.7 = 129,921,480` yields VND millions. Dividing by 1,000 converts to VND billions. The Stage 5 executor must use 129,921.5 VND B for all MVA and Market-to-Book calculations. See Validation Rule 6.

---

### 6. Ratio Definitions & Formulas

#### Performance

| Ratio | Formula (named-range notation) | Expected Output | Unit |
|---|---|---:|---|
| Market Value Added (MVA) | `market_capitalization − currentYear_equity` ¹ | 96,745.5 | VND B |
| Market-to-Book | `market_capitalization / currentYear_equity` ¹ | 3.91 | × |
| Economic Value Added (EVA) | `currentYear_after_tax_operating_income − (cost_capital × startYear_total_capitalization)` | 4,453.5 | VND B |

> ¹ Use unit-corrected `market_capitalization = 129,921.5 VND B` (not raw template value 129,921,480).

#### Profitability (start-of-year base)

| Ratio | Formula | Expected Output | Unit |
|---|---|---:|---|
| Return on Assets (ROA) | `currentYear_after_tax_operating_income / startYear_total_assets` | 11.71% | % |
| Return on Capital (ROC) | `currentYear_after_tax_operating_income / startYear_total_capitalization` | 29.34% | % |
| Return on Equity (ROE) | `INC_net / startYear_equity` | 25.15% | % |

#### Profitability (average base)

| Ratio | Formula | Expected Output | Unit |
|---|---|---:|---|
| ROA [avg] | `currentYear_after_tax_operating_income / avg_total_assets` | 10.69% | % |
| ROC [avg] | `currentYear_after_tax_operating_income / avg_total_capitalization` | 26.92% | % |
| ROE [avg] | `INC_net / avg_equity` | 23.08% | % |

#### Efficiency

| Ratio | Formula | Expected Output | Unit |
|---|---|---:|---|
| Asset Turnover | `INC_sales / startYear_total_assets` | 2.21 | × |
| Receivables Turnover | `INC_sales / startYear_receivables` | 17.67 | × |
| Average Collection Period | `startYear_receivables / currentYear_daily_sales_average` | 20.7 | days |
| Inventory Turnover | `INC_cost_goods_sold / startYear_inventory` | 5.62 | × |
| Days in Inventory | `startYear_inventory / currentYear_cost_goods_sold_daily` | 65.0 | days |
| Profit Margin | `INC_net / INC_sales` | 4.54% | % |
| Operating Profit Margin | `currentYear_after_tax_operating_income / INC_sales` | 5.29% | % |

#### Leverage

| Ratio | Formula | Expected Output | Unit |
|---|---|---:|---|
| LT Debt Ratio | `currentYear_debt_long_term / (currentYear_debt_long_term + currentYear_equity)` | 0% | % |
| LT Debt-to-Equity | `currentYear_debt_long_term / currentYear_equity` | 0% | % |
| Total Debt Ratio | `currentYear_liabilities_total / currentYear_assets_total` | 60.5% | % |
| Times Interest Earned (TIE) | `INC_ebit / INC_interest_expense` | 4.81 | × |
| Cash Coverage | `(INC_ebit + INC_depreciation) / INC_interest_expense` | 6.10 | × |
| Debt Burden | `INC_net / currentYear_after_tax_operating_income` | 0.857 | × |
| Financial Leverage | `currentYear_assets_total / currentYear_equity` | 2.53 | × |

> **VAS Note:** LT Debt Ratio = 0% is a structural VAS artefact (no IFRS 16). Do not interpret as low leverage. Primary leverage signals: Total Debt Ratio (60.5%) and TIE (4.81×).

#### Liquidity

| Ratio | Formula | Expected Output | Unit |
|---|---|---:|---|
| Net Working Capital to Assets | `currentYear_working_capital_net / currentYear_assets_total` | 31.5% | % |
| Current Ratio | `currentYear_assets_current / currentYear_liabilities_current` | 1.52 | × |
| Quick Ratio | `(currentYear_cash_marketable_securities + BAL_receivables_curr) / currentYear_liabilities_current` | 0.97 | × |
| Cash Ratio | `currentYear_cash_marketable_securities / currentYear_liabilities_current` | 0.77 | × |

#### Du Pont System

| Ratio | Formula | Expected Output | Unit |
|---|---|---:|---|
| ROA (Du Pont) | `RATIO_operating_profit_margin × RATIO_asset_turnover` | 11.69% | % |
| ROE (Du Pont) | `RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden` | 25.34% | % |

---

### 7. Validation Rules

The Stage 5 executor must verify all seven rules before proceeding to analysis. Flag any breach; do not suppress.

| # | Rule | Check | Tolerance |
|---|---|---|---|
| 1 | **Balance Sheet balance** | `BAL_assets_total_curr = BAL_liabilities_total_curr + BAL_equity_shareholders_curr` → 83,946 = 50,770 + 33,176 ✓ | 0 |
| 2 | **Income allocation** | `INC_net = INC_dividends + INC_addition_retained_earnings` → 7,073 = 1,478 + 5,595 ✓ | 0 |
| 3 | **ATOI derivation** | `currentYear_after_tax_operating_income = INC_net + INC_interest_expense × (1 − tax_rate)` → 8,249.8 = 7,073 + 1,471 × 0.80 ✓ | ≤ 0.1B |
| 4 | **Du Pont ROA** | `RATIO_operating_profit_margin × RATIO_asset_turnover ≈ RATIO_roa` → 5.29% × 2.21 = 11.69% ≈ 11.71% ✓ | ≤ 0.5% |
| 5 | **Du Pont ROE** | `RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden ≈ RATIO_roe` → 2.53 × 2.21 × 5.29% × 0.857 = 25.34% ≈ 25.15% ✓ | ≤ 0.5% |
| 6 | **Market cap unit correction** | `market_capitalization (VND B) = share_price × shares_outstanding / 1,000 = 88,400 × 1,469.7 / 1,000 = 129,921.5B`. Raw template cell C12 = 129,921,480 (VND millions — wrong). MVA and M/B must use the ÷1,000 corrected value. | Unit match required |
| 7 | **CF reconciliation gap** | `CASH_operating + CASH_investments + CASH_financing = 6,096 − 6,661 + 668 = +103B` (net cash flow per CF statement). Balance Sheet cash change: `BAL_cash_marketable_securities_curr − BAL_cash_marketable_securities_prior = 38,874 − 34,221 = +4,653B`. **Gap = 4,550B** — this is expected and not an error. Under VAS, short-term financial investments (fixed deposits) are classified within `BAL_cash_marketable_securities` but are excluded from the narrow "cash and cash equivalents" definition used in the Cash Flow Statement. Do not flag this as a reconciliation breach; document it as a VAS classification artefact. | Informational — do not suppress, do not treat as error |

---

## Part B — Analysis Specification

### 8. Analysis Requirements

For each ratio category below, interpret the computed values against the specified benchmarks and note cross-category connections. **Do not use generic HOSE-wide sector medians — use the segment-specific domestic competitor benchmarks listed below.**

**Performance (MVA, M/B, EVA)**
- Interpret EVA = 4,453.5B VND as the spread between after-tax operating return and the 13.5% WACC hurdle applied to start-of-year capital.
- Interpret M/B = 3.91× against HOSE retail peers. Note: a pending Bách Hóa Xanh (BHX) segment IPO at ~80,000B VND standalone valuation implies the grocery division alone may approximate a large portion of MWG's current market cap — a structural discount embedded in the FY2025 book equity of 33,176B that the market has only partially corrected. **BHX grocery valuation context:** The executor must compare BHX's revenue trajectory and store-count economics against **Winmart+ (Masan Consumer Holdings)** and **Co.opmart (Saigon Co.op)**. Winmart+ is the closest listed equivalent for rapid nationwide grocery expansion; Co.opmart represents the entrenched cooperative model with dense Southern Vietnam footprint. These comparisons frame the BHX valuation discount in terms of operational peer benchmarks, not only IPO speculation.
- MVA = 96,745.5B represents total market value added above book equity. Assess sustainability against EVA trajectory and the Q1/2026 macro headwinds quantified below.
- **Cross-category link:** EVA sustainability depends on operating profit margin (Efficiency) and the 13.5% WACC assumption. ALM-driven interest cost increases (see Du Pont section) directly compress ATOI and narrow EVA.

**Profitability (ROA, ROC, ROE)**
- Benchmark ROE (25.15%) against HOSE consumer discretionary median (~12–18%). Decompose into Du Pont drivers before attributing outperformance.
- ROC = 29.34% reflects zero long-term debt under VAS; interpret against WACC 13.5% — the spread (~15.8 pp) is the core value-creation argument.
- Flag that ATOI includes financial income (3,107B from deposit placement). Isolate EBIT-based retail return from treasury carry income, which is not recurring core retail income.
- **Q1/2026 macro headwind:** March 2026 CPI rose 4.65% YoY (GSO); Q1/2026 average CPI +3.51%; core inflation 3.63% YoY. The executor must assess how sustained inflation erodes real consumer purchasing power for discretionary electronics, compressing top-line revenue growth and threatening MWG's FY2026 target of 185,000B in net revenue (+19% YoY).
- **Cross-category link:** High ROE is partly driven by leverage (2.53×) and asset turnover (2.21×). Du Pont section must decompose this.

**Efficiency (Turnover, Margins)**

*Segment-specific competitor benchmarks — mandatory:*
- **Consumer Electronics & ICT (TGDĐ & DMX):** Benchmark Asset Turnover (2.21×) and Inventory Turnover (5.62× / 65 days) directly against **FPT Retail (FRT)** and **Nguyen Kim**. Generic HOSE retail medians are insufficient; FRT is the only listed domestic pure-play comparable for ICT retail. The executor must note where MWG leads or lags FRT on these two metrics.
- **Pharmacy segment (An Khang):** Benchmark Inventory Days (65 days consolidated) and scaling efficiency against **Long Châu (FRT subsidiary)** and **Pharmacity**. Long Châu has demonstrated superior per-store economics and inventory discipline in the pharmacy channel; Pharmacity represents the venture-capital-funded national rollout model. The executor must: (a) assess whether An Khang's inventory model is structurally viable against Long Châu's benchmark or requires a strategic pivot; (b) if publicly available per-store economics for Pharmacity are unavailable, state this exclusion explicitly — do not substitute generic pharmaceutical medians.
- **Grocery segment (BHX):** Benchmark BHX store-count efficiency and revenue-per-store trajectory against **Winmart+** and **Co.opmart**. Winmart+ is expanding aggressively in Northern Vietnam — the same territory BHX is entering — making it the most directly comparable competitive threat. Co.opmart's established supply-chain in the South provides a baseline for Southern store economics. The executor must assess whether BHX's inventory turnover trend (as a component of the consolidated 5.62× figure) is converging toward or diverging from these grocery benchmarks.

*Supply-side cost shock — mandatory integration:*
- May 2026 fuel prices: RON 95-III at ~25,540 VND/litre; Diesel at ~28,760 VND/litre. Local logistics networks are imposing flexible fuel surcharges of 6–10%. Vietnam's logistics cost-to-GDP ratio of 15–16% is cited as macro context only — it explains why fuel surcharges transmit so forcefully into retail SG&A, but it is **not** an invitation to recommend national-level logistics policy. The executor must translate this macro headwind into MWG-specific actions: quantify the directional impact on SG&A expenses (currently 22,036B / 14.1% of revenue) and assess the erosion risk to the 5.29% Operating Profit Margin. Any recommendation arising from this analysis must be a Board-level decision MWG can execute unilaterally — for example, renegotiating third-party logistics contracts, accelerating in-house BHX distribution centre investment, or locking in fuel-price-indexed freight agreements.
- Net Profit Margin = 4.54% vs. Gross Margin = 19.9%. The 15.4 pp gap is absorbed by SG&A (14.1%), D&A (1.2%), and net interest/tax (1.4%). Flag that financial income (3,107B) inflates net margin above pure retail operating performance.

**Leverage**
- LT Debt Ratio = 0% is a VAS structural artefact. Assess leverage through Total Debt Ratio (60.5%) and TIE (4.81×).
- TIE = 4.81× and Cash Coverage = 6.10× are acceptable but not strong given 29,931B in short-term rollover debt. Stress-test: if interest rates rise 100 bps, annual interest increases by ~299B, compressing TIE to approximately 4.39× (still above 3× threshold; see Du Pont Section 9 for full ALM derivation).
- Debt Burden = 0.857× indicates that non-operating financial income partially reduces the effective drag on ATOI. The executor must flag that this treasury carry income is rate-sensitive (see Du Pont ALM analysis).

**Liquidity**
- Current Ratio = 1.52×: adequate. Retail minimum: 1.2×. Monitor BHX inventory front-loading risk.
- Quick Ratio = 0.97×: below 1.0×, typical for inventory-heavy retail. The 38,874B cash & ST investments position provides a strong de facto liquidity buffer — but see ALM caveat below.
- Cash Ratio = 0.77×: MWG's treasury strategy (borrowing short at low rates, placing 33,874B in higher-yield fixed deposits) means the cash ratio overstates available operational liquidity. A portion of these deposits serve as collateral for ST borrowings. **In the Q1/2026 tightening credit cycle, if deposit maturities do not align with short-term debt rollover dates, MWG faces asset-liability maturity mismatch risk.** The executor must flag this as a structural liquidity vulnerability, not a liquidity strength.
- **Cross-category link:** Inventory (27,267B) is the critical variable. Inventory Turnover (Efficiency) sustainability under BHX expansion is the primary liquidity risk.

---

### 9. Du Pont Decomposition

**Target identity:**
> ROE = Financial Leverage × Asset Turnover × Operating Profit Margin × Debt Burden
> 25.34% = 2.53 × 2.21 × 5.29% × 0.857

**Decomposition instructions for Stage 5 executor:**

1. Compute each of the four Du Pont components from the named ranges in Section 6.
2. Identify the **primary ROE driver**: Asset Turnover (2.21×) is the dominant component for a retail group operating on thin margins. Confirm or challenge this based on computed values.
3. Interpret the **Debt Burden (0.857×)**: Below 1.0× because non-operating financial income supplements EBIT-level earnings. Net income is lower than ATOI as a percentage — this is unusual and reflects structural reliance on treasury carry income to prop ROE.
4. Assess **BHX expansion sensitivity**: If BHX expands from ~1,700 to 2,000+ stores in FY2026, capital base grows faster than revenue near-term, compressing Asset Turnover. Quantify: a 10% asset increase with flat revenue reduces Asset Turnover from 2.21× to ~2.01×, reducing Du Pont ROE by approximately 2 percentage points.
5. **ALM Interest Rate Gap Stress-Test (mandatory):** Perform a dedicated Asset-Liability Management risk analysis on MWG's balance sheet structure. MWG carries 29,931B VND in short-term floating-rate bank borrowings to fund working capital, while simultaneously locking a large portion of its 38,874B VND cash position into fixed-term bank deposits. In the early 2026 credit tightening environment, short-term borrowing rates adjust upward immediately upon rollover, while locked deposit yields remain fixed until maturity. The executor must:
   - Estimate the directional impact of a 100 bps rise in short-term borrowing rates on annual interest expense (currently 1,471B). A 100 bps increase on 29,931B ≈ +299B additional interest, reducing EBIT by ~299B and compressing TIE from 4.81× to approximately 4.39×.
   - Assess how this interest cost increase reduces Net Margin (currently 4.54%) and cascades through the Debt Burden component of the Du Pont ROE decomposition.
   - Evaluate whether the treasury carry spread (deposit yield minus borrowing rate) narrows to zero or turns negative, eliminating the 3,107B financial income that currently supports the Debt Burden ratio above 0.80×.
   - Flag whether MWG's current ALM structure represents a strategic carry trade or an unhedged refinancing risk, given the Q1/2026 tightening cycle.
6. Verify Du Pont ROE ≈ direct ROE within 0.5% tolerance (Validation Rule 5).

---

### 10. Strategic Recommendations

Provide **exactly 4 recommendations**, each meeting all three standards below.

> **Board-Level Constraint (mandatory):** All 4 recommendations must address Board-level capital allocation, strategic asset-liability management, or structural financing decisions. Two categories of scope are explicitly prohibited:
> 1. *Micro-management* — SKU rationalisation, store-level staffing, point-of-sale optimisation, or any action delegated below the Group CFO level.
> 2. *National policy* — recommendations that require government action, industry-wide regulation, or macro-level infrastructure investment (e.g., "optimise Vietnam's national logistics corridor", "lobby for fuel subsidy reform", "support green logistics policy"). Macro data (CPI, fuel prices, logistics cost-to-GDP) is analytical context only; it must be translated into a company-specific Board decision, not a policy prescription.
>
> Every recommendation must be actionable by MWG's Board of Directors or Group CFO alone, without requiring third-party regulatory or government approval. Examples of acceptable scope: interest rate hedging via swaps or fixed-rate caps, transitioning short-term floating debt into fixed-rate instruments, capital structure matching for BHX expansion financing, in-house distribution centre investment, segment equity separation strategies.

**Evidence standard:** Each recommendation must cite at least one specific ratio value from Section 6 and one directional data point (YoY change, benchmark gap, or macro trend).

**Actionable specificity:** Each recommendation must name a concrete Board-level action (not "manage interest rate risk" — instead "initiate a structured interest rate swap programme to fix 50% of the 29,931B short-term borrowing at current rates before Q3/2026 rollover, capping TIE downside at 4.0× under a 150 bps shock scenario").

**Format per recommendation:**
```
### R[n]: [Title]
- **Ratio evidence:** [Ratio name] = [value], vs. benchmark/prior [value]
- **Observation:** [One sentence on what the ratio reveals]
- **Recommendation:** [Specific Board-level action]
- **Risk if not acted upon:** [Directional consequence on a named ratio]
```

**Required recommendation coverage (one per area):**
1. ALM hedging strategy — interest rate risk from ST floating debt vs. fixed deposit mismatch (TIE, Debt Burden)
2. BHX expansion capital structure — equity vs. debt financing for Northern rollout (Asset Turnover, Total Debt Ratio)
3. Earnings quality and treasury carry dependency — Board decision on financial income reliance (Operating Profit Margin vs. Net Margin gap)
4. BHX segment disclosure and valuation gap — strategic decision on segment reporting ahead of IPO (MVA, M/B)

---

### 11. Output Format

**File format:** Markdown (`.md`)
**Length:** 1,400–1,800 words (body only; exclude frontmatter and references)
**Tone:** Senior analyst memo — factual, direct, quantitatively grounded. No marketing language. No hedging without data support.
**Audience:** Executive reader with financial literacy; does not need formula derivations explained.

**Required sections in order:**
```
## Executive Summary          (~150 words)
## Ratio Results Summary      (table: all 25+ ratios with name, value, unit, one-line interpretation)
## Du Pont Decomposition      (~200 words, includes decomposition identity with computed values + ALM stress-test)
## Category Analysis          (~600 words across 6 sub-sections, one per ratio category)
## Strategic Recommendations  (4 recommendations in R[n] format, Board-level scope only)
## Model Limitations          (~100 words: VAS vs IFRS, simplified template, unit mismatch correction)
## References                 (source list)
```

**Ratio Results Summary table format:**
```
| Category | Ratio | Value | Unit | Signal |
```
where Signal is one of: ✅ Positive · ⚠️ Monitor · ❌ Concern

---

## References

1. Mobile World Investment Corporation — Audited Consolidated Financial Statements FY2025. https://ir.thegioididong.com
2. Mobile World Investment Corporation — Audited Consolidated Financial Statements FY2024. https://ir.thegioididong.com
3. Mobile World Investment Corporation — Annual Report 2025. https://ir.thegioididong.com
4. CafeF.vn — MWG closing price Dec 31, 2025 = 88,400 VND. https://cafef.vn/du-lieu/hose/mwg
5. General Statistics Office of Vietnam (GSO) — CPI March 2026: +4.65% YoY; Q1/2026 average: +3.51%; core inflation: +3.63% YoY.
6. Vietnam Petroleum Administration — Fuel prices May 2026: RON 95-III 25,540 VND/l; Diesel 28,760 VND/l.
7. Stage 3 populated workbook: `2026-05-21-nguyen-mwg-financials.xlsx` (Ratios tab C43:C76)
8. Stage 4 brief: https://github.com/adamwstauffer/shidler/blob/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage4-technical-specification.md
9. Spec template: https://github.com/adamwstauffer/shidler/blob/main/docs/templates/spec-template.md

---

## HIL Review Note

### Iteration 1: Version 1.0 → 1.1 (Formula & Unit Calibration)

**Gap identified in v1.0:** Section 3 listed `market_capitalization = 129,921,480 VND B`. Upon reviewing the Stage 3 workbook ratio outputs, Market-to-Book showed 3,916× and MVA showed ~129.9 million VND billions — both nonsensical for a company with 33,176B in book equity.

**Root cause:** The template formula `share_price (raw VND/share) × shares_outstanding (millions)` yields VND millions, not VND billions. The template was designed for USD companies where share price (USD/share) × shares (millions) = USD millions = same unit as balance sheet. For MWG, 88,400 VND/share × 1,469.7M shares = 129,921,480 VND millions — 1,000× too large.

**Without this correction, Stage 5 would have reported** MVA of ~129 million VND billions and M/B of ~3,916× — making the entire Performance section analytically unusable.

**Changes made in v1.1:**
1. Added ÷1,000 factor to market cap formula → `market_capitalization = 129,921.5 VND B`
2. Recalculated Performance ratio expected outputs: MVA = 96,745.5B; M/B = 3.91×
3. Added Validation Rule 6 requiring Stage 5 executor to apply unit correction before computing MVA and M/B
4. Added footnote ¹ throughout ratio tables flagging the correction

---

### Iteration 2: Version 1.1 → 1.2 (Macro, ALM & Peer Benchmarking Calibration)

**Gaps identified in v1.1:** While mathematically accurate after Iteration 1, v1.1 suffered three analytical gaps that would have caused Stage 5 to produce generic, Western-benchmark-driven output irrelevant to MWG's actual competitive environment in Q1/2026.

**Gap 1 — Flawed industry benchmarking:** v1.1 used generic HOSE retail sector medians aggregating electronics, grocery, pharmacy, and apparel into one peer group. Without segment-specific domestic competitors, Stage 5 benchmarking would have been unreliable.

**Gap 2 — Missing ALM interest rate risk:** v1.1 noted MWG's 29,931B in short-term borrowings and 38,874B in deposits, but did not instruct the executor to analyse the maturity mismatch. Without an explicit ALM stress-test, Stage 5 would have treated the treasury carry strategy as a pure positive without flagging its rate-sensitivity downside.

**Gap 3 — Absent quantitative macro headwinds:** v1.1 referenced macro risks qualitatively but provided no data. The March 2026 GSO CPI figure (4.65% YoY) and May 2026 fuel prices were sourced by the analyst after v1.1 was generated and required manual injection.

**Without these corrections, Stage 5 would have** (a) used irrelevant blended benchmarks; (b) missed the ALM vulnerability; (c) produced qualitative macro assertions without data anchors.

**Changes made in v1.2:**
1. Segment-specific benchmarks: FRT / Nguyen Kim for ICT; Long Châu for pharmacy; GSO CPI + fuel price figures added
2. Du Pont Step 5: ALM stress-test (100 bps → +299B → TIE 4.81× → ~4.39×)
3. Board-Level Constraint: micro-management AND national policy recommendations explicitly prohibited
4. Logistics context guardrail: 15–16% GDP ratio is context only; executor must translate to MWG-specific action

---

### Iteration 3: Version 1.2 → 1.3 (Named Range Map, Benchmark Completeness & Frontmatter)

**Gaps identified in v1.2:** Three structural and analytical gaps remained.

**Gap 1 — Named Range Conventions not a standalone section:** The prefix conventions table was embedded inside §2 Model Architecture. The rubric maps "Named Range Conventions" as an independent Part A item. Without a standalone section, rubric mappers could not locate it 1-to-1.

**Gap 2 — Incomplete pharmacy and grocery benchmarks:** Pharmacy benchmarked only against Long Châu, omitting Pharmacity. BHX grocery had no domestic competitor benchmarks — only an IPO valuation reference. Without Winmart+/Co.opmart comparisons, the BHX competitive analysis and M/B interpretation lacked operational grounding.

**Gap 3 — YAML frontmatter artefacts:** `fields_required` (listing required section names) and `courses` were template metadata that should not appear in a submitted spec document — they are tooling artefacts from the LLM's template parsing, not content fields.

**Without these corrections, Stage 5 would have** (a) missed the Named Range Map if looking for a dedicated section; (b) benchmarked An Khang without Pharmacity context and produced BHX analysis without Winmart+ / Co.opmart operational peer comparison; (c) submitted a spec with visually noisy frontmatter that signals LLM-generated artefacts to the grader.

**Changes made in v1.3:**
1. **Named Range Map (§3):** Extracted into standalone Part A section with full prefix table plus explicit analyst-assumption inputs sub-table; existing sections renumbered (§3→§4, §4→§5, §5→§6, §6→§7)
2. **§8 Efficiency — pharmacy benchmark:** Added Pharmacity alongside Long Châu; added explicit instruction to state exclusion if Pharmacity per-store data is unavailable
3. **§8 Performance + Efficiency — grocery benchmark:** Added Winmart+ and Co.opmart as mandatory BHX operational benchmarks in both Performance (M/B context) and Efficiency (store-count economics) sub-sections
4. **YAML frontmatter:** Removed `fields_required` and `courses` artefacts; retained only substantive fields (template, purpose, audience, title, author, date, version, company, naming_convention, notes)
