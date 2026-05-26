# Manh Thai Nguyen

**Branch Director | Banking & Financial Services Leader | MBA Candidate**

📧 manhthai.bg@gmail.com | 📍 Hanoi, Vietnam

---

Over the past 17 years, I have built my career across Vietnam's leading commercial banks, including MB Bank, Techcombank, and TPBank. Starting in frontline relationship management and progressing into branch leadership, I have developed hands-on experience across Retail Banking, SME Banking, and Corporate & Investment Banking (CIB).

Currently, I serve as Branch Director at TPBank Hanoi, where I oversee branch operations and business development across multiple customer segments in one of Vietnam's most competitive banking markets. My professional focus includes commercial banking strategy, portfolio growth, client relationship management, and team leadership.

Before joining TPBank in 2022, I led Corporate Banking Centers at Techcombank across the Ba Dinh and regional business segments, strengthening my expertise in corporate client development and market expansion.

I hold a Bachelor's degree in Investment Economics from the National Economics University and am currently completing my MBA at the Shidler College of Business, University of Hawaiʻi at Mānoa (VEMBA Cohort 33).

I believe great banking is built on trust first, transactions second. My long-term goal is to contribute to the innovation and sustainable growth of Vietnam's banking industry through strategic leadership and continuous learning.

---

## What You'll Find Here

This repository holds all deliverables produced in **BUS-629 International Corporate Finance** at the Shidler College of Business, University of Hawaiʻi at Mānoa. The project is a five-stage AI-assisted financial analysis of **Mobile World Investment Corporation (MWG, HOSE)** — Vietnam's largest consumer electronics and grocery retailer — executed using a Specification-Driven Design (SDD) methodology.

The project demonstrates the complete analyst workflow: from company selection through financial modelling, technical specification, LLM execution, and executive-level evaluation. Each stage builds on the prior one; the Stage 4 specification is precise enough that any competent executor (human or LLM) can reproduce the Stage 5 analysis from it as sole input.

A manager, reviewer, or peer who navigates this repository will find: a professional-grade FY2025 ratio analysis of a major Vietnamese retailer, a documented AI prompt engineering workflow, and a structured self-evaluation of where the LLM-assisted process produced accurate output and where it required human correction.

---

## Repository Structure

| Folder | Contents |
|--------|----------|
| `docs/` | Decision memos (Stage 2), technical specifications (Stage 4), feedback files |
| `models/` | Financial model templates (Stage 1) and completed builds (Stage 3) |
| `data/` | Source financial data and provenance notes |
| `analysis/` | Validation reports and self-audit work (Stage 5 verification table) |
| `deliverables/` | Final, presentation-ready outputs — prompt log, raw LLM output, final analysis, spec retrospective |

---

## Project Status

| Stage | Title | Status | Key Deliverable | Commit |
|-------|-------|--------|-----------------|--------|
| Stage 1 | Financial Model Template | ✅ Complete | `models/templates/performance-ratios-template.xlsx` | Initial commit |
| Stage 2 | Company Selection Memo | ✅ Complete | `docs/decisions/2026-05-19-nguyen-mwg-selection.md` | `1dff355` |
| Stage 3 | Financial Model Build | ✅ Complete | `models/builds/2026-05-21-nguyen-mwg-financials.xlsx` | see models/ |
| Stage 4 | Technical Specification | ✅ Complete (v1.4) | `docs/specs/2026-05-25-nguyen-mwg-spec.md` | `dd17ea8` |
| Stage 5 | LLM Analysis & Evaluation | ✅ Complete | `deliverables/2026-05-26-nguyen-mwg-final-analysis.md` | see deliverables/ |

**Company analyzed:** Mobile World Investment Corporation · Ticker: MWG · Exchange: HOSE  
**Fiscal period covered:** FY2025 (audited consolidated, VAS)  
**Analytical methodology:** 28 performance ratios across 6 categories; Du Pont decomposition; ALM stress-test; 4 Board-level strategic recommendations

---

## Stage 5 Deliverables (Final Stage)

All Stage 5 files are in `deliverables/` and `analysis/validation/`:

| File | Purpose |
|------|---------|
| `deliverables/2026-05-26-nguyen-mwg-llm-raw.md` | Unedited LLM output from feeding Stage 4 spec as sole input |
| `analysis/validation/2026-05-26-nguyen-mwg-stage5-verification.md` | Manual recomputation of 8 ratios; 4 discrepancies identified and explained |
| `deliverables/2026-05-26-nguyen-mwg-final-analysis.md` | Corrected, annotated, executive-voice final analysis |
| `deliverables/2026-05-26-nguyen-mwg-spec-retrospective.md` | Structured spec self-evaluation using professor's template |
| `deliverables/prompt-log.md` | Full AI session log — Stages 2, 4, and 5 |
| `docs/decisions/2026-05-26-nguyen-ai-tooling-experiment.md` | Optional: banking practitioner reflection on general LLM vs. purpose-built finance tooling |

---

## Key Finding (Stage 5 Summary)

MWG's FY2025 ROE of 25.15% substantially outperforms the HOSE consumer discretionary median (12–18%), but Du Pont decomposition reveals the driver is asset turnover (2.21×) and leverage (2.53×), not margin expansion. Approximately 36% of pre-tax profit derives from treasury carry income (deposit placement strategy) rather than retail operations — creating a rate-sensitive earnings quality risk in Q1/2026's tightening credit cycle. Four Board-level recommendations address interest rate hedging, BHX expansion capital structure, financial income transparency, and segment-level disclosure ahead of the BHX IPO.

---

## License

[MIT License](LICENSE)

---

*BUS-629 VEMBA International Corporate Finance · Shidler College of Business · University of Hawaiʻi at Mānoa · Cohort 33*
