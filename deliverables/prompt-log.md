# Prompt Log — BUS-629 Stage 2: Company Selection Memo
## Mobile World Investment Corporation (MWG, HOSE)

**Analyst:** Nguyen Manh Thai  
**Tool:** Claude Sonnet 4.6 (Cowork Desktop, May 2026 workspace)  
**Session Date:** 2026-05-19  
**Deliverable:** `docs/decisions/2026-05-19-nguyen-mwg-selection.md`  
**Log Path:** `deliverables/prompt-log.md`

---

## Overview

This log documents every significant prompt submitted during the end-to-end engineering session producing the BUS-629 Stage 2 Company Selection Memo for Mobile World Investment Corporation (MWG, HOSE). The session is organized into five sequential phases: Initial Discovery & Document Ingestion, Analytical Framing & Clarifying Questions, Response Refinement & Hypothesis Lock, Final Generation Command, and Post-Draft Precision Edit. All prompts are reproduced verbatim or near-verbatim inside nested code blocks. Model outputs are summarized rather than reproduced in full, except where specific data extracts are analytically material.

---

## Phase 1 — Initial Discovery & Document Ingestion

**Objective:** Ingest the professor's Stage 2 grading rubric, the raw memo template, and all three MWG source documents (FY2024 audited financials, FY2025 audited financials, Annual Report 2025). Establish the factual data foundation before any drafting.

**Tool:** Claude Sonnet 4.6  
**Inputs:** Four uploaded files (`MWG_2024.pdf`, `MWG_2025.pdf`, `MWG_Baocaothuongnien_2025.pdf`, `memo-template.md`) plus one live URL fetch.

### Prompt 1.1 — Rubric Fetch & Pre-Draft Analysis Mandate

```text
Act as a senior financial analyst preparing a Stage 2 Company Selection Memo
for a Managing Director (my professor, Adam Stauffer).

In the Project Knowledge, I have already provided the following essential
documents:
1. Audited Consolidated Financial Statements of Mobile World Investment
   Corporation (MWG, HOSE) for FY2024.
2. Audited Consolidated Financial Statements of MWG for FY2025.
3. MWG's Annual Report 2025.
4. The raw 'memo-template.md'.

Please read the professor's official Stage 2 instructions from this raw URL
to understand the strict grading rubrics and expectations:
https://raw.githubusercontent.com/adamwstauffer/shidler/main/courses/
BUS-629-VEMBA-International-Corporate-Finance/stage2-company-selection-memo.md

DO NOT draft the memo yet. First, thoroughly analyze the uploaded financial
statements and annual report of MWG across the FY2023, FY2024, and FY2025
periods. Once your analysis is done, ask me 3 to 5 specific, clarifying
questions to personalize the draft. Your questions must cover:

1. My career goals, current industry background, or personal interests (to
   build a strong, customized "Selection Rationale" for choosing MWG).
2. Your initial data observations from the uploaded MWG financial documents
   (specifically looking at their massive restructuring trends, store closure
   impacts, and Bach Hoa Xanh's financial turnaround/profitability path
   across 2024-2025), so we can collaboratively formulate 2-3 strict,
   falsifiable hypotheses in the required "I expect X because Y" directional
   format.

Please list your clarifying questions now based on the real MWG data you
see in the files.
```

**Model Actions:**
- Fetched rubric from the raw GitHub URL; confirmed Stage 2 structure (six required sections, four rubric criteria at 25% each, 400–600 word body limit, collaborator penalty).
- Fetched `memo-template.md`; confirmed 12-field YAML structure.
- Extracted and compiled financial data from the uploaded PDFs.

**Key Data Extracted by Model (verbatim from filings):**

| Metric | FY2023 | FY2024 | FY2025 |
|---|---:|---:|---:|
| Net Revenue (VND B) | 118,280 | 134,341 | 155,928 |
| Gross Margin % | 19.0% | 20.5% | 19.9% |
| Selling Expenses (VND B) | (20,917) | (19,850) | (19,331) |
| Admin Expenses (VND B) | (1,168) | (3,566) | (4,596) |
| Net Profit (VND B) | 168 | 3,733 | 7,073 |
| Net Margin % | 0.14% | 2.8% | 4.5% |
| ST Borrowings (VND B) | 19,129 | 27,300 | 29,931 |
| LT Debt (VND B) | 5,986 | 0 | 0 |
| ST Financial Investments (VND B) | 18,937 | 29,324 | 33,874 |
| ROE | — | 13.3% | 21.3% |
| Inventory Turnover | — | 4.85x | 5.05x |
| BHX Revenue (VND B, 2025 AR) | — | — | ~46,900 |
| Operating CFO (VND B) | 3,436 | 8,517 | 6,096 |

---

## Phase 2 — Analytical Framing & Clarifying Questions

**Objective:** Present five data-grounded clarifying questions to personalize the Selection Rationale and lock the three directional hypotheses before any drafting occurs.

**Model Output — Five Questions Posed:**

1. **Career Background & Selection Rationale** — connecting personal professional context to the analytical framing.
2. **Admin Expense Anomaly** — tripling of admin costs (VND 1,168B → VND 4,596B), requiring hypothesis direction (normalization vs. structural step-up).
3. **BHX Sustainability vs. Re-expansion Risk** — Option A: margin compression from Northern expansion; Option B: proven scalability sustains profitability.
4. **The Debt-vs.-Deposits Paradox** — VND 36,639B in placements exceeding ST borrowings; smart carry trade vs. refinancing risk signal.
5. **Analytical Angle & Ratio Emphasis** — four focus options: (a) profitability, (b) liquidity/leverage, (c) efficiency, (d) earnings quality.

---

## Phase 3 — Response Refinement & Hypothesis Lock

### Prompt 3.1 — Full Response Submission (Five Answers)

```text
Here are my finalized, data-driven responses to your 5 clarifying questions.
Please use these inputs to anchor the analytical framework of the memo and
draft the deliverable:

Ans 1 (Background & Rationale):
I operate within the Banking and Financial Services industry. From a commercial
credit, capital structure, and liquidity risk lens, MWG represents the ultimate
real-world corporate stress-test in the current May 2026 macroeconomic
environment. For FY2026, management has set highly ambitious operational
targets: Consolidated Net Revenue of 185,000 billion VND (+19% YoY growth)
and Consolidated Net Profit of 9,200 billion VND. While the broader market
focuses heavily on this target and its FY2025 earnings recovery (+89% YoY),
my analytical interest is driven by how a retail giant completely reliant on
short-term bank debt (29,931 tỷ VND current borrowings) can realistically
achieve this 19% topline expansion while defending its debt-servicing capacity
and liquidity safety margins. Specifically, I am evaluating MWG's resilience
under compounding pressures: navigating an 8% free-market currency
depreciation (USD/VND at ~26,500), soaring freight and logistics COGS
triggered by the Iran war and the Strait of Hormuz closure, and rising
effective lending spreads. This directly aligns with my professional focus
on credit risk management and ASEAN corporate banking strategy.

Ans 2 (Admin Expense Anomaly):
The administrative expense surge (tripling from 1,168 tỷ to 4,596 tỷ VND)
is driven primarily by a combination of options (a) and (b). It reflects
one-off restructuring charges, asset impairments, and lease termination
penalties from radically closing over 200 inefficient TGDĐ/DMX/An Khang
stores, alongside significant management bonus accruals tied to the sharp
operational turnaround. Therefore, please orient Hypothesis 1 toward cost
normalization: I expect admin expenses to normalize downward in subsequent
quarters as these temporary, one-off restructuring costs phase out.

Ans 3 (BHX Sustainability vs. Re-expansion Risk):
I select Option A (Risk). Entering the lower-density Northern Vietnam market
for the first time after a decade of Southern dominance introduces severe
capital and logistical stress. Please structure Hypothesis 2 around this
expansion risk: I expect BHX's gross and operating margins to temporarily
compress in FY2026 because Northern expansion injects high upfront regional
logistics, supply-chain infrastructure, and distribution center costs before
achieving optimal store density and local economies of scale.

Ans 4 (The Debt-vs.-Deposits Paradox):
I view this paradox as a highly strategic "Smart Carry Trade" and a sign of
strong financial discipline rather than distress. MWG leverages its dominant
market position to extract ultra-low short-term working capital rates from
commercial banks, maintaining defensive tactical liquidity while placing its
immense idle cash (36,639 tỷ VND) in higher-yielding deposits to earn a safe
interest spread. Hypothesis 3 should reflect this: I expect this active
treasury strategy to continue bridging retail net income via robust financial
income, demonstrating sophisticated liquidity optimization and capital
preservation that mitigates short-term refinancing risks.

Ans 4.5 (Specific Hypotheses Refinement):
Please utilize these three directional and falsifiable hypotheses exactly in
the "Findings" section:

- Hypothesis 1: I expect gross margin to compress in FY2026 versus FY2025
  because the ~8% VND depreciation (USD/VND rising to ~26,500) directly
  inflates import costs on smartphones and consumer electronics, which cannot
  be fully passed through to consumers already facing a 5.5% CPI inflation
  stress test.

- Hypothesis 2: I expect the upcoming Bách Hóa Xanh IPO to sharply re-rate
  MWG's market-to-book and MVA metrics because a segment valuation of ~80,000
  tỷ VND implies the grocery division alone is worth a massive portion of the
  current market capitalization of the parent group, a valuation gap that
  FY2025 historical book values fail to capture but market ratios will make
  visible.

- Hypothesis 3: I expect Bách Hóa Xanh's asset turnover and inventory
  turnover to be the critical efficiency signals in FY2026 because validating
  the aggressive 1,200 tỷ VND net profit target (+70% YoY) requires
  structural improvements in supply-chain efficiency across its
  capital-intensive logistics network rather than temporary cost-cutting.

Ans 5 (Analytical Angle & Ratio Emphasis):
I want to heavily emphasize (d) Earnings Quality paired with (c) Operational
Efficiency. The ratio model must aggressively dissect how much of MWG's
recovery is driven by structural retail optimization versus treasury carry
income (with financial income accounting for nearly 40% of pre-tax profit).
Please prioritize Profitability Ratios (isolated EBIT margins), Activity
Ratios (Inventory Turnover and Cash Conversion Cycle), and Market-Performance
Ratios (MVA/EVA calculated at a country-risk adjusted 13.5% WACC) to expose
the intrinsic valuation gap ahead of the landmark Bách Hóa Xanh IPO.

***
GENERATION COMMAND:
Please generate the final Stage 2 Company Selection Memo in English now.
- Strictly map content into the 12-section YAML template structure.
- Set 'purpose' to "Stage 2 Company Selection Memo", 'audience' to
  "Adam Stauffer", date to "2026-05-19".
- Word count 400–600 words (excluding frontmatter), senior banker tone.
- Output in a single raw Markdown code block.
```

**Model Actions:**
- Mapped all six Stage 2 required sections onto the 12-field YAML template structure.
- Generated `2026-05-19-nguyen-mwg-selection.md`; body word count ~570 words ✓.

**Key Analytical Decisions Made in This Phase:**

| Decision Point | Input Provided | Model Mapping |
|---|---|---|
| Selection Rationale anchor | Commercial credit & ASEAN banking lens | Executive Summary + Background |
| Macro stress context | Iran war / Hormuz freight, 8% VND depreciation, rising spreads | Background + H1 |
| Admin expense direction | Options (a) + (b): restructuring charges + bonus accruals | Informed H1 framing |
| BHX hypothesis direction | Option A: Northern expansion margin risk | Informed H3 framing |
| Debt-deposits paradox | Smart carry trade / financial discipline | Implications + H3 |
| Ratio emphasis | Earnings quality + operational efficiency | Implications section |
| WACC assumption | 13.5% country-risk-adjusted | Implications section |

---

## Phase 4 — Post-Draft Precision Edit: Hypothesis Ratio Anchoring

### Prompt 4.1 — Hypothesis Ratio-Anchoring Revision

```text
I am working on my Stage 2 company selection memo for BUS-629. I need to
refine the hypotheses section of my draft to ensure they strictly map to
quantifiable financial ratios as required by the grading criteria.

Please rewrite only the 'Findings' section of the draft. Keep Hypothesis 1
intact, but revise Hypothesis 2 and Hypothesis 3 so that specific financial
ratios (such as Market-to-Book, MVA, and Inventory Turnover) serve as the
direct subjects in the 'I expect X because Y' format. Maintain the original
word count boundary and the senior analyst professional tone.
```

**Model Actions:**
- H2: Subject changed from "the pending IPO" (event) → "MWG's market-to-book ratio"; direction anchored to FY2025 book equity of VND 33,176B.
- H3: Subject changed from observational → "MWG's consolidated inventory turnover ratio to decline from 5.05x"; baseline sourced from Annual Report 2025 p.25.

---

## Phase 5 — Prompt Log Generation

### Prompt 5.1 — Prompt Log Commission

```text
Act as a senior systems analyst. Based on our entire end-to-end engineering
session for Mobile World Investment Corporation (MWG), please generate the
final, comprehensive 'prompt-log.md' file as mandated by the Stage 2 course
guidelines. Apply the following strict execution constraints:

1. Environment Tracking: Explicitly log the tool used as "Claude Sonnet 4.6".
2. Structure: Organize into clear phases tracking our dialogue.
3. Code Blocks: Wrap all documented prompts inside nested text code blocks.
4. Output Format: Single raw Markdown code block for copy-paste to
   'deliverables/prompt-log.md'.

Please generate the complete prompt log now.
```

**Model Actions:** Generated and saved to `deliverables/prompt-log.md`.

---

## Prompt Engineering Observations (Stage 2)

**1. Pre-draft analysis mandate.** Separating analysis from drafting produced materially better hypothesis quality than a single-shot generation prompt.

**2. Constraint stacking.** Specifying word count, YAML structure, tone, audience, and output format in one command yielded a compliant first draft without structural correction.

**3. Surgical edit prompts.** A targeted single-section edit preserved all other content while isolating the structural defect (event vs. ratio subject).

**4. Data anchoring.** Hypothesis quality increased when prompts cited explicit data points from the model's own extraction (VND 33,176B book equity; 5.05x inventory turnover).

**5. Role framing.** Framing as "commercial credit and ASEAN banking" drove a distinctive angle — earnings quality, leverage, debt-servicing capacity.

---

*Log compiled by Claude Sonnet 4.6 | Session: 2026-05-19 | BUS-629 VEMBA International Corporate Finance*

---

# Stage 4 Prompt Log — Technical Specification
## Mobile World Investment Corporation (MWG, HOSE)

**Analyst:** Nguyen Manh Thai
**Tool:** Claude Sonnet 4.6 (Cowork Desktop, May 2026 workspace)
**Session Date:** 2026-05-25
**Deliverable:** `docs/specs/2026-05-25-nguyen-mwg-spec.md` (version 1.3)
**Input artifacts:** Stage 3 workbook (`2026-05-21-nguyen-mwg-financials.xlsx`), Stage 4 brief (GitHub), spec template (GitHub)

---

## HIL Iteration Log

The spec went through three analyst-driven iterations before reaching submission-ready v1.3. Full gap descriptions, root causes, Stage 5 consequences, and change lists are in the spec's **HIL Review Note** section (`docs/specs/2026-05-25-nguyen-mwg-spec.md` → end of document).

| Iter | Versions | Gap Category | Key Change | Analyst Action |
|---|---|---|---|---|
| 1 | v1.0 → v1.1 | Formula / unit error | Market cap ÷1,000; MVA/M/B recalculated; Validation Rule 6 added | Cross-checked spec outputs against Stage 3 workbook Ratios tab |
| 2 | v1.1 → v1.2 | Analytical completeness | FRT/Long Châu benchmarks; ALM stress-test 100 bps → TIE 4.39×; Board-level + national-policy guardrail | Sourced GSO CPI + fuel prices externally; identified scope drift to national policy |
| 3 | v1.2 → v1.3 | Structure & benchmark coverage | Named Range Map extracted to standalone §3; Pharmacity added; Winmart+/Co.opmart added; YAML artefacts removed | Mapped spec sections against rubric Part A items 1-to-1 |

---

## Overview

Phase 1 covers rubric ingestion and data extraction. Phase 2 covers the v1.0 draft and analyst review decisions. Phase 3 (Iteration 1) corrects the market cap unit error. Phase 4 (Iteration 2) adds benchmarks, ALM stress-test, and scope guardrails. Phase 5 (Iteration 3) extracts the Named Range Map, completes competitor benchmarks, and cleans the YAML frontmatter.

---

## Phase 1 — Rubric & Template Ingestion

**Objective:** Read the Stage 4 brief and spec template; extract all data from the Stage 3 workbook before drafting.

### Prompt 1.1 — Stage 4 Brief + Template Fetch

```text
Tôi đã hoàn thành stage 3 trong folder, giúp tôi hoàn thiện stage 4 theo
hướng dẫn lưu ý bạn tạo file mới chứ không ghi đè file cũ.
https://github.com/adamwstauffer/shidler/blob/main/courses/
BUS-629-VEMBA-International-Corporate-Finance/stage4-technical-specification.md
```

**Model actions:**
- Fetched Stage 4 brief. Confirmed: deliverable is `.md` at `docs/specs/`, plus prompt log entry, plus at least one HIL iteration. Rubric is 4×25%: Data & Structure, Ratios & Validation, Analysis Spec, Spec Craft + Prompt Log.
- Fetched spec template. Confirmed: YAML frontmatter required; 10 sections.
- Read all six sheets of `2026-05-21-nguyen-mwg-financials.xlsx` via openpyxl to extract Ratios!C6:C76, Balance Sheet, Income Statement, Cash Flow.

**Key data extracted:**

| Source | Key Values |
|---|---|
| Balance Sheet | Total Assets: 83,946B (FY2025), 70,437B (FY2024); Total Equity: 33,176B / 28,121B |
| Income Statement | Net Sales: 155,928B; COGS: 124,926B; EBIT: 7,075B; Net Income: 7,073B |
| Cash Flow | `CASH_operating`: 6,096B; `CASH_investments`: −6,661B; `CASH_financing`: 668B |
| Ratios inputs | Share price: 88,400 VND; Shares: 1,469.7M; WACC: 13.5%; Tax: 20% |
| Ratios derived | ATOI: 8,249.8B; Market cap (raw): 129,921,480; startYear equity: 28,121B |
| Ratios outputs | ROE: 25.15%; Asset Turnover: 2.21×; TIE: 4.81×; Current Ratio: 1.52× |

---

## Phase 2 — Initial Spec Draft (v1.0) & Analyst Review

**Objective:** Draft all 10 spec sections in a single pass, then review against the Stage 3 workbook before any revision.

### Draft Generation — v1.0 First Pass

Model drafted v1.0 per the spec-template structure using extracted data. All Part A and Part B sections populated in the first pass.

**v1.0 draft state:**
- 25 ratios in named-range notation with expected outputs.
- Market cap listed as raw template value 129,921,480 VND B — direct transcription without unit verification.
- §7 benchmarks used generic HOSE retail medians (electronics + grocery + pharmacy + apparel aggregated).
- Macro risks referenced qualitatively; no GSO CPI or fuel price figures sourced yet.

**Analyst review of v1.0 — three judgment decisions before any revision:**

1. *Unit verification:* Market-to-Book showed 3,916× and MVA ~129.9 million VND billions. Analyst cross-checked against known market cap (~130,000B VND at 88,400 × 1,469.7M shares) and confirmed a unit scale error, not a data entry error. → Triggered Iteration 1.
2. *Benchmark scope decision:* Generic HOSE medians were judged inadequate for MWG's three-segment structure (ICT + grocery + pharmacy). Segment-specific Vietnamese competitors required — to be addressed in a separate iteration, not mixed with the unit fix.
3. *Macro data gap decision:* Analyst resolved to source GSO CPI and Vietnam Petroleum Administration fuel prices externally before Iteration 2, rather than ask the model to generate plausible numbers.

---

## Phase 3 — HIL Iteration 1: Unit-Mismatch Correction (v1.0 → v1.1)

**Gap:** `market_capitalization = 129,921,480 VND B` in v1.0. M/B = 3,916×, MVA ≈ 129.9 million VND billions — nonsensical for 33,176B book equity.

**Root cause:** `share_price (raw VND/share) × shares_outstanding (millions)` = VND millions, not VND billions. Template designed for USD companies; for MWG, ÷1,000 conversion required.

**Stage 5 consequence if not corrected:** Entire Performance category analytically unusable (MVA ≈ 129M VND billions, M/B ≈ 3,916×).

### Prompt 3.1 — v1.1 Revision Command

```text
Please upgrade the spec to version 1.1. Targeted corrections only:

1. Data Inputs: market_capitalization → 129,921.5 VND B + unit footnote.
2. Derived Inputs: formula → 'share_price × shares_outstanding / 1,000'.
3. Performance ratios: MVA → 96,745.5 VND B; M/B → 3.91×.
4. Validation: add Rule 6 — unit correction required before MVA/M/B.
5. Add footnote ¹ to Performance ratio table entries.
6. Append HIL Review Note. Do not modify any other section.
```

**What changed v1.0 → v1.1:**

| Location | v1.0 | v1.1 |
|---|---|---|
| Market cap value | 129,921,480 VND B | 129,921.5 VND B + footnote ¹ |
| Market cap formula | `share_price × shares_outstanding` | `share_price × shares_outstanding / 1,000` |
| MVA | ~129.9M VND B | 96,745.5 VND B |
| Market-to-Book | 3,916× | 3.91× |
| Validation rules | 5 | 6 (Rule 6 added) |

**Analyst verification:** M/B = 3.91×, MVA = 96,745.5B ✓

---

## Phase 4 — HIL Iteration 2: Macro, ALM & Benchmarking (v1.1 → v1.2)

**Gap 1 — Flawed benchmarking:** Generic HOSE medians aggregated four unrelated retail categories. MWG's three segments each require segment-specific domestic competitors.

**Gap 2 — Missing ALM analysis:** v1.1 noted MWG's 29,931B ST floating debt and 38,874B deposits but did not instruct maturity mismatch analysis. In early 2026 tightening, borrowing rates reprice immediately; fixed-term deposits remain locked. Stage 5 would have treated the carry strategy as unambiguously positive.

**Gap 3 — Absent quantitative macro data:** GSO CPI (4.65% YoY March 2026) and fuel prices (RON 95-III 25,540 VND/l; Diesel 28,760 VND/l) were sourced by the analyst after v1.1 generation. LLM could not retrieve these independently.

**Gap 4 — Recommendation scope drift:** Vietnam's 15–16% logistics cost-to-GDP lacked a guardrail. Without explicit instruction, Stage 5 produced "optimise Vietnam's national green/digital logistics corridor" — a government-level policy prescription, not a Board action.

**Stage 5 consequence if not corrected:** (a) Irrelevant benchmarks; (b) ALM risk presented as pure positive; (c) qualitative macro assertions; (d) national policy recommendations unimplementable by MWG management.

### Prompt 4.1 — v1.2 Upgrade Command

```text
Please upgrade the spec to version 1.2. Do not modify Part A other than
version number and YAML notes.

1. §7 Efficiency: replace HOSE medians with FRT + Nguyen Kim (ICT);
   Long Châu (pharmacy). Add GSO CPI (March 2026: 4.65% YoY, Q1 avg:
   3.51%, core: 3.63%) and fuel prices (RON 95-III 25,540 VND/l;
   Diesel 28,760 VND/l; 6-10% surcharges). Add guardrail: logistics
   cost-to-GDP is context only; executor must translate to MWG-specific
   Board action (e.g., logistics contract renegotiation, distribution
   centre investment) — not national policy.

2. §8 Du Pont: add Step 5 — mandatory ALM stress-test. 100 bps on
   29,931B ≈ +299B interest; TIE 4.81× → ~4.39×; carry spread
   compression analysis on 3,107B financial income.

3. §9 Recommendations: add Board-Level Constraint with two prohibited
   categories: (a) micro-management; (b) national policy. Rewrite
   coverage areas: ALM hedging, BHX capital structure, earnings quality,
   segment disclosure.

4. References: add GSO and Vietnam Petroleum Administration sources.

5. HIL Review Note: append Iteration 2 documentation.
```

**What changed v1.1 → v1.2:**

| Location | v1.1 | v1.2 |
|---|---|---|
| §7 benchmarks | Generic HOSE medians | FRT / Nguyen Kim (ICT); Long Châu (pharmacy) |
| §7 macro data | Qualitative only | GSO CPI 4.65%; fuel RON 95-III 25,540 VND/l |
| §7 logistics context | No guardrail | Context only; not policy recommendation |
| §8 Du Pont | 4 steps | Step 5: ALM 100 bps → TIE 4.39× |
| §9 Recommendations | No scope constraint | Micro-management + national policy both prohibited |
| References | 7 | 9 |

**Analyst verification:** Benchmarks named. ALM quantified. Macro data anchored to primary sources. National policy guardrail present. ✓

---

## Phase 5 — HIL Iteration 3: Named Range Map, Benchmarks & Frontmatter (v1.2 → v1.3)

**Gap 1 — Named Range Conventions not a standalone section:** Prefix conventions table was embedded in §2 Model Architecture. Rubric maps "Named Range Conventions" as an independent Part A item. Without a dedicated section, rubric mappers could not locate it 1-to-1.

**Gap 2 — Incomplete competitor benchmarks:** Pharmacy benchmarked only against Long Châu, omitting Pharmacity. BHX grocery had no domestic operational competitor benchmarks — only an IPO valuation reference.

**Gap 3 — YAML frontmatter artefacts:** `fields_required` and `courses` were template metadata from the LLM's template parsing — not content fields appropriate in a submitted spec.

**Stage 5 consequence if not corrected:** (a) Named Range Map not findable as dedicated section; (b) An Khang benchmarked without Pharmacity; BHX analysis without Winmart+/Co.opmart peer comparison; (c) frontmatter signals LLM artefacts to grader.

### Prompt 5.1 — v1.3 Upgrade Command

```text
Please upgrade the spec to version 1.3. Three targeted changes only:

1. Extract the Named Range Prefix Conventions table from §2 into a new
   standalone Part A section "Named Range Map". Expand with a sub-table
   for the four analyst assumption inputs (share_price, shares_outstanding,
   cost_capital, tax_rate). Renumber downstream sections +1.

2. §8 Analysis Requirements (Efficiency + Performance):
   - Pharmacy: add Pharmacity alongside Long Châu; instruct to state
     exclusion explicitly if per-store data unavailable.
   - Grocery (BHX): add Winmart+ and Co.opmart as mandatory operational
     benchmarks in both Performance (M/B context) and Efficiency
     (store-count economics) sub-sections.

3. YAML: remove fields_required and courses. Retain only: template,
   purpose, audience, title, author, date, version, company,
   naming_convention, notes. Update version to "1.3"; update notes
   to summarise all three iterations.

Append Iteration 3 to HIL Review Note. Do not modify any other content.
```

**What changed v1.2 → v1.3:**

| Location | v1.2 | v1.3 |
|---|---|---|
| Part A structure | Named Range table in §2 | Standalone §3 "Named Range Map" + analyst inputs sub-table; sections renumbered |
| §8 pharmacy benchmark | Long Châu only | Long Châu + Pharmacity; explicit exclusion instruction |
| §8 grocery benchmark (Performance + Efficiency) | IPO valuation reference only | Winmart+ and Co.opmart added as mandatory operational benchmarks |
| YAML frontmatter | `fields_required` + `courses` present | Removed; clean 9-field frontmatter |

**Analyst verification:** Named Range Map present as standalone section. Pharmacity and Winmart+/Co.opmart in §8. YAML contains only substantive fields. ✓

---

## Prompt Engineering Observations (Stage 4)

**1. Data-first drafting.** Extracting all workbook values before writing a single spec line prevented right-structure / wrong-numbers failure.

**2. Cross-check outputs against the workbook.** Comparing spec expected outputs against Ratios!C43:C76 caught the unit mismatch in Iteration 1. Standard first step of every HIL review.

**3. Scope HIL iterations separately.** Iteration 1 = formula/unit pass (verifiable). Iteration 2 = analytical completeness pass (required external data). Iteration 3 = structural/rubric-alignment pass. Mixing these would have obscured which gap type drove each correction.

**4. Named-range precision over cell references.** `currentYear_after_tax_operating_income` instead of "Ratios!C22" — robust to template restructuring and unambiguous for Stage 5.

**5. VAS structural zeros require explicit annotation.** LT Debt = 0% must be labelled a VAS artefact to prevent Stage 5 misinterpreting it as low-leverage signal.

**6. Analyst-sourced external data must be manually injected.** LLM cannot fetch GSO CPI or Vietnam Petroleum Administration fuel prices. Sourced after v1.1; injected in v1.2 prompt.

**7. Board-level scope constraint prevents output dilution.** Without the dual exclusion (micro-management + national policy), Stage 5 produced a green logistics corridor recommendation — government-level policy, not a Board action.

**8. Rubric-mapping review catches structural gaps.** Reviewing spec sections against rubric Part A items 1-to-1 (Iteration 3) revealed Named Range Conventions was not findable as a standalone item — invisible from content review alone.

---

*Stage 4 log compiled by Claude Sonnet 4.6 | Session: 2026-05-25 | BUS-629 VEMBA International Corporate Finance*

---

## Stage 5 Prompt Log — LLM Analysis & Evaluation
### Mobile World Investment Corporation (MWG, HOSE)

**Analyst:** Nguyen Manh Thai  
**Tool:** Claude Sonnet 4.6 (Cowork Desktop, May 2026 workspace)  
**Session Date:** 2026-05-26  
**Deliverables:**
- `deliverables/2026-05-26-nguyen-mwg-llm-raw.md`
- `analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md`
- `deliverables/2026-05-26-nguyen-mwg-final-analysis.md`
- `deliverables/2026-05-26-nguyen-mwg-spec-retrospective.md`

**Input artifacts:**
- Stage 4 spec: `docs/specs/2026-05-25-nguyen-mwg-spec.md` (v1.4)
- Stage 3 workbook: `models/builds/2026-05-21-nguyen-mwg-financials.xlsx`
- Instructor PR feedback: `docs/feedback/stage4-review-2026-05-26.md`
- Stage 5 brief: https://github.com/adamwstauffer/shidler/blob/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage5-llm-analysis-evaluation.md
- Spec retrospective template: https://github.com/adamwstauffer/shidler/blob/main/docs/templates/spec-retrospective-template.md

---

### Overview

Stage 5 was executed in five sequential phases following the professor's recommended production order: (1) raw LLM execution from spec only, (2) manual verification table, (3) evaluated final analysis, (4) spec retrospective, (5) prompt log update. All sessions used Claude Sonnet 4.6 (Cowork Desktop). The spec was fed as sole input for the raw LLM output session; no additional context was provided. The verification, final analysis, and retrospective sessions were analyst-directed with Claude as execution partner.

---

### Phase 1 — Spec v1.4 Revision (Incorporating Instructor PR Feedback)

**Objective:** Incorporate the professor's Stage 4 PR feedback into a v1.4 revision before Stage 5 execution.

**Input artifacts:** `docs/feedback/stage4-review-2026-05-26.md`, `docs/specs/2026-05-25-nguyen-mwg-spec.md` (v1.3)

**Prompt 1.1 — Instructor Feedback Review and v1.4 Revision**

```
Read the instructor's Stage 4 feedback at docs/feedback/stage4-review-2026-05-26.md.
Then read my spec at docs/specs/2026-05-25-nguyen-mwg-spec.md (v1.3).
For each suggestion in the feedback, propose a specific edit (file + section + before/after)
that would address it. Then implement all accepted edits and save as v1.4.
Update version number, notes field, and append HIL Iteration 4 documentation.
```

**Model actions:**

Read instructor feedback PR file. Identified key suggestions: (a) add six YAML fields (ticker, exchange, course, reporting_standard, currency, fiscal_year); (b) add CF reconciliation validation rule (V7) to cover the 4,550B reclassification gap between CFO+CFI+CFF and balance sheet cash change. Implemented targeted v1.4 changes; spec renumbered but analytically unchanged from v1.3.

**Changes v1.3 → v1.4:**

| Section | Change |
|---------|--------|
| YAML frontmatter | Added 6 fields: ticker, exchange, course, reporting_standard, currency, fiscal_year |
| Part C Validation Rules | Added V7: CF reconciliation gap (CFO+CFI+CFF = +103B vs. BS cash change +4,653B; note ~4,550B reclassification artefact) |
| YAML notes field | Updated to summarize four iterations |
| HIL Review Note | Appended Iteration 4 documentation |

---

### Phase 2 — Raw LLM Execution (Spec as Sole Input)

**Objective:** Feed the v1.4 spec as the only input to Claude Sonnet 4.6 and save the complete, unedited response as the raw LLM output.

**Prompt 2.1 — Raw Execution Command**

```
[Full text of docs/specs/2026-05-25-nguyen-mwg-spec.md (v1.4) pasted verbatim]

Please execute this specification and produce the complete ratio analysis as described.
No additional context beyond this specification document.
```

**Model actions:**

Executed all six ratio categories from named-range inputs. Applied ÷1,000 unit correction for market capitalization. Produced all 28 ratios across six categories. Computed Du Pont decomposition and ALM stress-test. Generated four strategic recommendations in R[n] format. Produced all six required output sections in order.

**Analyst observation before saving:**

Four discrepancies noted in the Efficiency section: Inventory Turnover (5.05× vs. expected 5.62×), Receivables Turnover (16.40× vs. 17.67×), and cascading days-in-inventory and collection period values. These were not corrected in the raw output — saved unedited as specified.

**Output saved:** `deliverables/2026-05-26-nguyen-mwg-llm-raw.md`

---

### Phase 3 — Manual Ratio Verification

**Objective:** Recompute ≥5 ratios by hand from Stage 3 financial data. Compare to LLM's stated values. Document discrepancies with explanation.

**Prompt 3.1 — Verification Table Commission**

```
I need to build the Stage 5 manual verification table.
Using only the financial data from 2026-05-21-nguyen-mwg-financials.xlsx
(Balance Sheet, Income Statement, Cash Flow, and Ratios tabs), please:

1. Recompute 8 ratios by hand using the exact named-range formulas from the spec.
   Cover at least one ratio from each of the following: Profitability, Efficiency,
   Leverage, Liquidity, Performance, Du Pont.
2. Compare each to the LLM's stated value in the raw output.
3. For each discrepancy, explain the root cause in one sentence.
4. Create the verification file at analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md.
   Use the table format from the Stage 5 brief.
```

**Model actions:**

Recomputed 8 ratios from Stage 3 workbook data. Identified four discrepancies in the Efficiency category (all traceable to LLM's averaging convention). Confirmed correct computations for ROE, M/B, TIE, and ALM stress-test TIE. Documented pattern analysis identifying a systematic denominator error vs. a random computation error.

**Key finding documented:** LLM applied standard textbook averaging convention ((start + end) / 2) to efficiency denominators. The spec listed `startYear_inventory` and `startYear_receivables` as the correct named ranges but did not explicitly warn against averaging. This is a spec gap, not an LLM error.

**Output saved:** `analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md`

---

### Phase 4 — Final Analysis (Corrected, Annotated, Executive Voice)

**Objective:** Produce the evaluated, corrected, and annotated final analysis — incorporating verification table corrections, LLM evaluation, and executive voice.

**Prompt 4.1 — Final Analysis Generation**

```
Using the raw LLM output (2026-05-26-nguyen-mwg-llm-raw.md) and the
verification table (analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md),
generate the final evaluated analysis at deliverables/2026-05-26-nguyen-mwg-final-analysis.md.

Requirements:
1. Apply all four efficiency ratio corrections from the verification table.
   Mark corrected values with ✏️ in the summary table.
2. Include all six required sections in order (Executive Summary, Ratio Results,
   Du Pont, Category Analysis, Strategic Recommendations, Model Limitations, References).
3. Add Section 5: LLM Evaluation — what the LLM got right, where it diverged,
   and whether each divergence was a spec gap or LLM limitation.
4. Add Section 6: Executive Justification in my voice (commercial banker,
   ASEAN credit risk lens, 17 years banking experience).
5. Target 1,500–1,800 words body. Senior analyst memo tone. No marketing language.
```

**Model actions:**

Applied four efficiency corrections. Annotated the Efficiency category analysis with explicit before/after notes. Wrote LLM evaluation table (spec gap vs. LLM limitation attribution). Wrote Executive Justification from commercial banking perspective, focusing on the carry-trade earnings quality risk and the BHX expansion capital structure concern. Enhanced R1 with three-layer ALM strategy: (1) interest rate swap ~VND 9,000B on 30% of ST debt before Q3/2026; (2) pledge-secured lending (vay cầm cố sổ tiết kiệm) ~VND 12,000B at fixed spread (0.5–1.0%) above deposit rate; (3) deposit ladder VND 33,874B across 6M/12M/18M tranches.

**Output saved:** `deliverables/2026-05-26-nguyen-mwg-final-analysis.md`

---

### Phase 5 — Spec Retrospective

**Objective:** Complete the structured spec retrospective using the professor's template.

**Prompt 5.1 — Spec Retrospective Commission**

```
Using the spec retrospective template at:
https://github.com/adamwstauffer/shidler/blob/main/docs/templates/spec-retrospective-template.md

Complete the retrospective for my Stage 4 spec (docs/specs/2026-05-25-nguyen-mwg-spec.md v1.4)
based on what the LLM output (deliverables/2026-05-26-nguyen-mwg-llm-raw.md)
revealed about the spec's strengths and gaps.

Requirements:
1. Complete Section 1 with specific symptoms from the LLM raw output for every Vague row.
   Do not write "seems vague" — trace each verdict to a specific number or claim in the output.
2. Identify the top 3 gaps with the exact spec language that caused each gap and
   the exact replacement language that would prevent it.
3. Rate effectiveness 1–5 with anchored justification.
4. Write 100–150 word process feedback with one structural template suggestion.
5. Save to deliverables/2026-05-26-nguyen-mwg-spec-retrospective.md.
```

**Model actions:**

Completed all six retrospective sections. Rated spec effectiveness 4/5 with specific evidence (LLM executed unit correction and Du Pont correctly; single section needs sharpening). Identified three gaps with exact fix language. Section 6 feedback proposed adding a "Severity" column to the verdict table (Minor / Analytical Consequence / Conclusion-Changing) to help distinguish remediation priorities.

**Output saved:** `deliverables/2026-05-26-nguyen-mwg-spec-retrospective.md`

---

### Phase 6 — Repo Polish Pass

**Objective:** Update all per-directory READMEs, root README project status, and ensure file naming compliance.

**Prompt 6.1 — Repo Polish Commission**

```
Compare the current repo structure against the Stage 5 target hierarchy from:
https://github.com/adamwstauffer/shidler/blob/main/courses/BUS-629-VEMBA-International-Corporate-Finance/stage5-llm-analysis-evaluation.md

Identify:
1. Per-directory READMEs that need updating
2. Root README project status section to add
3. Any file naming issues

Draft updated README content for each directory. Update the root README.md
with a Project Status section listing all five stages with commit references.
```

**Model actions:** Audited repo structure against Stage 5 target hierarchy. Updated root README.md with "What You'll Find Here" narrative, Project Status table (Stages 1–5 with commit references), Stage 5 deliverables summary table, and Key Finding section. Confirmed per-directory README for `analysis/validation/`. Verified naming convention compliance for all five Stage 5 deliverables. Added `docs/decisions/2026-05-26-nguyen-ai-tooling-experiment.md` — optional portfolio artifact: banking practitioner reflection on general LLM vs. purpose-built finance tooling and the parallel to managing a junior credit analyst.

---

### Prompt Engineering Observations (Stage 5)

**1. Production order discipline pays off.** Running the raw LLM output before the verification table forced the analyst to confront the efficiency discrepancy with arithmetic evidence rather than impression. The verification table motivated the LLM evaluation section, which motivated the retrospective gap analysis. Each file built on the previous one.

**2. Spec-as-sole-input is a real test.** Feeding only the spec to the LLM (no additional context, no "also consider...") revealed the anti-averaging gap that would have gone unnoticed in a standard draft-and-revise workflow. The systematic nature of the error (four ratios, one root cause) makes it easier to trace than random errors would be.

**3. The verification table changes conclusions, not just numbers.** The corrected Inventory Turnover (5.62× vs. LLM's 5.05×) shifted the competitive benchmarking conclusion from "MWG lags FRT" to "MWG meets/exceeds FRT." That is not a rounding error; it is a strategy-level finding. This confirms the spec's rationale for requiring the verification table.

**4. Retrospective Section 6 (process feedback) is the most generative.** Being required to propose a structural change to the template — not just say "it was useful" — forced a specific observation: the verdict table needs a Severity column to distinguish conclusion-changing gaps from minor ones. This distinction would have helped prioritize which of the three gaps to address first in a v1.5 revision.

**5. Repo polish is not administrative.** Updating the per-directory READMEs required reading every file in the repo and confirming what actually exists vs. what the Stage 5 target hierarchy expects. Three READMEs needed substantive content updates, not just placeholder text.

**6. Banking domain expertise elevates the spec output.** The R1 ALM recommendation moved from "consider an interest rate swap" (textbook-level) to a three-layer structured strategy (swap + pledge-secured lending + deposit ladder) because the analyst's institutional knowledge identified instruments that are operationally feasible at a Vietnamese commercial bank. The LLM executed the spec correctly; the practitioner insight is what made the spec worth executing.

---

*Stage 5 log compiled by Claude Sonnet 4.6 | Session: 2026-05-26 | BUS-629 VEMBA International Corporate Finance*
