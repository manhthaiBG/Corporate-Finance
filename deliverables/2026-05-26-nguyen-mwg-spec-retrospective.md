---
template: spec-retrospective
purpose: Structured self-evaluation of the Stage 4 MWG technical specification after seeing how an LLM executed it at Stage 5
audience: Adam Stauffer (BUS-629 instructor)
author: Nguyen Manh Thai
date: 2026-05-26
company: Mobile World Investment Corporation (MWG, HOSE)
spec_file: docs/specs/2026-05-25-nguyen-mwg-spec.md (v1.4)
stage5_output: deliverables/2026-05-26-nguyen-mwg-llm-raw.md
naming_convention: YYYY-MM-DD-{lastname}-{company-slug}-spec-retrospective.md
---

# Stage 4 Spec — Retrospective

**Author:** Nguyen Manh Thai  
**Date:** 2026-05-26  
**Company:** Mobile World Investment Corporation (MWG, HOSE)  
**Spec being evaluated:** `docs/specs/2026-05-25-nguyen-mwg-spec.md` (v1.4, incorporating instructor PR feedback)  
**Stage 5 LLM output:** `deliverables/2026-05-26-nguyen-mwg-llm-raw.md`  
**Verification table:** `analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md`

---

## 1. Section-by-Section Verdict

| Spec section | Verdict | Symptom in Stage 5 LLM output |
|--------------|---------|-------------------------------|
| Part A.1 — Scope & Objective | **Clear** | LLM correctly identified company, fiscal period, VAS constraints, and analytical objective. All scope framing was accurately reproduced. |
| Part A.2 — Model Architecture | **Clear** | LLM correctly described the six-tab structure, color coding, and data flow. No architectural misinterpretation. |
| Part A.3 — Named Range Map | **Vague** | LLM used named ranges (`startYear_receivables`, `startYear_inventory`) correctly in the formula table but applied averaging conventions in computation, indicating the named-range labels did not communicate the *contrast with textbook averaging*. The section listed the correct names but never stated "do not average start and end year values — use start-of-year only." |
| Part A.4 — Data Inputs | **Clear** | All balance sheet, income statement, and cash flow inputs were reproduced correctly with accurate FY2025 and FY2024 values. No data transposition errors. |
| Part A.5 — Derived Inputs | **Clear** | Unit-correction formula (÷1,000) for market capitalization was correctly applied; M/B = 3.91×, MVA = 96,745.5B. ATOI derivation confirmed correct. |
| Part A.6 — Ratio Definitions & Formulas | **Vague** | The Efficiency ratio table listed `startYear_inventory` and `startYear_receivables` as denominators — the correct named ranges. However, without an explicit anti-averaging instruction, the LLM defaulted to averaging convention in calculation, producing Inventory Turnover of 5.05× vs. correct 5.62× and Receivables Turnover of 16.40× vs. correct 17.67×. The formula notation was correct; the behavioral instruction was absent. |
| Part A.7 — Validation Rules | **Clear** | LLM correctly applied all six validation rules: balance sheet balance, income allocation, ATOI derivation, Du Pont ROA, Du Pont ROE, and market cap unit correction. All rules passed. |
| Part B.8 — Analysis Requirements | **Clear** | Segment-specific benchmarks were used (FRT/Nguyen Kim for ICT, Long Châu/Pharmacity for pharmacy, Winmart+/Co.opmart for BHX). Pharmacity exclusion was correctly stated. Fuel cost headwind was quantified directionally. Board-level constraint (no national policy) was respected. |
| Part B.9 — Du Pont Decomposition | **Clear** | Du Pont identity was correctly computed (25.34% = 2.53 × 2.21 × 5.29% × 0.857). ALM stress-test was executed: 100 bps → +299B interest → TIE ~4.00×. BHX expansion sensitivity was addressed. All five steps followed per spec. |
| Part B.10 — Strategic Recommendation Requirements | **Clear** | All four recommendations used the R[n] format, included ratio evidence, observation, recommendation, and risk consequence. Board-level scope was maintained. Micro-management and national policy exclusions were respected in all four. |
| Part B.11 — Output Format | **Clear** | All six required sections appeared in order: Executive Summary, Ratio Results Summary table, Du Pont, Category Analysis, Strategic Recommendations, Model Limitations, References. Length approximately 1,650 words (body) — within the 1,400–1,800 target. |

---

## 2. Top Three Gaps with Evidence

### Gap 1: Absence of an Anti-Averaging Instruction for Efficiency Ratio Denominators

**Where it surfaced:** Efficiency section of the LLM raw output. Inventory Turnover reported as 5.05× (LLM averaged: (22,245 + 27,267) / 2 = 24,756B) vs. correct 5.62× (spec: `startYear_inventory` = 22,245B). Receivables Turnover reported as 16.40× (LLM averaged: (8,826 + 10,183) / 2 = 9,504.5B) vs. correct 17.67× (`startYear_receivables` = 8,826B). Four efficiency ratios were affected (including the cascading collection period and days in inventory).

**Spec cause:** Part A.6 (Ratio Definitions & Formulas) listed `startYear_inventory` and `startYear_receivables` as the denominators in the formula column. This is correct notation. However, the spec never stated explicitly: *"Do not apply the standard textbook convention of averaging start and end-of-year values. Use start-of-year denominators exclusively — this matches the named-range convention in the Stage 3 workbook."* An LLM trained on thousands of corporate finance textbooks defaults to the averaging convention unless explicitly overridden. The named-range labels alone were insufficient to override that default behavior.

**Consequence:** The LLM benchmarked MWG's Inventory Turnover (5.05×) below FRT's range (~5.5–5.8×), concluding MWG lags peers. The corrected value (5.62×) places MWG within or above that range — a materially different competitive signal. This is the kind of spec gap that changes the strategic conclusion, not just the arithmetic.

**Fix (exact language):** Add the following note immediately below the Efficiency ratio table in Part A.6:

> ⚠️ **Denominator convention (efficiency ratios):** All efficiency ratio denominators use **start-of-year values only** (`startYear_*` named ranges). Do **not** apply the textbook averaging convention (start + end) / 2. The start-of-year requirement aligns with the named-range architecture of the Stage 3 workbook and eliminates double-counting of within-year changes. Averaging `startYear_inventory` and `BAL_inventories_curr` will understate turnover by approximately 10% in a growth year.

---

### Gap 2: Financial Income Source Identification Not Distinguished from Operating Income

**Where it surfaced:** Profitability analysis section of the LLM raw output. The LLM correctly flagged that "financial income (VND 3,107B) inflates Net Margin above pure retail operating performance" — but it described the financial income source as generically "treasury carry income" without identifying the exact input it came from (`INC_other_income`). In the Debt Burden discussion, the LLM computed the ratio correctly (0.857×) but described the mechanics imprecisely: it stated "non-operating financial income partially reduces the effective drag on ATOI" — which is the opposite of the mathematical reality. Financial income boosts *net income* (the numerator) above what ATOI would predict, making Debt Burden < 1.0× because ATOI > net income in ratio terms.

**Spec cause:** Part B.8 (Analysis Requirements, Profitability section) instructed: *"Flag that ATOI includes financial income (3,107B from deposit placement)."* This instruction contains a factual error: ATOI does **not** include financial income. ATOI = Net Income + Interest Expense × (1 − tax rate) = 7,073 + 1,471 × 0.80 = 8,249.8B. Financial income is in net income but is removed from ATOI by the add-back formula. The spec's own instruction was ambiguous (saying financial income is "in ATOI" when it means "the financial income is the reason net income and ATOI diverge"). This confused the LLM's Debt Burden interpretation.

**Fix (exact language):** Replace the following line in Part B.8 (Profitability):

*Current:* `Flag that ATOI includes financial income (3,107B from deposit placement). Isolate EBIT-based retail return from treasury carry income, which is not recurring core retail income.`

*Revised:* `Flag that ATOI (VND 8,249.8B) is computed from Net Income by adding back after-tax interest expense — financial income of VND 3,107B is included in Net Income but is NOT a component of ATOI. The divergence between ATOI (8,249.8B) and Net Income (7,073B) is driven by interest expense exceeding the financial income net contribution; consequently, Debt Burden = Net Income / ATOI = 0.857× < 1.0×. The executor must flag that the VND 3,107B financial income is treasury carry income (deposit placement strategy) rather than recurring retail operating income — it would disappear if carry spread compressed to zero in a tightening rate environment.`

---

### Gap 3: Benchmark Data Availability Not Pre-Confirmed for Pharmacity and Winmart+

**Where it surfaced:** Efficiency section of the LLM raw output. The LLM correctly stated "Pharmacity per-store economics are not publicly available from HOSE disclosures; exclusion is noted explicitly per specification instruction" — which was the correct outcome. However, for Winmart+ (Masan Consumer Holdings), the LLM cited estimated figures ("~VND 33–37B per store in established Northern markets") without sourcing them or noting the estimation basis. There is no HOSE filing that directly states Winmart+ revenue-per-store at this granularity; the LLM generated a plausible-sounding estimate without flagging it as derived.

**Spec cause:** Part B.8 (Efficiency, Grocery Segment) instructed: *"Benchmark BHX store-count efficiency and revenue-per-store trajectory against Winmart+ and Co.opmart."* The spec required the benchmark but did not specify what to do if Winmart+ per-store data is not available in public filings — it provided explicit guidance only for Pharmacity (*"if publicly available per-store economics for Pharmacity are unavailable, state this exclusion explicitly — do not substitute generic pharmaceutical medians"*). The equivalent exclusion instruction was not written for Winmart+/Co.opmart, allowing the LLM to generate estimated figures without flagging the estimation basis.

**Fix (exact language):** Add the following sentence to Part B.8, Grocery Segment sub-section, after the Winmart+ and Co.opmart instruction:

> If Winmart+ or Co.opmart segment-level revenue-per-store data is not directly available from HOSE filings or Masan Consumer Holdings investor relations disclosures, state the data gap explicitly and note any estimates as derived (not sourced). Do not substitute analyst consensus estimates or internal model outputs as if they were reported figures.

---

## 3. Revisions

If I re-ran with a revised spec, three targeted changes would address the gaps above:

1. **Add an anti-averaging note to the Efficiency ratio table** — addresses Gap 1. The single paragraph quoted in Gap 1 (Fix) would have prevented four efficiency ratio errors and the resulting benchmark conclusion error. Approximately 60 words; zero restructuring required.

2. **Correct the ATOI/financial income instruction in Part B.8 (Profitability)** — addresses Gap 2. Replace the ambiguous "flag that ATOI includes financial income" with the precise statement that financial income is IN net income but NOT in ATOI, and that Debt Burden < 1.0× results. This would have produced a cleaner, more accurate Debt Burden interpretation in the LLM output without any arithmetic impact on the ratio.

3. **Add a parallel exclusion instruction for Winmart+/Co.opmart benchmark data** — addresses Gap 3. Extending the Pharmacity exclusion protocol to grocery benchmarks would have flagged the LLM's Winmart+ revenue-per-store estimates as derived rather than sourced. The LLM's numbers were plausible, but a spec-graded deliverable should not generate unsourced estimates without disclosure.

---

## 4. Effectiveness Rating

| Rating | Anchor |
|--------|--------|
| **5** | I would hand this spec to a junior analyst and trust their output without re-checking. |
| **4** | Solid overall; one section needs sharpening before I'd ship it. |
| **3** | Workable with revisions; spec has gaps the LLM had to guess around. |
| **2** | Substantial rework needed; LLM output diverged in meaningful ways traceable to the spec. |
| **1** | Spec is not yet usable as a standalone artifact. |

**My rating: 4**

**Justification (100–200 words):**

The spec achieved its primary objective: the LLM produced a structurally correct, Board-appropriate analysis of MWG FY2025 across all six ratio categories, with accurate Du Pont decomposition, correct unit-correction application (the hardest single instruction in the spec), and four properly scoped strategic recommendations. This is strong performance against a complex analytical brief. A grader who read only the strategic recommendations section would conclude the spec worked.

The one section that requires sharpening is Part A.6 / Part B.8 around the efficiency ratio denominator convention. The four efficiency errors (Inventory Turnover at 5.05× vs. correct 5.62×; Receivables Turnover at 16.40× vs. 17.67×; and cascading collection period / days in inventory) trace to a single missing instruction that I could add in one paragraph. These errors changed a benchmarking conclusion — MWG appeared to lag FRT in inventory turns when it actually meets or exceeds the peer range. That is not a trivial error: it would have led to a strategic recommendation about inventory management that the corrected data does not support.

I do not rate this a 5 because I would not hand this spec to a junior analyst without the anti-averaging note and trust the efficiency section without re-checking. The three corrections identified above are small in scope but material in analytical consequence. A revised v1.5 spec incorporating these three edits would earn a 5.

---

## 5. Forward Link

In the next spec I write — whether for MWG in FY2026, a different Vietnamese retail conglomerate, or a non-finance domain — I will include a dedicated **"Convention Override" section** in Part A that explicitly lists every place where the spec's required approach departs from the standard textbook default: denominator conventions, day-count basis, unit scaling factors, and exclusion protocols. These are the gaps that generate systematic errors, not the gaps in analytical judgment.

---

## 6. Retrospective Process Feedback (≤150 words)

Filling out the Section 1 table with the "Symptom" column forced me to locate the exact LLM sentence or number that revealed each gap — rather than forming a general impression that something was "off." Without that column, I would have written "efficiency ratios could be clearer" and moved on. Having to write "LLM reported Inventory Turnover = 5.05× because it used average inventory denominator (24,756B) instead of start-of-year (22,245B)" forced me to trace the error to its exact spec location. That diagnostic chain — symptom → spec location → exact fix — is the intellectual value of the retrospective.

One structural addition I would suggest: a **"Severity" column** in the Section 1 table with three options (Minor / Analytical Consequence / Conclusion-Changing). "Vague" by itself does not tell a grader how much the gap mattered. The Inventory Turnover gap was conclusion-changing; the Winmart+ sourcing gap was minor. The distinction affects how much remediation energy to spend on each.

---

*Retrospective compiled by Nguyen Manh Thai · 2026-05-26 · BUS-629 VEMBA International Corporate Finance · Shidler College of Business*
