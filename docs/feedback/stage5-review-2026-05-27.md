# Stage 5 — Instructor Review

**Student:** Nguyen Manh Thai
**Company:** Mobile World Investment Corporation (MWG, HOSE)
**Repo:** https://github.com/manhthaiBG/Corporate-Finance
**Reviewed:** 2026-05-27

---

## Artifact Checklist

| Artifact | Status | Path |
|---|---|---|
| Raw LLM output | ✓ | `deliverables/2026-05-26-nguyen-mwg-llm-raw.md` |
| Manual verification table | ✓ | `analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md` |
| Final analysis | ✓ | `deliverables/2026-05-26-nguyen-mwg-final-analysis.md` |
| Spec retrospective | ✓ | `deliverables/2026-05-26-nguyen-mwg-spec-retrospective.md` |
| Prompt log | ✓ | `deliverables/prompt-log.md` |
| Stage 2 feedback response | — | (not found) |

---

## Observations

### Final Analysis

- **Structure:** The final analysis contains nine well-organized sections: Executive Summary, Ratio Results Summary, Du Pont Decomposition, Category Analysis (with six sub-sections), LLM Evaluation & Annotations, Strategic Recommendations, Executive Justification, Model Limitations, and References. The automated scanner detected 5 of 6 required sections; the sixth (LLM Evaluation) is present and substantive but may have triggered a detection gap because of its combined heading ("LLM Evaluation & Annotations"). Five of six sections is the scanner reading; all six are present in the document. At approximately 4,600 words with 78 ratio citations, this is one of the most data-dense final analyses in the cohort.

- **Analytical depth:** The ratio interpretation goes well beyond restatement. For example, the Profitability section isolates the carry-income effect by stripping VND 3,107B in financial income from Net Margin to arrive at an operating-only net margin of approximately 2.9% — then connects this to the macro headwind (GSO CPI at 4.65% YoY) and questions whether the FY2026 revenue target of VND 185,000B is achievable in that environment. The Efficiency section correctly updates all four corrected ratios with annotations, explains the competitive benchmarking reversal (MWG now meets or exceeds FRT in Inventory Turnover at 5.62x vs. the LLM's erroneous 5.05x), and contextualizes the BHX revenue-per-store gap against Winmart+ and Co.opmart. The Leverage section correctly flags LT Debt = 0% as a VAS artefact and redirects to Total Debt Ratio (60.5%) and TIE (4.81x) — exactly the right treatment.

- **Du Pont Analysis:** The 4-factor decomposition is verified (2.53 x 2.21 x 5.29% x 0.857 = 25.34%, within 0.5% of direct ROE 25.15%). The analysis correctly identifies Asset Turnover as the primary driver and explains the unusual Debt Burden < 1.0x structure caused by the gap between ATOI and net income. The ALM stress-test is well-executed: 100 bps on VND 29,931B yields +299B interest, TIE compresses from 4.81x to 4.00x, and the analysis extends to a 150 bps scenario (TIE ~3.55x) with practical hedging recommendations. The BHX expansion sensitivity (+10% assets, flat revenue, AT drops from 2.21x to 2.01x, ROE down ~2pp) is a strong addition that connects the Du Pont framework to a forward-looking capital allocation decision.

- **LLM Evaluation:** Section 5 is excellent. The student cleanly separates what the LLM got right (unit correction, profitability ratios, leverage, ALM stress-test, Du Pont identity, strategic recommendation structure, Board-level scope) from the single systematic error category (efficiency denominators). The attribution table — "caused by spec gap vs. caused by LLM limitation" — correctly identifies every error as a spec-level gap rather than an LLM failure. This shows genuine understanding of the feedback loop between spec quality and execution quality.

### Manual Verification Table

- **Coverage:** 8 ratios across all six categories, with 22 data rows in the full table (including the discrepancy summary and corrected efficiency table). The selection strategy was deliberate: the student targeted "the formulas most likely to produce LLM discrepancies (averaging conventions, year-end vs. start-of-year denominators, day-count, unit scaling)" — this is strong verification methodology.
- **Quality of discrepancy analysis:** Outstanding. Each of the four errors includes the exact LLM computation (e.g., "(8,826 + 10,183) / 2 = 9,504.5B"), the correct computation, the magnitude of error in both absolute and percentage terms, and the root cause. The Pattern Analysis section identifies the single systematic cause (averaging convention) and connects it to the strategic consequence: "Inventory Turnover understated by 10.1% makes MWG appear less efficient than it is relative to the FRT benchmark — a materially different strategic signal for the inventory management recommendation." The self-correction on item 8 (ALM Stress-Test TIE initially marked as an error, then corrected to a match after re-checking the formula) demonstrates intellectual honesty. The Source Clarification table distinguishing three ratio sources (template auto-computed, LLM stated, manual) is a methodological touch that adds transparency. This verification table is among the strongest in the cohort.

### Spec Retrospective

- **Template compliance:** 4 of 5 expected template signals detected: Section-by-Section Verdict table (with Clear/Vague column and Symptom column), Top Three Gaps with Evidence (each including spec cause, consequence, and exact fix language), Revisions section, and Effectiveness Rating. The Forward Link and Retrospective Process Feedback sections are bonus material that goes beyond the template.
- **Self-assessment quality:** The self-rating of 4/5 is honest and well-justified. The student does not inflate the rating despite the spec's strong overall performance; instead, they ground the deduction in the single anti-averaging instruction gap and its material consequence on benchmarking conclusions. The exact language proposed for the fix (a 60-word paragraph to insert below the Efficiency ratio table) is specific enough to implement directly. Gap 2 (ATOI/financial income mislabeling in the spec) and Gap 3 (Winmart+ benchmark data availability) demonstrate careful re-reading of the spec after seeing how the LLM interpreted each instruction. The suggestion to add a Severity column to the Section 1 table (Minor / Analytical Consequence / Conclusion-Changing) is a constructive addition to the retrospective framework.

### Strategic Recommendations & Executive Voice

- **Recommendations:** The final analysis contains four Board-level recommendations (R1 through R4), each with ratio evidence, observation, recommendation, and risk consequence. The automated scanner reported recs = 0, which is a heading-format detection issue — the recommendations are clearly present and substantial. The student should not be penalized for this scanner artifact.

  - **R1** (ALM three-layer strategy: interest rate swap, pledge-secured lending, deposit laddering) is the most sophisticated recommendation in the cohort. The Vietnamese banking practice detail (*vay cam co so tiet kiem* — collateralized loans backed by deposit contracts) reflects genuine practitioner domain knowledge, not generic textbook advice.
  - **R2** (BHX standalone equity raise vs. group borrowing) correctly connects to the Du Pont sensitivity analysis and preserves group Total Debt Ratio below 60%.
  - **R3** (separate disclosure of financial income + target cap) addresses the earnings quality risk identified in the profitability section with three specific action items.
  - **R4** (segment-level financial reporting for BHX IPO preparation) connects the MVA/M/B analysis to the conglomerate valuation discount and proposes a concrete disclosure timeline.

- **Executive justification:** Section 7 is written from a commercial banking credit-analysis perspective — the student's actual professional lens as a TPBank branch director. The voice is confident, specific, and independent. The opening framing ("A company that earns VND 3,107 billion from placing bank deposits — while borrowing from the same banks at slightly lower rates — is executing a treasury carry trade, not a retail business transformation") demonstrates the kind of independent analytical judgment the course is designed to develop. This section is not a restatement of the LLM output; it is a practitioner's synthesis that could stand in a credit committee presentation.

### Stage 2 Feedback Incorporation

- The Stage 4 instructor review provided two specific minor refinements: (1) add `ticker`, `exchange`, `course`, `reporting_standard`, `currency`, and `fiscal_year` YAML fields to the spec, and (2) add a V7 validation rule for the CF reconciliation gap. The student addressed both in spec v1.4 (commit `dd17ea8`: "Add YAML fields and V7 CF reconciliation rule per instructor Stage 4 feedback"). However, no formal feedback response memo was found in the repo. While the student clearly acted on the feedback (the spec was updated), the absence of a structured response document means the automated scanner could not credit this work fully. A brief response memo acknowledging the two items and confirming the changes would close this gap.

### Repo Polish

- **LICENSE:** MIT License present. Good.
- **`.gitignore`:** Present and functional.
- **GitHub repo description:** Missing (the repository header on GitHub is blank). This is a one-click fix in the GitHub UI.
- **Directory READMEs:** 12 of 13 directories have READMEs — strong structural documentation. The one missing README appears to be in `docs/feedback/`.
- **Canonical filenames:** 8 of 8 expected canonical filenames present. Clean.
- **Commit hygiene:** 29 of 60 commits (48%) have descriptive messages. The descriptive commits are genuinely excellent — for example, `"refactor(stage5): complete structured spec retrospective evaluation"` and `"audit(stage5): create manual ratio verification table for 8 ratios"` follow conventional commit conventions with clear scope and intent. The problem is the other half: a long sequence of `"Create README.md"`, `"Update README.md"`, `"Update BIO.md"` commits from the initial repository setup phase. These appear to be GitHub web-UI commits (one file at a time) rather than batched local commits. The later-stage commits (Stage 4 and Stage 5) are uniformly strong.

### Supplementary Artifact: AI Tooling Reflection Memo

- The student submitted an optional decision memo (`docs/decisions/2026-05-26-nguyen-ai-tooling-experiment.md`) reflecting on the differences between general-purpose LLMs and purpose-built financial analysis tools. The memo draws a parallel between writing an LLM specification and onboarding a junior credit analyst — arguing that "convention drift" is the failure mode in both cases, and that only explicit written SOPs prevent it. The three-tier control framework (AI for speed, junior analyst for verification, senior analyst for judgment) is a practical contribution from the student's banking experience. This is not a graded artifact, but it demonstrates intellectual engagement that goes beyond the assignment requirements.

---

## Kindly-worded suggestions for improvement

- **Strengths first:** This is a strong Stage 5 submission. The verification table is outstanding — 8 ratios, clear error tracing to root cause, self-correction on item 8, and a Pattern Analysis section that connects arithmetic errors to strategic consequences. The final analysis is data-dense (78 ratio citations), well-structured, and analytically mature. The spec retrospective is honest (self-rated 4/5 with clear justification) and includes exact fix language that could be implemented directly. The four strategic recommendations are Board-appropriate, ratio-grounded, and draw on genuine Vietnamese banking domain expertise. The Executive Justification section is the strongest in the cohort — it reads like a credit committee presentation, not a student paper. The optional AI tooling memo is an impressive addition that demonstrates reflective practice.

- **The Stage 4 feedback was incorporated into the spec (v1.4) but not documented in a formal response memo.** The automated scanner could not credit this work because it looks for a response document. A brief response memo — even three to five sentences acknowledging the two items and confirming the spec updates — would have captured the full credit. This is a documentation gap, not a substantive gap.

- **The strategic recommendations are all present and well-structured, but the automated scanner reported recs = 0.** This is because the section headings use long-form titles (e.g., "R1: Execute a Three-Layer ALM Strategy to Lock the Carry Spread and Cap Debt Repricing Risk") rather than a pattern the scanner expected. The content is excellent; the detection issue is on the scanner side, not the student side.

**Concrete improvements for the revision sweep:**

1. **Add a GitHub repo description.** Go to the repo's main page, click the gear icon next to "About," and add a one-line description such as "BUS-629 VEMBA International Corporate Finance — MWG (Mobile World Group) FY2025 financial analysis." This takes 30 seconds and resolves the DESCRIPTION_MISSING flag.

2. **Add a brief Stage 4 feedback response memo.** Create a file at `docs/feedback/stage4-response-2026-05-27.md` (or similar) containing three to five sentences: which feedback items were received, what changes were made (YAML fields added, V7 validation rule added in spec v1.4), and a reference to the commit (`dd17ea8`). This resolves the "no response memo" finding and gives the scanner something to detect.

3. **Consider squashing or annotating the early setup commits.** The 11 consecutive "Create README.md" / "Update README.md" commits from the initial repo setup phase drag the commit hygiene ratio down. For the revision sweep, this is not worth retroactively fixing (rewriting git history is risky), but going forward, batch multiple file changes into single descriptive commits — as you already do in your Stage 4 and Stage 5 work. Your later commits are genuinely exemplary; the early ones just reflect the learning curve with git.
