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
- Fetched `memo-template.md`; confirmed 12-field YAML structure (`fields_required: [title, to, from, date, re, executive_summary, background, method, findings, implications, limitations, references]`).
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

**Objective:** Present five data-grounded clarifying questions to personalize the Selection Rationale and lock the three directional hypotheses before any drafting occurs. This phase enforced the "analyst as editor, LLM as drafter" workflow recommended in the rubric.

**Model Output — Five Questions Posed:**

The model identified and surfaced five analytical decision points from the raw data:

1. **Career Background & Selection Rationale** — connecting personal professional context to the analytical framing.
2. **Admin Expense Anomaly** — tripling of admin costs (VND 1,168B → VND 4,596B) identified as the most anomalous three-year data pattern, requiring hypothesis direction (normalization vs. structural step-up).
3. **BHX Sustainability vs. Re-expansion Risk** — two competing hypothesis directions offered (Option A: margin compression from Northern expansion; Option B: proven scalability sustains profitability).
4. **The Debt-vs.-Deposits Paradox** — VND 36,639B in financial placements exceeding total ST borrowings of VND 29,931B; model offered two interpretations (smart carry trade vs. refinancing risk signal).
5. **Analytical Angle & Ratio Emphasis** — four focus options offered: (a) profitability sustainability, (b) liquidity/leverage risk, (c) operational efficiency, (d) earnings quality.

---

## Phase 3 — Response Refinement & Hypothesis Lock

**Objective:** Receive analyst inputs across all five dimensions and lock the three hypotheses in strict "I expect X because Y" directional format.

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
- You must strictly map the content above into the exact 12-section structure
  and maintain the structural integrity of the YAML frontmatter from the
  template ('memo-template.md').
- Set 'purpose' to "Stage 2 Company Selection Memo" and 'audience' to
  "Adam Stauffer". Set the date to "2026-05-19".
- Ensure the final word count is tightly constrained between 400 and 600
  words (excluding frontmatter header metadata), utilizing a sharp, concise,
  and decision-oriented senior banker tone.
- Provide the output in a single, raw Markdown code block so I can copy it
  directly to my repository.
```

**Model Actions:**
- Mapped all six Stage 2 required sections (Company Overview, Selection Rationale, Data Availability & Sources, Preliminary Observations, Ratio Categories Preview, Data Collection Plan) onto the template's 12-field YAML structure.
- Generated `2026-05-19-nguyen-mwg-selection.md` and saved to workspace folder.
- Body word count: ~570 words (within 400–600 constraint).

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

**Objective:** After reviewing the generated draft, the analyst identified that H2 and H3 used corporate events and qualitative signals as the subject of the "I expect X" clause rather than named financial ratios with explicit directional outcomes. A targeted surgical edit was commissioned.

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
- Identified exact structural defects in H2 and H3:
  - H2: Subject was "the pending IPO" (a corporate event), not a ratio.
  - H3: Direction was "will be critical signals" (observational), not a measurable directional outcome.
- Applied targeted `Edit` tool call on `2026-05-19-nguyen-mwg-selection.md` — no other sections modified.

**Before / After Comparison:**

| | Before | After |
|---|---|---|
| **H2 subject** | "the pending **Bách Hóa Xanh** segment IPO" | "MWG's **market-to-book ratio**" |
| **H2 direction** | "to sharply re-rate… metrics" | "to **expand materially above** its FY2025 book-implied level" |
| **H2 anchor** | qualitative valuation narrative | FY2025 book equity of VND 33,176 billion (extracted from audited BS) |
| **H3 subject** | "BHX's asset turnover and inventory turnover… critical efficiency signals" | "MWG's consolidated **inventory turnover ratio**" |
| **H3 direction** | "to be the critical… signals" (no direction) | "to **decline from its FY2025 level of 5.05x**" |
| **H3 baseline** | none cited | 5.05x (sourced directly from MWG Annual Report 2025, p.25) |

**Final Locked Hypotheses:**

```text
Hypothesis 1: I expect gross margin to compress in FY2026 versus FY2025
because the ~8% VND depreciation (USD/VND ~26,500) directly inflates import
costs on smartphones and consumer electronics that cannot be fully passed
through to consumers already absorbing 5.5% CPI pressure, squeezing the
19.9% gross margin MWG achieved in FY2025.

Hypothesis 2: I expect MWG's market-to-book ratio to expand materially above
its FY2025 book-implied level because a standalone Bách Hóa Xanh (BHX)
valuation of ~VND 80,000 billion implies the grocery chain alone approximates
a massive portion of the parent group's current market capitalization — a
structural discount embedded in FY2025 book equity of VND 33,176 billion that
the forward expansion will compel market multiples to correct.

Hypothesis 3: I expect MWG's consolidated inventory turnover ratio to decline
from its FY2025 level of 5.05x because Bách Hóa Xanh's aggressive Northern
Vietnam store rollout will front-load inventory accumulation well ahead of
optimal throughput, revealing whether the supply-chain infrastructure
underpinning management's VND 1,200 billion BHX profit target (+70% YoY)
is operationally sound.
```

---

## Phase 5 — Prompt Log Generation

### Prompt 5.1 — Prompt Log Commission

```text
Act as a senior systems analyst. Based on our entire end-to-end engineering
session for Mobile World Investment Corporation (MWG), please generate the
final, comprehensive 'prompt-log.md' file as mandated by the Stage 2 course
guidelines. Apply the following strict execution constraints:

1. Environment Tracking: Explicitly log the tool used as "Claude Sonnet 4.6"
   to accurately reflect the May 2026 workspace environment.
2. Structure: Organize the log into clear, logical phases tracking our
   dialogue: Initial Discovery, Response Refinement (incorporating the
   commercial banking risk lens, the 185,000B VND revenue / 9,200B VND net
   profit targets, and the Iran war macro stress tests), and the Final
   Generation Command.
3. Code Blocks: Wrap all documented prompts inside nested text code blocks
   so they are perfectly readable.
4. Output Format: Provide the final output inside a single, raw Markdown code
   block so I can copy-paste it directly into my 'deliverables/prompt-log.md'
   file.

Please generate the complete prompt log now.
```

**Model Actions:** Generated and saved this file to `deliverables/prompt-log.md` in the workspace folder.

---

## Prompt Engineering Observations

The following patterns proved most effective in this session and are worth carrying forward into Stage 3 and Stage 4 workflows:

**1. Pre-draft analysis mandate.** Separating the analysis phase from the drafting phase — explicitly instructing the model *not* to draft until it had ingested all source documents and posed clarifying questions — produced materially better hypothesis quality than a single-shot generation prompt would have.

**2. Constraint stacking.** Specifying multiple simultaneous constraints (word count, YAML structure, tone register, audience, output format) in a single generation command yielded a compliant first draft without iterative correction on structural issues.

**3. Surgical edit prompts.** Rather than re-generating the entire memo to fix H2 and H3, a targeted single-section edit prompt preserved all other carefully constructed content while isolating the structural defect (subject vs. event; directional outcome vs. observational label). This is the correct workflow for post-draft refinement.

**4. Data anchoring.** Hypothesis quality increased significantly when prompts included explicit real data points (VND 33,176B book equity for H2; 5.05x inventory turnover for H3) sourced from the model's own OCR extraction of the audited filings, rather than relying on management narrative from the annual report alone.

**5. Role framing.** Framing the analyst role as "commercial credit and ASEAN banking" rather than "equity investor" drove a distinctive analytical angle — prioritizing earnings quality, leverage structure, and debt-servicing capacity — that differentiated the memo from a generic retail sector analysis.

---

*Log compiled by Claude Sonnet 4.6 | Session: 2026-05-19 | BUS-629 VEMBA International Corporate Finance*
