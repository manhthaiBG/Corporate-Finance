# Stage 4 — Instructor Review

**Student:** Nguyen Manh Thai
**Company:** Mobile World Investment Corporation (MWG, HOSE)
**Spec:** `docs/specs/2026-05-25-nguyen-mwg-spec.md`
**Reviewed:** 2026-05-26

---

## Observations

### Part A — Model Specification

- **Scope & Objective (Section 1):** Well-defined — identifies VAS, VND billions, MWG/HOSE, FY2025/FY2024, with specific VAS–IFRS differences documented (no IFRS 16 equivalent, LT debt structurally zero). Share price unit exception (raw VND per share, not VND billions) explicitly flagged. Analytical objective and intended audience clearly stated.
- **Model Architecture (Section 2):** Six-tab workbook documented with color coding (Green headers, Yellow manual inputs, Light gray formulas, White labels), data flow diagram, and input/calculation/output separation rule. Clean tabular format.
- **Named Range Map (Section 3):** Standalone section extracted in v1.3 — a deliberate rubric-alignment decision documented in the HIL trail. Prefix table with `BAL_*_curr/_prior`, `INC_*`, `CASH_*`, `startYear_*`, `currentYear_*`, `avg_*`, `RATIO_*` conventions. Analyst assumption inputs sub-table with unit alert on `share_price`. This is the cleanest Named Range Map in the cohort.
- **Data Inputs (Section 4):** Comprehensive — BS (20+ named ranges both years), IS (12 items), CF (3 items with reconciliation check CFO+CFI+CFF = +103B). Model note explaining slight divergence from audited totals (83,946 vs 84,066 / 70,437 vs 70,416). All values sourced from MWG Audited Consolidated Financial Statements FY2025.
- **Derived Inputs (Section 5):** 20 intermediate calculations with explicit named-range formulas and computed values. Market cap unit-mismatch correction documented with ÷1,000 factor and footnote.

### Part A — Ratios & Validation

- **Ratio Definitions (Section 6):** 29 ratios across all six categories — Performance (3: MVA, M/B, EVA), Profitability start-year (3: ROA, ROC, ROE), Profitability average (3: ROA avg, ROC avg, ROE avg), Efficiency (7), Leverage (7 with VAS structural note on LT Debt = 0%), Liquidity (4), Du Pont (2: 4-factor). All in named-range notation with expected output values and units. The VAS note on LT Debt Ratio is well-placed — "Do not interpret as low leverage. Primary leverage signals: Total Debt Ratio (60.5%) and TIE (4.81×)."
- **Validation Rules (Section 7):** 6 rules with computed expected values: BS balance (83,946 = 50,770 + 33,176 ✓), income allocation (7,073 = 1,478 + 5,595 ✓), ATOI derivation (8,249.8 ✓), Du Pont ROA (11.69% ≈ 11.71% ✓), Du Pont ROE (25.34% ≈ 25.15% ✓), market cap unit correction (V6 — the most impactful validation rule in the cohort). Each rule has a tolerance specification.

### Part B — Analysis Specification

- **Analysis Requirements (Section 8):** Exceptionally detailed per-category guidance with segment-specific Vietnamese competitor benchmarks:
  - **ICT:** FPT Retail (FRT) and Nguyen Kim — the only listed domestic pure-play comparables for consumer electronics retail
  - **Pharmacy (An Khang):** Long Châu (FRT subsidiary) and Pharmacity — with explicit instruction to state exclusion if Pharmacity per-store data is unavailable
  - **Grocery (BHX):** Winmart+ (Masan Consumer Holdings) and Co.opmart (Saigon Co.op) — framing the BHX valuation discount in operational peer terms, not IPO speculation
  - Q1/2026 macro headwinds quantified: GSO CPI 4.65% YoY, fuel RON 95-III 25,540 VND/l, 6–10% logistics surcharges. Supply-side cost shock translated into SG&A impact (22,036B / 14.1%) and OPM erosion risk (5.29%).
  - Cross-category connections: EVA sustainability ↔ operating profit margin ↔ ALM interest costs. Financial income isolation (3,107B treasury carry is not recurring core retail income).
- **Du Pont Decomposition (Section 9):** Full 4-factor chain (2.53 × 2.21 × 5.29% × 0.857 = 25.34%). Primary driver identified: Asset Turnover (2.21×) for a retail group on thin margins. BHX expansion sensitivity quantified: +10% assets with flat revenue → AT 2.21→2.01×, ROE −2pp. **Mandatory ALM stress-test** (Step 5): 100 bps on 29,931B ST borrowings → +299B interest → TIE 4.81→4.39×; carry spread compression on 3,107B financial income; refinancing risk assessment.
- **Strategic Recommendations (Section 10):** 4 required, Board-level scope with dual prohibition (micro-management + national policy). The dual prohibition is a constraint engineering achievement — documenting that Stage 5 without this guardrail produced "optimise Vietnam's national green/digital logistics corridor." Four coverage areas: ALM hedging, BHX capital structure, earnings quality/treasury carry dependency, BHX segment disclosure/valuation gap.
- **Output Format (Section 11):** 7-section structure with word targets, senior analyst tone, ratio results summary table format with ✅/⚠️/❌ signals.

### Prompt Log & HIL Iteration

- **Prompt log:** Comprehensive documentation covering both Stage 2 and Stage 4. Stage 2: 5-phase session with verbatim prompts (Vietnamese + English), model action tracking, key data extraction tables, and analytical decision log. Stage 4: 5-phase session documenting rubric ingestion, v1.0 draft, and three targeted iteration commands (v1.1, v1.2, v1.3) with before/after tables. 8 prompt engineering observations at the end — substantive reflections, not boilerplate.
- **HIL iteration:** Three rounds, each with clear gap identification, root cause, "Stage 5 consequence if not corrected," and specific change list:
  - **v1.0→v1.1:** Market cap unit-mismatch catch — M/B 3,916×→3.91×, MVA ~129.9M VND B → 96,745.5B. Root cause: template designed for USD; VND/share × M shares = VND millions, not billions. **Most impactful quantitative correction in the cohort.**
  - **v1.1→v1.2:** Segment-specific benchmarks replace generic HOSE medians; ALM stress-test added; Board-level scope guardrail added; GSO CPI + fuel prices manually sourced and injected.
  - **v1.2→v1.3:** Named Range Map extracted to standalone section; Pharmacity + Winmart+/Co.opmart benchmarks added; YAML template artefacts removed.

---

## Kindly-worded suggestions for improvement

- **This is one of the strongest Stage 4 submissions in the cohort, alongside Dang Hai's SKF spec.** The three-iteration HIL trail is exemplary: each iteration has a clear gap identification, root-cause analysis, "Stage 5 consequence if not corrected" statement, and specific change list. The market cap unit-mismatch catch in Iteration 1 is the most impactful quantitative correction in the cohort — without it, MVA and M/B would have been off by a factor of 1,000.
- **The segment-specific Vietnamese competitor benchmarking** demonstrates genuine domain expertise with MWG's three-segment structure. Generic HOSE retail medians would have been analytically misleading — separating ICT (FRT/Nguyen Kim), pharmacy (Long Châu/Pharmacity), and grocery (Winmart+/Co.opmart) gives Stage 5 defensible comparison targets.
- **The ALM stress-test** (100 bps → TIE 4.81→4.39×; carry spread compression on 3,107B financial income) converts the Du Pont decomposition from a descriptive exercise into a risk assessment tool. The Board-level scope constraint prevents the kind of generic national-policy recommendations that erode memo credibility.
- **The prompt engineering observations are substantive.** Observation 6 ("Analyst-sourced external data must be manually injected — LLM cannot fetch GSO CPI or Vietnam Petroleum Administration fuel prices") is a genuine methodological insight about the boundary between LLM capability and analyst judgment.

**Minor refinements:**

1. **YAML frontmatter:** While you correctly cleaned template artefacts in v1.3, the YAML is missing `ticker`, `exchange`, `course`, `reporting_standard`, `currency`, and `fiscal_year` fields. These are documented in the spec body (§1) but their absence from the YAML means Stage 5 tooling can't extract them programmatically. A 2-minute addition.
2. **CF reconciliation gap:** CFO + CFI + CFF = +103B, but BS cash changed by 38,874 − 34,221 = +4,653B. The ~4,550B difference likely reflects reclassifications between cash and short-term financial investments. Consider adding a V7 validation rule noting this gap so Stage 5 doesn't flag it.

**Looking ahead to Stage 5:** Your spec is detailed enough that the LLM output should be high-quality. The key verification targets: (1) confirm the ÷1,000 market cap correction propagates through MVA and M/B; (2) verify the ALM stress-test arithmetic (100 bps × 29,931B = 299B → TIE 4.39×); (3) check that the Board-level scope constraint prevents micro-management and national-policy recommendations; (4) verify segment-specific benchmarks are used, not generic HOSE medians.
