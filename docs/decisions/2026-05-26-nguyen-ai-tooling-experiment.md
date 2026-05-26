---
template: decision-memo
purpose: Reflection on AI-assisted financial analysis — general LLM vs. purpose-built finance tooling, the limits of surface-level ratio benchmarking, and the parallel to managing junior credit analysts
audience: Adam Stauffer (BUS-629 instructor); professional network
author: Nguyen Manh Thai
date: 2026-05-26
stage: Stage 5 (optional portfolio artifact)
---

# AI Tooling Experiment — Reflection Memo

**Author:** Nguyen Manh Thai, Branch Director, TPBank Hanoi  
**Date:** 2026-05-26  
**Context:** BUS-629 Stage 5 — LLM Analysis & Evaluation, Mobile World Investment Corporation (MWG)

---

## 1. What I Tried

I used Claude Sonnet 4.6 (general-purpose LLM) as the primary AI executor across all five stages of the MWG financial analysis. I also reviewed the architecture of purpose-built tools — `financial-analysis:audit-xls` and `financial-analysis:3-statement-model` — designed specifically for structured financial document workflows. This memo compares the two approaches and draws out the practitioner implications.

---

## 2. The Gap — and the Deeper Problem with "Surface-Level Ratios"

**The technical error:** Claude Sonnet 4.6 defaulted to textbook averaging convention for inventory denominators, producing an Inventory Turnover of 5.05× instead of the spec-required 5.62×. That single error reversed the competitive benchmarking conclusion: MWG appeared to lag FPT Retail when the corrected data shows it meets or exceeds it.

A purpose-built `audit-xls` tool would not make this error. It would parse the named-range map, enforce the workbook's denominator convention, and flag formula inconsistencies before the analyst sees the output. The gap is not intelligence — it is domain-specific guardrails.

**The more fundamental problem:** The technical error is recoverable. The deeper risk of LLM-driven analysis — and of raw quantitative models in general — is the tendency to treat all companies within an industry as structurally equivalent. In this project, MWG and FPT Retail (FRT) share an industry classification, but they are operationally different entities:

- **Business model and customer positioning:** Thế Giới Di Động and Điện Máy Xanh (MWG) operate a self-managed warehouse and logistics network with a store-experience focus. Long Châu (FRT) is a pharmaceutical retail chain — with entirely different inventory turnover characteristics, product shelf-life constraints, and customer segments. Comparing their raw efficiency ratios without this context produces a category error, not an analysis.

- **Leadership risk appetite and working capital structure:** The working capital management strategy at MWG — supplier credit terms, inventory buffer policy, cash placement decisions — reflects the direct operating philosophy of its founder and controlling shareholder. That governance layer shapes the financial structure in ways no standardized formula captures. An LLM treating MWG and FRT as interchangeable benchmarks based on SIC code alone will produce a plausible-looking but fundamentally misleading conclusion.

**The lesson:** If the analyst only reads surface-level ratios, the AI will flatten every company into the same mold. Real-world financial analysis requires deconstructing metrics to understand the operating model behind the numbers — not just computing them.

---

## 3. The Management Parallel: Writing a Spec Is Writing an SOP

Designing a Stage 4 specification for an LLM is structurally identical to onboarding a junior credit analyst — and the failure modes are the same.

**Convention drift** is the most common error in both cases. A junior analyst fresh from university will apply the formula they were taught (average inventory, 360-day DSO) rather than the convention the institution actually uses. An LLM will do the same. No amount of general financial training prevents this — only an explicit written operating procedure does.

The spec is that SOP. But the spec must go further than locking in formulas. It must force the analyst — human or AI — to engage with the non-financial variables: the sales model, the ownership structure, the management team's risk tolerance. A spec that only constrains arithmetic will produce arithmetic-level output.

The critical difference between managing the LLM and managing the analyst: I can correct a junior analyst verbally in a one-on-one conversation, and the lesson sticks because they build institutional memory. The LLM has no memory between sessions. Every correction must be written into the spec itself, or it disappears. This means the spec must be more complete, more explicit, and more assumption-free than any verbal briefing I would give a person.

---

## 4. A Three-Tier Control Framework for Credit Approval

For a credit committee presentation on a Vietnamese listed company, the practical workflow at branch level would operate as follows:

**Tier 1 — AI (speed optimization)**  
The LLM runs the first-pass draft: rapid data scan, surface anomaly detection, ratio computation from a well-engineered spec. Output is fast but requires verification.

**Tier 2 — Junior Analyst (verification and deconstruction)**  
The analyst runs the verification table to catch arithmetic errors, then performs the qualitative deconstruction the LLM cannot do: bóc tách the sales model, assess the management team's operating track record, identify structural differences that make peer benchmarks misleading.

**Tier 3 — Senior Banker (judgment and accountability)**  
The credit director or committee approves based on the full picture: management credibility, strategic positioning within the macroeconomic context, and ultimate risk ownership. This role does not change with AI adoption — it becomes more important, because the speed of Tier 1 creates pressure to skip Tier 2.

---

## Conclusion

Technology leverage accelerates computation. But the ability to deconstruct metrics based on a company's actual operating identity — and the judgment to take responsibility for the final credit recommendation — remains the decisive variable in the quality of a credit file. The leverage is in the spec and in the judgment, not in the arithmetic.

---

*Memo compiled by Nguyen Manh Thai · 2026-05-26 · BUS-629 VEMBA International Corporate Finance*  
*Shidler College of Business · University of Hawaiʻi at Mānoa · VEMBA Cohort 33*  
*Word count: 892 words (body, excluding YAML frontmatter)*
