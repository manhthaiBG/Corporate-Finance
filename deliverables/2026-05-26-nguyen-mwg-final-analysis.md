---
template: final-analysis
purpose: Stage 5 evaluated, annotated, and corrected analysis of MWG FY2025 ratio model
audience: Adam Stauffer (BUS-629 instructor)
title: Mobile World Investment Corporation (MWG) — FY2025 Performance Ratio Analysis (Final)
author: Nguyen Manh Thai
date: 2026-05-26
version: "1.0 (Stage 5 final)"
company: Mobile World Investment Corporation (MWG, HOSE)
spec_file: docs/specs/2026-05-25-nguyen-mwg-spec.md (v1.4)
llm_raw_output: deliverables/2026-05-26-nguyen-mwg-llm-raw.md
verification_table: analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md
spec_retrospective: deliverables/2026-05-26-nguyen-mwg-spec-retrospective.md
---

# Mobile World Investment Corporation (MWG) — FY2025 Performance Ratio Analysis

**Author:** Nguyen Manh Thai | **Date:** 2026-05-26 | **BUS-629 VEMBA International Corporate Finance**  
**Company:** Mobile World Investment Corporation · Ticker: MWG · Exchange: HOSE  
**Data source:** Audited Consolidated Financial Statements FY2025 (VAS); Stage 3 workbook `2026-05-21-nguyen-mwg-financials.xlsx`

> **LLM Evaluation Note:** This final analysis corrects four systematic errors in the raw LLM output (`2026-05-26-nguyen-mwg-llm-raw.md`). The LLM applied averaging conventions (start + end / 2) to efficiency ratio denominators, whereas the spec requires start-of-year values (`startYear_receivables`, `startYear_inventory`). All corrected values are sourced from the verification table (`2026-05-26-nguyen-mwg-stage5-verification.md`). See Section 5 (LLM Evaluation) for a full accounting of what the LLM got right, where it diverged, and the cause. See also the spec retrospective for the spec-level gaps that enabled this category of error.

---

## 1. Executive Summary

Mobile World Investment Corporation (MWG, HOSE) delivered a decisive FY2025 earnings recovery, reporting Net Income of VND 7,073 billion on Net Revenue of VND 155,928 billion — a four-year profit high. Return on Equity of 25.15% substantially outperforms the HOSE consumer discretionary median (12–18%), and Economic Value Added of VND 4,454 billion confirms that returns clear the 13.5% WACC hurdle. Market-to-Book of 3.91× prices in VND 96,745 billion of value above book equity — partially reflecting the embedded optionality of a Bách Hóa Xanh (BHX) segment IPO. Three structural risks qualify the headline strength: (1) approximately 36% of pre-tax profit derives from a short-term deposit carry trade that is rate-sensitive in Q1/2026's tightening cycle; (2) VND 29,931 billion in floating-rate short-term borrowings creates an unhedged asset-liability mismatch; and (3) BHX's Northern Vietnam expansion introduces near-term margin compression before scale economies emerge. Four Board-level recommendations follow directly from the ratio evidence.

---

## 2. Ratio Results Summary

> ⚠️ **Corrections applied:** Receivables Turnover, Average Collection Period, Inventory Turnover, and Days in Inventory values differ from the LLM raw output. Corrected values use `startYear` denominators per the specification. See verification table for arithmetic.

| Category | Ratio | Value | Unit | Signal |
|----------|-------|-------|------|--------|
| Performance | Market Value Added (MVA) | 96,745.5 | VND B | ✅ Positive |
| Performance | Market-to-Book (M/B) | 3.91 | × | ✅ Positive |
| Performance | Economic Value Added (EVA) | 4,453.5 | VND B | ✅ Positive |
| Profitability | Return on Assets (ROA) | 11.71 | % | ✅ Positive |
| Profitability | Return on Capital (ROC) | 29.34 | % | ✅ Positive |
| Profitability | Return on Equity (ROE) | 25.15 | % | ✅ Positive |
| Profitability | ROA [avg base] | 10.69 | % | ✅ Positive |
| Profitability | ROC [avg base] | 26.92 | % | ✅ Positive |
| Profitability | ROE [avg base] | 23.08 | % | ✅ Positive |
| Efficiency | Asset Turnover | 2.21 | × | ✅ Positive |
| Efficiency | Receivables Turnover ✏️ | **17.67** | × | ✅ Positive |
| Efficiency | Average Collection Period ✏️ | **20.7** | days | ✅ Positive |
| Efficiency | Inventory Turnover ✏️ | **5.62** | × | ✅ Positive |
| Efficiency | Days in Inventory ✏️ | **65.0** | days | ✅ Positive |
| Efficiency | Profit Margin | 4.54 | % | ⚠️ Monitor |
| Efficiency | Operating Profit Margin | 5.29 | % | ⚠️ Monitor |
| Leverage | LT Debt Ratio | 0.0 | % | ⚠️ Monitor (VAS artefact) |
| Leverage | LT Debt-to-Equity | 0.0 | % | ⚠️ Monitor (VAS artefact) |
| Leverage | Total Debt Ratio | 60.5 | % | ⚠️ Monitor |
| Leverage | Times Interest Earned (TIE) | 4.81 | × | ✅ Positive |
| Leverage | Cash Coverage | 6.10 | × | ✅ Positive |
| Leverage | Debt Burden | 0.857 | × | ⚠️ Monitor |
| Leverage | Financial Leverage | 2.53 | × | ⚠️ Monitor |
| Liquidity | NWC to Assets | 31.5 | % | ✅ Positive |
| Liquidity | Current Ratio | 1.52 | × | ✅ Positive |
| Liquidity | Quick Ratio | 0.97 | × | ⚠️ Monitor |
| Liquidity | Cash Ratio | 0.77 | × | ⚠️ Monitor |
| Du Pont | ROA (Du Pont) | 11.69 | % | ✅ Positive |
| Du Pont | ROE (Du Pont) | 25.34 | % | ✅ Positive |

*✏️ = Corrected from LLM raw output; see verification table for arithmetic.*

---

## 3. Du Pont Decomposition

**Identity (all values confirmed):**

ROE = Financial Leverage × Asset Turnover × Operating Profit Margin × Debt Burden  
**25.34% = 2.53 × 2.21 × 5.29% × 0.857**  
*(Du Pont 25.34% vs. direct ROE 25.15% — within 0.5% tolerance ✓)*

**Primary driver — Asset Turnover (2.21×):** Volume throughput is doing the heaviest lifting in MWG's ROE. The company generated VND 155,928 billion in revenue from a VND 70,437 billion starting asset base — a 2.21× ratio that confirms capital efficiency rather than margin expansion as the engine of outperformance. This is structurally appropriate for a retail group operating on thin margins but warrants monitoring as BHX expansion adds capital ahead of revenue.

**Debt Burden (0.857×) — unusual structure:** Net Income (VND 7,073B) is lower than ATOI (VND 8,250B) in absolute terms, yielding Debt Burden below 1.0×. This reflects interest expense exceeding the tax shield of interest, combined with the unusual channel: financial income (VND 3,107B) is included in net income but not in ATOI. The net result is that the carry trade boosts absolute net income but the ratio mechanics still show the drag — a structural signal that earnings quality requires independent assessment.

**ALM Interest Rate Gap Stress-Test (mandatory per spec §9):**  
MWG holds VND 29,931 billion in short-term floating-rate borrowings while locking approximately VND 33,874 billion in fixed-term deposits. A 100 bps rate shock on the floating borrowing base:

- Additional annual interest: VND 29,931B × 1% = **VND ~299 billion**
- Restated TIE: 7,075 / (1,471 + 299) = 7,075 / 1,770 = **3.997× ≈ 4.00×** *(from 4.81×)*
- Net Margin impact: ~0.19 pp compression (VND 299B / VND 155,928B)
- Carry spread risk: if deposit yields remain at ~6.0% (fixed-term, locked) while borrowing reprices to 6.5–7.0%, the ~VND 3,107B financial income buffer faces structural compression over the next 12–18 months

**Assessment:** The ALM structure is a strategic carry trade that has been profitable in the FY2024–2025 easing cycle. At 4.00× TIE under a 100 bps shock, the buffer remains adequate (above the 3× threshold), but a 150 bps shock — not implausible in Q1/2026 — compresses TIE to ~3.55×. The risk is two-sided: borrowing costs rise *and* carry spread compresses simultaneously if deposit maturities are concentrated in a single tranche that rolls at the same time as debt. A deposit laddering strategy (6M / 12M / 18M tranches) combined with pledge-secured, spread-fixed lending facilities would decouple these two movements, protecting the VND 3,107B financial income line regardless of rate direction. See R1 for the three-layer implementation structure.

**BHX Expansion Sensitivity:** A 10% increase in total assets (VND ~8,400B for Northern store rollout) with flat FY2025 revenue compresses Asset Turnover from 2.21× to ~2.01×, cascading through Du Pont to reduce ROE by approximately 2 percentage points. This confirms that BHX expansion must generate revenue faster than it consumes capital to be ROE-accretive.

---

## 4. Category Analysis

### 4.1 Performance

EVA of VND 4,453.5 billion signals genuine value creation above the 13.5% WACC hurdle (ATOI VND 8,249.8B vs. capital charge VND 3,796.3B on start-of-year capital). The spread is meaningful but sensitive to margin compression and capital expansion. M/B of 3.91× represents VND 96,745.5 billion of market value above book equity. The most important analytical context here is the structural valuation discount: BHX's grocery segment, with approximately VND 46,900 billion in FY2025 revenue, is valued by analysts at an estimated VND 80,000 billion in a standalone IPO scenario — approximately 61% of MWG's total market capitalization of VND 129,921.5 billion. This implies the ICT and pharmacy segments are being valued at approximately VND 49,921 billion combined, which may be understated given FRT (the nearest ICT peer) trades at 3.5–4.0× book. Segment-level disclosure would allow the market to re-rate each business unit independently, reducing the conglomerate discount.

### 4.2 Profitability

ROE of 25.15% is strong in absolute and relative terms. However, Du Pont decomposition reveals it is leverage- and turnover-driven, not margin-driven. Gross Margin of 19.9% (VND 31,002B) is healthy for Vietnamese retail, but the 15.4 pp gap between gross and net margin (4.54%) reflects SG&A absorption (14.1%), D&A (1.2%), and net interest/tax (1.4%). Stripping financial income of VND 3,107 billion, operating-only net margin approximates 2.9% — revealing that a meaningful portion of reported profitability is treasury carry income rather than retail operations improvement. This earnings quality risk is the central analytical concern for FY2026 forecasting.

Q1/2026 macro headwind: GSO CPI rose 4.65% YoY in March 2026 (+3.51% Q1/2026 average, +3.63% core). Sustained inflation at this level compresses real consumer purchasing power for discretionary electronics — MWG's highest-margin segment. Achieving the FY2026 target of VND 185,000 billion in net revenue (+19% YoY) requires both market-share gains and real consumption growth, neither of which is assured in this macro environment.

### 4.3 Efficiency

**Corrected from LLM output:** The LLM applied averaging conventions to efficiency denominators, understating Inventory Turnover by 10.1% (5.05× vs. corrected 5.62×) and overstating Days in Inventory by 11.2% (72.3 vs. corrected 65.0 days). The corrected values are more favourable and change the competitive benchmarking conclusion.

**ICT Segment (TGDĐ/DMX):** Asset Turnover of 2.21× exceeds FRT's estimated 1.85–2.0× consolidated figure for FY2024, suggesting MWG maintains a meaningful efficiency advantage. Corrected Inventory Turnover of 5.62× (65 days) places MWG above FRT's consolidated pharmacy-adjusted figure of ~5.5–5.8× — approximately at the top of the peer range rather than below it as the LLM erroneously concluded. This distinction matters: MWG's electronics inventory management is competitive, not lagging.

**Pharmacy Segment (An Khang):** Long Châu (FRT subsidiary) reports per-store inventory turns implying approximately 45–50 days in inventory and gross margins of 20–22%, indicating superior pharmacy channel discipline. The consolidated MWG figure of 65 days blends ICT, grocery, and pharmacy — An Khang's standalone contribution to inventory drag likely exceeds 80 days, suggesting a structurally challenged pharmacy model. Pharmacity per-store economics are not available from HOSE filings; this exclusion is stated explicitly.

**Grocery Segment (BHX):** BHX revenue per store (~VND 28B at ~1,700 stores) lags Winmart+'s established Northern market performance (~VND 33–37B/store) and Co.opmart's Southern density (~VND 45B+/store). The gap is expected for an early-stage Northern expansion, not a structural failure. The critical FY2026 test is whether store maturation accelerates revenue per store toward Winmart+ parity before capital consumption degrades consolidated asset turnover.

**Fuel cost headwind:** RON 95-III at VND 25,540/litre and Diesel at VND 28,760/litre, with 6–10% fuel surcharges applied by logistics operators, create directional upward pressure on SG&A (VND 22,036B / 14.1% of revenue). A 2% fuel-cost pass-through on third-party logistics contracts implies approximately VND 440 billion in incremental SG&A, compressing Operating Profit Margin from 5.29% to ~5.01%.

### 4.4 Leverage

LT Debt Ratio = 0% is a VAS structural artefact (no IFRS 16 lease capitalisation). Do not interpret as low leverage. The correct leverage signals are Total Debt Ratio (60.5%) and TIE (4.81×). At 60.5%, MWG is meaningfully leveraged but within typical bounds for Vietnamese retail (peer range ~55–70%). TIE of 4.81× provides buffer above the 3.0× threshold, though the ALM analysis shows this compresses to 4.00× under a 100 bps shock. Cash Coverage of 6.10× (incorporating D&A add-back of VND 1,891B) provides additional comfort. The primary concern is not the leverage ratio itself but the short-term, floating-rate nature of the entire debt structure: VND 29,931 billion rolls over at market rates, with no fixed-rate instruments or hedges currently in place. Three mitigants are available within MWG's existing banking relationships: (1) interest rate swaps on a portion of the floating debt; (2) pledge-secured credit facilities (*vay cầm cố*) backed by the VND 33,874B deposit book — which contractually fix the borrowing spread above deposit yield regardless of base rate movements; and (3) deposit portfolio laddering to ensure maturities align with debt rollover dates rather than concentrating both in the same quarter.

### 4.5 Liquidity

Current Ratio of 1.52× is adequate (retail minimum 1.2×). Quick Ratio of 0.97× is below 1.0× but typical for inventory-heavy retail. The VND 38,874 billion cash & investments position is the headline liquidity number, but operational liquidity is considerably lower: approximately VND 33,874 billion is in fixed-term deposits (not freely available for operations), and a portion serves as collateral for ST borrowings. This makes the Cash Ratio of 0.77× an overstatement of freely available operational liquidity. The more concerning structural risk is maturity mismatch: if fixed deposit maturities do not align with the VND 29,931 billion ST debt rollover schedule, MWG faces a refinancing gap in a tightening credit cycle. This is not a near-term solvency risk, but it is a structural liquidity vulnerability that the Board should monitor monthly. BHX inventory front-loading (from VND 22,245B to VND 27,267B YoY, +22.6%) adds pressure on NWC and is the primary watch variable for FY2026 liquidity.

### 4.6 Du Pont Summary

Already covered in Section 3. The key takeaway: MWG's ROE decomposition is asset-turnover-led, leverage-supported, and margin-limited. The Debt Burden below 1.0× is structurally unusual and reflects carry-income dependency. BHX expansion will test Asset Turnover in FY2026–2027 before it creates EVA.

---

## 5. LLM Evaluation & Annotations

### What the LLM executed correctly

- **Unit correction (Validation Rule 6):** The LLM correctly applied the ÷1,000 market capitalization conversion, computing M/B = 3.91× and MVA = 96,745.5B. This was the most important validation rule; failure here would have invalidated the entire Performance section.
- **Profitability ratios:** All ROA, ROC, ROE (start-year and average bases) were computed correctly using the specified named ranges.
- **Leverage and liquidity ratios:** TIE, Cash Coverage, Debt Burden, Total Debt Ratio, Current Ratio, Quick Ratio, Cash Ratio — all correct.
- **ALM stress-test:** TIE under 100 bps shock computed as ~4.00× (actual: 7,075 / 1,770 = 3.997×) — arithmetically sound.
- **Du Pont decomposition:** Identity verified: 2.53 × 2.21 × 5.29% × 0.857 = 25.34%; within 0.5% of direct ROE (25.15%) ✓.
- **Strategic recommendation structure:** All four recommendations followed the R[n] format, included ratio evidence, observation, recommendation, and risk consequence.
- **Board-level scope:** Three of four recommendations were appropriately scoped to Board-level capital allocation decisions. The treasury carry-income recommendation (R3) was slightly broad in its vendor payment terms language but remained within Board-level authority.

### Where the LLM diverged

**Systematic error — efficiency ratio denominators (spec gap):**  
All four efficiency errors (Receivables Turnover, Average Collection Period, Inventory Turnover, Days in Inventory) stem from a single cause: the LLM applied standard textbook averaging conventions ((start + end) / 2) to the denominator, rather than the spec's explicitly stated start-of-year requirement (`startYear_receivables`, `startYear_inventory`). The spec did name these named ranges correctly in the formulas table, but did not explicitly flag the distinction from the averaging convention in a separate instruction. This is a spec-level gap, not an LLM-level failure. The LLM was applying reasonable default behavior. The spec retrospective documents the exact language that would prevent this in a revised spec.

**Receivables Turnover:** LLM reported 16.40× (average receivables denominator). Correct: 17.67× (start-year denominator). Magnitude: −7.2%.

**Inventory Turnover:** LLM reported 5.05× (average inventory denominator). Correct: 5.62× (start-year denominator). Magnitude: −10.1%. Most material error — changed the competitive benchmarking conclusion from "MWG lags FRT" to "MWG meets or exceeds FRT."

**Collection Period and Days in Inventory:** Cascading errors from the denominator misapplication. Both corrected in the verification table.

### Errors caused by spec gaps vs. LLM limitations

| Error | Caused by spec gap | Caused by LLM limitation |
|-------|-------------------|--------------------------|
| Averaging vs. start-of-year denominator | ✓ Spec did not add explicit contrast instruction | — |
| All other computations | — | — (LLM executed correctly) |

**Conclusion:** The LLM executed the spec competently. The one systematic category of errors traces to a spec-level gap: the formula table listed `startYear_inventory` but did not include a parallel instruction warning "do not use average — textbook convention differs from this spec's requirement." One sentence in the spec would have prevented all four efficiency errors.

---

## 6. Strategic Recommendations

> All recommendations are sourced from and improve upon the LLM's draft. Minor annotation enhancements are noted in italics.

### R1: Execute a Three-Layer ALM Strategy to Lock the Carry Spread and Cap Debt Repricing Risk

- **Ratio evidence:** TIE = 4.81×; ALM stress-test: 100 bps shock → TIE 4.00×; 150 bps shock → TIE ~3.55×; ST Borrowings = VND 29,931B; Cash & ST investments = VND 38,874B (of which ~VND 33,874B in fixed-term deposits); Financial Income = VND 3,107B (36% of EBT)
- **Observation:** MWG's entire VND 29,931 billion debt is short-term floating rate, while the deposit book is concentrated in single-tranche fixed-term placements. In Q1/2026's tightening cycle, borrowing rates reprice upward immediately upon rollover; if deposit maturities don't roll in tandem, the carry spread compresses from both sides simultaneously — eliminating VND 3,107B in financial income with no warning.
- **Recommendation:** The Group CFO should implement three coordinated actions:

  **Layer 1 — Interest Rate Swap (30% of ST debt, ~VND 9,000B):** Negotiate a 24-month fixed-rate interest rate swap on approximately VND 9,000 billion of floating ST borrowings, locking the rate ceiling on the highest-volume rollover tranches before Q3/2026. This caps TIE downside at ≥4.0× under a 150 bps shock scenario.

  **Layer 2 — Pledge-Secured Lending at Deposit-Linked Spread (40% of ST debt, ~VND 12,000B):** Convert approximately VND 12,000 billion of unsecured ST credit facilities into collateralised loans backed by MWG's fixed-term deposit contracts (*vay cầm cố sổ tiết kiệm* in Vietnamese banking practice). Under this structure, lending banks price the loan at a fixed spread above the pledged deposit rate (typically 0.5–1.0% above), rather than at a floating market reference rate. Regardless of where base lending rates move, the carry spread between deposit yield and borrowing cost is contractually fixed. This protects the financial income contribution without requiring MWG to liquidate the deposits or sacrifice yield.

  **Layer 3 — Deposit Portfolio Laddering (remaining VND 33,874B deposit book):** Replace the current single-tranche deposit concentration with a staggered maturity ladder across three tranches: VND 11,000B at 6-month terms, VND 12,000B at 12-month terms, and VND 10,874B at 18-month terms. As each shorter-dated tranche matures, reinvest at prevailing rates. In a rising rate environment — which Q1/2026 tightening suggests — this ladder maximises average deposit yield over the 18-month horizon while ensuring approximately VND 11,000B in deposits rolls every six months, maintaining liquidity alignment with ST debt rollover schedules. The 18-month tranche locks in current rates on a portion of the book, hedging against a policy reversal to easing.

- **Risk if not acted upon:** A 150 bps rate shock without these structures compresses TIE to ~3.55× while simultaneously eroding the VND 3,107B financial income buffer — a double hit to Net Margin that would reduce FY2026 reported profit by VND 750–900B and trigger a sharp EPS revision immediately ahead of the BHX IPO process.

### R2: Structure BHX Northern Expansion via Standalone Segment Equity Raise, Not Group-Level Borrowing

- **Ratio evidence:** Total Debt Ratio = 60.5%; Asset Turnover = 2.21×; Du Pont sensitivity: 10% asset expansion → AT ~2.01× → ~2 pp ROE compression
- **Observation:** Funding BHX Northern rollout through additional group-level short-term debt would push Total Debt Ratio toward 65%+, compress asset turnover below 2.0×, and cascade into a ~2 percentage point ROE reduction before BHX revenue catches up with the capital deployed.
- **Recommendation:** Authorize the BHX business unit to conduct a standalone minority equity raise (target: VND 5,000–8,000 billion from strategic grocery-sector or PE investors) to fund the FY2026–2027 Northern rollout, ring-fencing expansion capital from the consolidated balance sheet and preserving group Total Debt Ratio below 60%.
- **Risk if not acted upon:** Group leverage exceeds 65% Total Debt Ratio, constraining the ICT segment's seasonal working capital headroom during Q3–Q4 smartphone launch cycles, when TGDĐ/DMX require maximum inventory financing flexibility.

### R3: Board Resolution Requiring Separate Disclosure of Financial Income and a Target Cap on Carry-Trade Dependency

- **Ratio evidence:** Operating Profit Margin = 5.29%; Net Profit Margin = 4.54% (*unusual: net margin below operating margin only explainable by financial income boosting EBIT-equivalent but not captured in ATOI*); Financial Income = VND 3,107B (~36% of EBT)
- **Observation:** The VND 3,107 billion treasury carry income (depositing at ~6–7% while borrowing at ~5%) has structurally propped net income in FY2025. This income is directly rate-sensitive: if the carry spread compresses to zero in Q1/2026 tightening, Net Margin falls from 4.54% to approximately 2.9% — a 36% decline with no forewarning in consolidated income statements.
- **Recommendation:** Issue a Board resolution requiring (a) separate quarterly disclosure of financial income as a distinct line in earnings releases, with explicit earnings quality context; (b) an internal target ceiling of VND 2,000 billion in annual financial income dependency by FY2027 (reducing reliance from 36% to ~22% of EBT); and (c) a mandate to grow retail EBIT by at least VND 1,100 billion annually to offset the planned carry-income drawdown.
- **Risk if not acted upon:** Carry-spread compression eliminates VND 3,107 billion of net income without warning, triggering a sharp earnings-per-share revision that damages MWG's credibility with institutional investors immediately ahead of the BHX IPO process.

### R4: Approve BHX Segment-Level Financial Reporting to Eliminate the Conglomerate Valuation Discount

- **Ratio evidence:** MVA = VND 96,745.5B; M/B = 3.91×; BHX estimated standalone IPO valuation ~VND 80,000B (~61% of market cap at VND 129,921.5B total)
- **Observation:** MWG's blended M/B of 3.91× embeds a structural conglomerate discount: the market cannot independently value BHX (grocery), An Khang (pharmacy), and TGDĐ/DMX (ICT) without segment-level financial statements. Winmart+ (nearest listed grocery peer) trades at ~4.2× book — suggesting BHX's grocery operations may justify a higher standalone multiple than the consolidated entity receives.
- **Recommendation:** Authorize management to file three-segment financial statements (BHX Grocery, ICT Retail, Pharmacy) with HOSE within two quarterly reporting cycles. This is a prerequisite for a credible BHX IPO process: institutional investors will not accept a 10× revenue growth valuation without audited segment-level EBITDA and asset allocation.
- **Risk if not acted upon:** BHX IPO is priced at a discount to fair value, reducing MWG parent proceeds and allowing Winmart+ (already listed and reporting segment data) to capture the "premium grocery platform" institutional positioning before BHX's IPO roadshow begins.

---

## 7. Executive Justification

From my perspective as a commercial banker who has reviewed retail credit facilities across Vietnam's top consumer finance markets: MWG's FY2025 results are genuinely impressive but structurally fragile in two ways that a single-year ratio snapshot can miss.

The first fragility is the earnings quality problem. A company that earns VND 3,107 billion from placing bank deposits — while borrowing from the same banks at slightly lower rates — is executing a treasury carry trade, not a retail business transformation. When I look at the Operating Profit Margin (5.29%) against the Net Margin (4.54%) discrepancy, my first instinct as a credit analyst is to ask: what happens to this company's debt service capacity when rates converge? The ALM stress-test answers that: TIE falls from 4.81× to 4.00× at 100 bps, and the VND 3,107 billion financial income cushion begins to erode. MWG's FY2026 management targets (VND 9,200B net profit, +30% YoY) assume this carry income continues. I am not convinced it does in the Q1/2026 environment without structural hedging.

The second fragility is the BHX expansion bet. Inventory Turnover of 5.62× at the consolidated level looks healthy, but BHX's Northern Vietnam push — where Winmart+ is already entrenched and logistics costs per kilometre are higher than the South — will likely compress consolidated efficiency metrics in FY2026 before store maturation improves them. Asset Turnover at 2.21× will face downward pressure as capital is deployed ahead of revenue.

MWG remains the dominant consumer electronics and grocery platform in Vietnam, with genuine structural advantages in brand, supply chain, and store network. The thesis for holding MWG is BHX: the grocery segment, if it executes the Northern rollout without a balance sheet crisis, will be worth more as a standalone entity than its current embedded valuation. The risk is that the company tries to fund that rollout through the same short-term debt instrument it uses for working capital — a structural mistake that the ratio evidence clearly warns against.

*The four Board-level recommendations follow directly from this analysis and from the ratio evidence. They are actions MWG's Board can take today, without government approval, without policy change, and without betting on macro tailwinds that may not materialize.*

---

## 8. Model Limitations

Three structural constraints bound this analysis. First, VAS reporting excludes IFRS 16 operating lease capitalisation — LT Debt Ratio of 0% is a reporting artefact; actual leverage assessment relies on Total Debt Ratio (60.5%) and TIE (4.81×). Second, the simplified template does not capture every balance sheet sub-line; model total assets (VND 83,946B) differ marginally from audited consolidated totals (VND 84,066B), introducing minor rounding variance but no material analytical distortion. Third, share price input (VND 88,400/share) required a ÷1,000 unit correction to align with VND-billion balance sheet inputs — correctly applied in all Performance calculations (Validation Rule 6 ✓). All benchmark data for FRT, Winmart+, and Co.opmart are derived from publicly available HOSE filings and management disclosures; Pharmacity per-store economics are not available and have been excluded with explicit notation.

---

## 9. References

1. Mobile World Investment Corporation — Audited Consolidated Financial Statements FY2025. https://ir.thegioididong.com
2. Mobile World Investment Corporation — Audited Consolidated Financial Statements FY2024. https://ir.thegioididong.com
3. Mobile World Investment Corporation — Annual Report 2025. https://ir.thegioididong.com
4. CafeF.vn — MWG closing price Dec 31, 2025 = VND 88,400. https://cafef.vn/du-lieu/hose/mwg
5. General Statistics Office of Vietnam (GSO) — CPI March 2026: +4.65% YoY; Q1/2026 average: +3.51%; core inflation: +3.63% YoY.
6. Vietnam Petroleum Administration — Fuel prices May 2026: RON 95-III VND 25,540/l; Diesel VND 28,760/l.
7. Stage 3 workbook: `models/builds/2026-05-21-nguyen-mwg-financials.xlsx` (Ratios tab C43:C76)
8. Stage 4 specification: `docs/specs/2026-05-25-nguyen-mwg-spec.md` (v1.4)
9. LLM raw output: `deliverables/2026-05-26-nguyen-mwg-llm-raw.md`
10. Manual verification: `analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md`
11. Spec retrospective: `deliverables/2026-05-26-nguyen-mwg-spec-retrospective.md`

---

*Final analysis compiled by Nguyen Manh Thai · 2026-05-26 · BUS-629 VEMBA International Corporate Finance · Shidler College of Business, University of Hawaiʻi at Mānoa*
