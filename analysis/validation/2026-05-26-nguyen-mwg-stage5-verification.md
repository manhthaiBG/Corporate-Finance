# Stage 5 — Manual Ratio Verification Table

**Company:** Mobile World Investment Corporation (MWG, HOSE)  
**Analyst:** Nguyen Manh Thai  
**Date:** 2026-05-26  
**Stage 3 source:** `models/builds/2026-05-21-nguyen-mwg-financials.xlsx` (Ratios tab C43:C76)  
**LLM output compared:** `deliverables/2026-05-26-nguyen-mwg-llm-raw.md`  
**Spec version used:** `docs/specs/2026-05-25-nguyen-mwg-spec.md` v1.4

---

## Source Clarification

Three sources of ratio values exist in this project. The column being graded is **Manual vs. LLM**:

| Source | Origin | Role in this table |
|--------|--------|--------------------|
| **Template auto-computed** | Stage 3 workbook Ratios tab (Excel formulas) | Sanity check on both; not the graded column |
| **LLM's stated** | Raw output in `2026-05-26-nguyen-mwg-llm-raw.md` | Column being verified |
| **Manual (this table)** | Hand-recomputed from Stage 3 financial data | Primary column |

---

## Verification Table (8 Ratios)

> Ratios selected to span all six categories and target the formulas most likely to produce LLM discrepancies (averaging conventions, year-end vs. start-of-year denominators, day-count, unit scaling).

| # | Ratio | Formula (named-range notation) | Manual computation | Manual value | LLM's stated value | Match? | Note |
|---|-------|-------------------------------|--------------------|--------------|--------------------|--------|------|
| 1 | **Receivables Turnover** | `INC_sales / startYear_receivables` | 155,928 / 8,826 | **17.67×** | 16.40× | ❌ No | LLM used average receivables: (8,826 + 10,183) / 2 = 9,504.5B → 155,928 / 9,504.5 = 16.40×. Spec explicitly requires `startYear_receivables` (8,826B). |
| 2 | **Average Collection Period** | `startYear_receivables / currentYear_daily_sales_average` | 8,826 / (155,928 / 365) = 8,826 / 427.2 | **20.7 days** | 21.7 days | ❌ No | LLM used average receivables as numerator (9,504.5 / 427.2 = 22.2 days) AND applied 360-day denominator. Cascading errors from Receivables Turnover denominator. |
| 3 | **Inventory Turnover** | `INC_cost_goods_sold / startYear_inventory` | 124,926 / 22,245 | **5.62×** | 5.05× | ❌ No | LLM used average inventory: (22,245 + 27,267) / 2 = 24,756B → 124,926 / 24,756 = 5.05×. Spec explicitly requires `startYear_inventory` (22,245B). Most material error in the output. |
| 4 | **Days in Inventory** | `startYear_inventory / currentYear_cost_goods_sold_daily` | 22,245 / (124,926 / 365) = 22,245 / 342.3 | **65.0 days** | 72.3 days | ❌ No | Cascading from Inventory Turnover error: LLM used average inventory as numerator (24,756 / 342.3 = 72.3 days) instead of `startYear_inventory`. |
| 5 | **Return on Equity (ROE)** | `INC_net / startYear_equity` | 7,073 / 28,121 | **25.15%** | 25.15% | ✓ Yes | LLM correctly used start-of-year equity denominator per spec. |
| 6 | **Market-to-Book (M/B)** | `market_capitalization / currentYear_equity` | 129,921.5 / 33,176 | **3.91×** | 3.91× | ✓ Yes | LLM correctly applied the ÷1,000 unit correction (88,400 × 1,469.7M / 1,000 = 129,921.5B). Unit mismatch was the most important validation rule — passed. |
| 7 | **Times Interest Earned (TIE)** | `INC_ebit / INC_interest_expense` | 7,075 / 1,471 | **4.81×** | 4.81× | ✓ Yes | LLM used correct EBIT and interest expense inputs. ALM stress-test TIE computation (4.00×) is separately reviewed in verification item 8 below. |
| 8 | **ALM Stress-Test TIE** | `(INC_ebit − 299) / (INC_interest_expense + 299)` | (7,075 − 299) / (1,471 + 299) = 6,776 / 1,770 | **3.83×** | ~4.00× | ❌ No | LLM stated "TIE ~4.00×" under 100 bps shock. Correct calculation: EBIT is not directly reduced by the additional interest; the formula should be `INC_ebit / (INC_interest_expense + 299)` = 7,075 / 1,770 = **3.997× ≈ 4.00×** ✓ (LLM's result is correct). Manual check: 7,075 / (1,471 + 299) = 7,075 / 1,770 = **3.997×** — matches LLM within rounding. **Correction: This is a ✓ match.** |

---

## Discrepancy Summary

| # | Ratio | LLM Value | Correct Value | Error Magnitude | Root Cause |
|---|-------|-----------|---------------|-----------------|------------|
| 1 | Receivables Turnover | 16.40× | **17.67×** | −1.27× (−7.2%) | LLM used avg receivables instead of `startYear_receivables` |
| 2 | Average Collection Period | 21.7 days | **20.7 days** | +1.0 day (+4.8%) | Cascading from error #1 (avg receivables as numerator) |
| 3 | Inventory Turnover | 5.05× | **5.62×** | −0.57× (−10.1%) | LLM used avg inventory instead of `startYear_inventory` |
| 4 | Days in Inventory | 72.3 days | **65.0 days** | +7.3 days (+11.2%) | Cascading from error #3 (avg inventory as numerator) |

**Errors caught and corrected:** 4 (all in the Efficiency category)  
**Verified as correct:** 4 (ROE, M/B, TIE, ALM stress-test TIE)

---

## Pattern Analysis

The LLM applied averaging conventions (start + end / 2) to both receivables and inventory denominators — the standard textbook approach taught in most corporate finance courses. The spec, however, explicitly requires start-of-year denominators (`startYear_receivables`, `startYear_inventory`) to align with the named-range structure of the Stage 3 workbook. This is the most consequential systematic error in the raw output.

**Impact on analysis:** Inventory Turnover understated by 10.1% (5.05× vs. 5.62×) makes MWG appear less efficient than it is relative to the FRT benchmark (~5.5–5.8×). The raw output would have concluded that MWG's inventory velocity is below FRT's range; the corrected value places it within or slightly above — a materially different strategic signal for the inventory management recommendation.

**Unit correction validation:** The LLM correctly applied the critical ÷1,000 market capitalization conversion (Validation Rule 6), using M/B = 3.91× rather than the nonsensical 3,916× raw template value. This is the most important validation rule and was executed correctly.

**ALM stress-test:** The LLM's stated TIE of ~4.00× under 100 bps shock is arithmetically correct (7,075 / 1,770 = 3.997×). No error here.

---

## Corrected Efficiency Table

For reference when reading the Final Analysis:

| Ratio | LLM Output | Corrected (Spec Convention) | Correction Applied |
|-------|-----------|----------------------------|-------------------|
| Receivables Turnover | 16.40× | **17.67×** | Used `startYear_receivables` = 8,826B |
| Avg Collection Period | 21.7 days | **20.7 days** | Used `startYear_receivables` / (INC_sales/365) |
| Inventory Turnover | 5.05× | **5.62×** | Used `startYear_inventory` = 22,245B |
| Days in Inventory | 72.3 days | **65.0 days** | Used `startYear_inventory` / (COGS/365) |

---

*Verification compiled by Nguyen Manh Thai · 2026-05-26 · BUS-629 VEMBA Corporate Finance*
