---
template: spec
purpose: Technical specification for MWG FY2025 ratio model and analysis — defines scope, inputs, formulas, validation, and analysis requirements precisely enough that any competent executor (human or LLM) can produce correct output
audience: Adam Stauffer (BUS-629 instructor); EMBA peers
title: "Mobile World Investment Corporation (MWG) — FY2025 Performance Ratios Technical Specification"
author: Nguyen Manh Thai
date: 2026-05-25
version: "1.1"
company: "Mobile World Investment Corporation (MWG, HOSE)"
fields_required:
  - title
  - author
  - date
  - version
  - company
  - scope
  - model_architecture
  - data_inputs
  - derived_inputs
  - formulas
  - validation
  - analysis_requirements
  - output_format
  - references
naming_convention: YYYY-MM-DD-{slug}.md
courses:
  - BUS-629
notes: >
  Spec version 1.1 corrects a unit-mismatch gap identified during HIL review
  (see Section 6 Validation Rules and HIL note at end of document).
  Share price is denominated in raw VND (not VND billions), so the template
  formula share_price × shares_outstanding yields VND millions, not VND
  billions. MVA and Market-to-Book are corrected accordingly.
---

# MWG FY2025 Performance Ratios — Technical Specification

**Author:** Nguyen Manh Thai
**Date:** 2026-05-25
**Version:** 1.1 (HIL-revised — see unit-mismatch correction note)
**Company:** Mobile World Investment Corporation · Ticker: MWG · Exchange: Ho Chi Minh Stock Exchange (HOSE)

---

## 1. Scope & Objective

This specification fully defines the Excel ratio model and the analytical work for Mobile World Investment Corporation (MWG, HOSE) using audited FY2025 consolidated financial statements.

- **Company:** Mobile World Investment Corporation (Công ty Cổ phần Đầu tư Thế Giới Di Động)
- **Ticker / Exchange:** MWG · HOSE
- **Fiscal Period:** FY2025 (January 1 – December 31, 2025); prior-year comparative is FY2024
- **Reporting Standard:** Vietnamese Accounting Standards (VAS). Critical VAS–IFRS difference: VAS does not require operating lease capitalisation (no IFRS 16 equivalent). Consequently, long-term debt = 0 and no right-of-use assets are recorded. The LT debt ratio and LT debt-to-equity ratio are structurally zero and should be interpreted as N/A rather than as low-leverage signals.
- **Reporting Currency:** VND billions (1 VND billion = 10⁹ VND). All balance sheet, income statement, and cash flow figures are in VND billions unless otherwise noted.
- **Share Price Unit Exception:** The share price input (`share_price`) is in raw VND per share (not VND billions). See Section 4 Derived Inputs for the unit-corrected market capitalisation formula.
- **Analytical Objective:** Compute 25+ performance ratios across six categories (Performance, Profitability, Efficiency, Leverage, Liquidity, Du Pont), interpret the results against sector benchmarks, and deliver 3–5 actionable strategic recommendations.
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
- *Inputs:* Financial statement tabs (data entered via openpyxl script from audited filings) + four Ratios tab assumption cells (C8:C11)
- *Calculations:* Ratios tab rows 12–38 (derived inputs) and rows 43–76 (ratio formulas)
- *Outputs:* Ratio values in Ratios!C43:C76; Cover tab spot-check table

---

### 3. Data Inputs

All values are sourced from MWG Audited Consolidated Financial Statements FY2025 (primary) and CafeF.vn historical price feed (share price). All figures in VND billions unless the Unit column specifies otherwise.

#### Balance Sheet Inputs

| Named Range | Description | FY2025 (curr) | FY2024 (prior) | Unit |
|---|---|---:|---:|---|
| `BAL_cash_marketable_securities_curr` | Cash & short-term financial investments | 38,874 | 34,221 | VND B |
| `BAL_receivables_curr` / `_prior` | Trade and other receivables | 10,183 | 8,826 | VND B |
| `BAL_inventories_curr` / `_prior` | Inventories | 27,267 | 22,245 | VND B |
| `BAL_other_current_curr` / `_prior` | Other current assets | 878 | 544 | VND B |
| `BAL_assets_current_curr` / `_prior` | Total current assets (sum) | 77,202 | 65,836 | VND B |
| `BAL_ppe_gross_curr` / `_prior` | PP&E gross | 19,568 | 19,265 | VND B |
| `BAL_accum_depreciation_curr` / `_prior` | Accumulated depreciation | 16,970 | 15,678 | VND B |
| `BAL_net_ppe_curr` / `_prior` | Net tangible fixed assets | 2,598 | 3,587 | VND B |
| `BAL_intangibles_curr` / `_prior` | Intangible assets / goodwill | 0 | 0 | VND B |
| `BAL_other_assets_curr` / `_prior` | Other long-term assets | 4,146 | 1,014 | VND B |
| `BAL_assets_total_curr` / `_prior` | **Total Assets** | **83,946** | **70,437** | VND B |
| `BAL_debt_short_term_curr` / `_prior` | Short-term bank borrowings | 29,931 | 27,300 | VND B |
| `BAL_payables_curr` / `_prior` | Accounts payable | 13,114 | 9,180 | VND B |
| `BAL_other_current_liabilities_curr` / `_prior` | Other current liabilities | 7,725 | 5,836 | VND B |
| `BAL_liabilities_current_curr` / `_prior` | Total current liabilities (sum) | 50,770 | 42,316 | VND B |
| `BAL_debt_long_term_curr` / `_prior` | Long-term debt | 0 | 0 | VND B |
| `BAL_other_lt_liabilities_curr` / `_prior` | Other long-term liabilities | 0 | 0 | VND B |
| `BAL_common_stock_curr` / `_prior` | Common stock (paid-in capital) | 14,532 | 15,174 | VND B |
| `BAL_retained_earnings_curr` / `_prior` | Retained earnings | 18,644 | 12,947 | VND B |
| `BAL_equity_shareholders_curr` / `_prior` | **Total shareholders' equity** | **33,176** | **28,121** | VND B |
| `BAL_liabilities_total_curr` / `_prior` | Total liabilities | 50,770 | 42,316 | VND B |

> **Model note:** Model total assets (83,946 / 70,437) differs slightly from audited financial statement totals (84,066 / 70,416) because the simplified 8-row template does not capture all MWG sub-line items. The balance sheet equation holds within the model: Assets = Liabilities + Equity (83,946 = 50,770 + 33,176 ✓).

#### Income Statement Inputs

| Named Range | Description | FY2025 | Unit |
|---|---|---:|---|
| `INC_sales` | Net revenue (net sales) | 155,928 | VND B |
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
| `CASH_investing` | Cash used for investments (CFI) | −6,661 | VND B |
| `CASH_financing` | Cash from financing activities (CFF) | 668 | VND B |
| `CASH_capex` | Capital expenditures | −888 | VND B |

> **CF reconciliation check:** CFO + CFI + CFF = 6,096 − 6,661 + 668 = +103B ≈ change in cash & deposits ✓

#### Market & Assumption Inputs (Ratios tab, cells C8:C11)

| Named Range | Description | Value | Unit |
|---|---|---:|---|
| `share_price` | Closing price Dec 31, 2025 (CafeF.vn verified) | 88,400 | VND per share |
| `shares_outstanding` | Shares outstanding | 1,469.7 | Millions of shares |
| `cost_capital` | WACC (country-risk-adjusted) | 13.5% | % |
| `tax_rate` | Effective tax rate | 20.0% | % |

---

### 4. Derived Inputs

All derived inputs are computed in Ratios tab rows 12–38. Formulas are expressed in named-range notation.

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

> ¹ **Unit-mismatch correction (HIL revision):** The template formula `share_price × shares_outstanding = 88,400 × 1,469.7 = 129,921,480` yields VND millions (raw VND per share × millions of shares = millions of VND). Dividing by 1,000 converts to VND billions, consistent with all balance sheet figures. The corrected `market_capitalization = 129,921.5 VND billions`. The raw template cell C12 shows 129,921,480; the Stage 5 executor must apply the ÷ 1,000 correction when computing MVA and Market-to-Book. See also Validation Rule 6 in Section 6.

---

### 5. Ratio Definitions & Formulas

All ratios use named-range notation. Expected output values are derived from Stage 3 workbook (Ratios tab C43:C76) with unit corrections applied where noted.

#### Performance

| Ratio | Formula (named-range notation) | Expected Output | Unit |
|---|---|---:|---|
| Market Value Added (MVA) | `market_capitalization − currentYear_equity` ¹ | 96,745.5 | VND B |
| Market-to-Book | `market_capitalization / currentYear_equity` ¹ | 3.91 | × |
| Economic Value Added (EVA) | `currentYear_after_tax_operating_income − (cost_capital × startYear_total_capitalization)` | 4,453.5 | VND B |

> ¹ Use unit-corrected `market_capitalization = 129,921.5 VND billions` (not the raw template value of 129,921,480).

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

> **VAS Note:** LT Debt Ratio = 0% and LT Debt-to-Equity = 0% are structural under VAS (no IFRS 16 lease capitalisation). Do not interpret as conservative financing. MWG carries 29,931B in short-term bank borrowings. The correct leverage signal is Total Debt Ratio (60.5%) and TIE (4.81×).

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

### 6. Validation Rules

The Stage 5 executor must verify all six rules before proceeding to analysis. Flag any breach; do not suppress.

| # | Rule | Check | Tolerance |
|---|---|---|---|
| 1 | **Balance Sheet balance** | `BAL_assets_total_curr = BAL_liabilities_total_curr + BAL_equity_shareholders_curr` → 83,946 = 50,770 + 33,176 ✓ | 0 |
| 2 | **Income allocation** | `INC_net = INC_dividends + INC_addition_retained_earnings` → 7,073 = 1,478 + 5,595 ✓ | 0 |
| 3 | **ATOI derivation** | `currentYear_after_tax_operating_income = INC_net + INC_interest_expense × (1 − tax_rate)` → 8,249.8 = 7,073 + 1,471 × 0.80 ✓ | ≤ 0.1B |
| 4 | **Du Pont ROA** | `RATIO_operating_profit_margin × RATIO_asset_turnover ≈ RATIO_roa` → 5.29% × 2.21 = 11.69% ≈ 11.71% ✓ | ≤ 0.5% |
| 5 | **Du Pont ROE** | `RATIO_leverage × RATIO_asset_turnover × RATIO_operating_profit_margin × RATIO_debt_burden ≈ RATIO_roe` → 2.53 × 2.21 × 5.29% × 0.857 = 25.34% ≈ 25.15% ✓ | ≤ 0.5% |
| 6 | **Market cap unit correction** | `market_capitalization (VND B) = share_price × shares_outstanding / 1,000 = 88,400 × 1,469.7 / 1,000 = 129,921.5B`. Raw template cell C12 = 129,921,480 (VND millions). MVA and M/B must use the ÷1,000 corrected value. Raw template outputs MVA ≈ 129.9M (wrong) and M/B ≈ 3,916× (wrong). | Unit match required |

---

## Part B — Analysis Specification

### 7. Analysis Requirements

For each ratio category below, interpret the computed values, apply the listed benchmarks, and note cross-category connections.

**Performance (MVA, M/B, EVA)**
- Interpret EVA = 4,453.5B VND as the spread between after-tax operating return and the 13.5% WACC hurdle applied to start-of-year capital.
- Interpret M/B = 3.91× against the HOSE retail sector median (~1.5–2.5×). A ratio materially above 1× confirms market expectation of continued value creation. Note that the pending Bách Hóa Xanh (BHX) segment IPO may compress this premium if BHX is spun off at a valuation above its book contribution.
- MVA = 96,745.5B represents the market's total value added above book equity. Assess sustainability relative to the EVA trajectory.
- **Cross-category link:** EVA sustainability depends on operating profit margin (Efficiency) and the 13.5% WACC assumption. If BHX margin compresses (see Hypothesis 2), ATOI falls and EVA narrows.

**Profitability (ROA, ROC, ROE)**
- Benchmark ROE (25.15%) against HOSE consumer discretionary median (~12–18%). Decompose into the Du Pont drivers before attributing performance.
- ROC = 29.34% reflects zero long-term debt under VAS; interpret against WACC of 13.5% — the spread (≈15.8 pp) is the core value-creation argument.
- Flag that ATOI includes other income (financial income of 3,107B from deposit placement). Isolate the EBIT-based operating return from the treasury carry income contribution, which is not recurring core retail income.
- **Cross-category link:** High ROE is partly driven by financial leverage (2.53×, Leverage section) and high asset turnover (2.21×, Efficiency). Du Pont section must decompose this.

**Efficiency (Turnover, Margins)**
- Asset Turnover = 2.21× is high for a multi-format retailer; benchmark against HOSE retail peers (~1.5–2.0×). Assess whether Northern BHX rollout will dilute this as capital base expands ahead of revenues.
- Inventory Turnover = 5.62× (65 days): benchmark against FY2024 model-computed level and management's own 5.05× (FY2025 Annual Report, p.25). Note the improvement reflects better stock discipline at TGDĐ/DMX but may reverse as BHX scales in lower-density Northern markets.
- Collection Period = 20.7 days: typical for a retail group with B2B receivables from franchisees and corporate clients.
- Net Profit Margin = 4.54% versus Gross Margin = (155,928 − 124,926) / 155,928 = 19.9%. The gap between gross and net margin (≈15.4 pp) is absorbed by SG&A (14.1%), D&A (1.2%), and net interest/tax (1.4%). Flag that financial income of 3,107B inflates the net margin relative to pure retail operating performance.

**Leverage**
- LT Debt Ratio = 0% is a VAS structural artefact, not a low-risk signal. Assess leverage through Total Debt Ratio (60.5%) and TIE (4.81×).
- TIE = 4.81× and Cash Coverage = 6.10× are acceptable but not strong for a company carrying 29,931B in short-term rollover debt. Stress-test: if interest rates rise 100 bps, TIE falls to approximately 4.0× (still above 3× threshold).
- Debt Burden = 0.857× indicates that non-operating income (financial income, net of taxes) materially reduces the effective tax-and-interest drag on ATOI, allowing net income to be 85.7% of ATOI despite the absence of LT debt tax shield.

**Liquidity**
- Current Ratio = 1.52×: adequate. Benchmark minimum for retail: 1.2×. Monitor: if BHX inventory front-loading increases current assets without proportional revenue, ratio may widen artificially.
- Quick Ratio = 0.97×: below 1.0×. This is typical for inventory-heavy retail groups; however, the 38,874B cash & ST investments position provides a strong de facto liquidity buffer.
- Cash Ratio = 0.77×: MWG's "smart carry trade" strategy (borrowing short at low rates, placing 33,874B in higher-yield deposits) means that the cash ratio overstates available operational liquidity — a portion of these deposits serve as collateral for ST borrowings.
- **Cross-category link:** High Cash Ratio + Low Quick Ratio reveals that inventory (27,267B) is the critical variable. Inventory Turnover (Efficiency) and its sustainability under BHX expansion is therefore the primary liquidity risk.

---

### 8. Du Pont Decomposition

**Target identity:**
> ROE = Financial Leverage × Asset Turnover × Operating Profit Margin × Debt Burden
> 25.34% = 2.53 × 2.21 × 5.29% × 0.857

**Decomposition instructions for Stage 5 executor:**

1. Compute each of the four Du Pont components from the named ranges in Section 5.
2. Identify the **primary ROE driver**: Asset Turnover (2.21×) is the dominant component for a retail group operating on thin margins. This is characteristic of high-volume, low-margin retail. Confirm or challenge this based on the computed values.
3. Interpret the **Debt Burden (0.857×)**: This ratio is below 1.0× because non-operating income (financial income) supplements EBIT-level earnings, such that net income is lower than ATOI as a percentage. This is unusual — typically Debt Burden compresses ROE below the ATOI-based return. Here it partially offsets leverage, confirming that treasury income is structurally propping ROE.
4. Assess **sustainability**: High Asset Turnover is achievable at current scale. If BHX expands its store count from ~1,700 to 2,000+ in FY2026, capital base grows faster than revenue in the near term, which will compress Asset Turnover. Quantify the sensitivity: a 10% asset increase with flat revenue reduces Asset Turnover from 2.21× to approximately 2.01×, reducing Du Pont ROE by approximately 2 percentage points.
5. Verify Du Pont ROE ≈ direct ROE within 0.5% tolerance (Validation Rule 5).

---

### 9. Strategic Recommendations

Provide **exactly 4 recommendations**, each meeting all three standards below:

**Evidence standard:** Each recommendation must cite at least one specific ratio value from Section 5 and one directional data point (year-over-year change, benchmark gap, or trend).

**Actionable specificity:** Each recommendation must name a concrete management action (not "improve efficiency" — instead "reduce average days in inventory from 65 days to below 55 days by tightening BHX northern hub replenishment cycles").

**Format per recommendation:**
```
### R[n]: [Title]
- **Ratio evidence:** [Ratio name] = [value], vs. benchmark/prior [value]
- **Observation:** [One sentence on what the ratio reveals]
- **Recommendation:** [Specific management action]
- **Risk if not acted upon:** [Directional consequence on a named ratio]
```

**Required recommendation coverage (one per area):**
1. Earnings quality / financial income dependency (Operating Profit Margin vs. Net Margin gap)
2. BHX inventory efficiency ahead of Northern expansion (Inventory Turnover)
3. Short-term debt rollover and interest coverage (TIE, Total Debt Ratio)
4. Market valuation and BHX segment disclosure (MVA, M/B in context of pending BHX IPO)

---

### 10. Output Format

The Stage 5 analysis deliverable must conform exactly to the following structure:

**File format:** Markdown (`.md`)
**Length:** 1,400–1,800 words (body only; exclude frontmatter and reference section)
**Tone:** Senior analyst memo — factual, direct, quantitatively grounded. No marketing language. No hedging without data support.
**Audience:** Executive reader with financial literacy; does not need formula derivations explained.

**Required sections in order:**

```
## Executive Summary          (~150 words)
## Ratio Results Summary      (table: all 25+ ratios with name, value, unit, one-line interpretation)
## Du Pont Decomposition      (~200 words, includes the decomposition identity with computed values)
## Category Analysis          (~600 words total across 6 sub-sections, one per ratio category)
## Strategic Recommendations  (4 recommendations in the R[n] format specified in Section 9)
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

1. Mobile World Investment Corporation — Audited Consolidated Financial Statements FY2025. Available at: https://ir.thegioididong.com
2. Mobile World Investment Corporation — Audited Consolidated Financial Statements FY2024. Available at: https://ir.thegioididong.com
3. Mobile World Investment Corporation — Annual Report 2025. Available at: https://ir.thegioididong.com
4. CafeF.vn historical price feed — MWG closing price Dec 31, 2025 = 88,400 VND. Available at: https://cafef.vn/du-lieu/hose/mwg-cong-ty-co-phan-dau-tu-the-gioi-di-dong.chn
5. Stage 3 populated workbook: `2026-05-21-nguyen-mwg-financials.xlsx` (Ratios tab C43:C76, verified values used in Sections 3–5)
6. Stage 4 brief: https://github.com/adamwstauffer/shidler/blob/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage4-technical-specification.md
7. Spec template: https://github.com/adamwstauffer/shidler/blob/main/docs/templates/spec-template.md

---

## HIL Review Note (Human-in-the-Loop Iteration — Version 1.0 → 1.1)

**Gap identified in v1.0 draft:** In the first draft of this specification (v1.0), Section 3 Data Inputs listed `market_capitalization` as the raw template output of `share_price × shares_outstanding = 88,400 × 1,469.7 = 129,921,480` with unit labeled "VND B." Upon reviewing the Stage 3 workbook ratio outputs, the Market-to-Book ratio showed 3,916× and MVA showed approximately 129.9 million VND billions — both values were obviously wrong for a company with 33,176B in book equity.

**Root cause analysis:** The template formula computes `share_price (raw VND per share) × shares_outstanding (millions of shares) = result in millions of VND`. Since the balance sheet is denominated in VND billions, the market cap is 1,000× too large in the formula output. This is a unit mismatch: the template was designed for USD-denominated companies where share price (USD/share) × shares (millions) = USD millions, matching balance sheet units. For MWG, share price (88,400 VND/share) × 1,469.7M shares = 129,921,480 (VND millions), not VND billions.

**Changes made in v1.1:**
1. Added footnote ¹ to Section 3 (Data Inputs) flagging the unit mismatch
2. Revised Section 4 (Derived Inputs) to show corrected formula: `market_capitalization = share_price × shares_outstanding / 1,000 = 129,921.5 VND billions`
3. Revised Section 5 Performance ratios: MVA = 96,745.5B (not ~129.9M); Market-to-Book = 3.91× (not 3,916×)
4. Added Validation Rule 6 in Section 6 requiring Stage 5 executor to apply the ÷1,000 unit correction before computing MVA and Market-to-Book

**What this means for Stage 5:** Do not use the raw Ratios!C43 (MVA) or Ratios!C44 (M/B) values from the Excel file directly. Apply the correction per Validation Rule 6. EVA (Ratios!C45 = 4,453.5B) is not affected by the market cap unit mismatch and is correct as-is.
