# JSP-001025 — Quality-Control Report

**Author:** Kames xyz  
**Date:** 1 November 2026  
**Status:** MATHEMATICAL PROOF-OUTLINE REVISION COMMITTED — PDF/DOCX CONTENT REVIEW PENDING

## Scope

The repository contains the final-named PDF and DOCX files, and their GitHub file objects are retrievable:

- `JSP-001025_Exposition_OneWayFunctions_FINAL-1.pdf`
- `JSP-001025_Exposition_OneWayFunctions_FINAL-1.docx`

This report distinguishes file availability from document-content verification. The binary files have not been rendered page-by-page in this review, so their visual layout, pagination, embedded fonts, metadata, and exact text match against the Markdown are not certified.

## Changes made to the Markdown source

1. Added the general threshold-indexed definition of randomized time-bounded Kolmogorov complexity, `rK^t_δ(x)`, for every (0<δ<1), and stated that `rK^t(x)=rK^t_{2/3}(x)).
2. Expanded Section 5 with a source-aligned proof outline of Theorem 4.3: the restricted-length function construction, its (n^3) random tapes, the padding step, the hypothetical inverter, the `Fail` promise problem, the Goldberg–Sipser compression step, and the roles of Claims 4.4 and 4.5.
3. Expanded the Theorem 4.7 explanation to distinguish the OWF-to-Cond-EP-PRG step from the transfer to boundary-MINrK, including the two properties explicitly used by Liu–Pass: small (rK^{poly})-complexity of generator outputs and (pK^t(x)\le rK^t(x)).
4. Clarified the proof architecture: Theorems 4.3 + 2.3 give the hardness-to-OWF direction; Theorem 4.7 gives the converse. The conditional ordinary-MINK result uses Theorem 4.6 and the stated derandomization assumption.

## Mathematical/editorial checklist

| Item | Review status |
|---|---|
| OWF definition | Present in Markdown; includes polynomial-time evaluation, PPT inversion, negligible success, and any valid preimage. |
| (K^t) definition | Present in Markdown. |
| (rK^t) definition | Present; fixed program and varying random tape explained. |
| General (rK^t_δ) notation | **Clarified in this update.** |
| (rK) versus (pK) | Distinction included in Markdown. |
| Boundary-MINK promise | YES/NO thresholds included. |
| Boundary-MINrK promise | YES/NO thresholds included; threshold-indexed notation now defined. |
| Theorems 1.1/4.2 | Conditional characterization stated with (E \not\subseteq ioSIZE[2^{εn}]) for some constant (ε>0). |
| Theorems 1.2/4.1 | Unconditional randomized-boundary characterization stated. |
| Theorems 4.3, 2.3, 4.7 | Expanded source-aligned proof outline; construction, inverter contradiction, compression, amplification, and converse ingredients summarized. |
| Theorems 1.3 and 1.4 | Presented separately as worst-case-to-average-case results. |
| Cryptographic implications | No claim that OWFs alone imply public-key encryption. |
| Open question | Ordinary MINK hardness without the boundary promise identified as unresolved. |
| Educational analogy | Explicitly labeled as pedagogical, not a theorem. |
| References | ITCS 2026, CRYPTO 2025, and FOCS 2020 entries included. |

## Source verification

The official ITCS 2026 paper by Yanyi Liu and Rafael Pass is published in LIPIcs, Volume 362, Article 97, DOI 10.4230/LIPIcs.ITCS.2026.97. Section 3 supports the generalized (rK^t_\delta) definition and the boundary-MINrK thresholds. Section 4.2, Theorem 4.3 and Claims 4.4–4.5 support the weak-OWF construction and compression-based contradiction; Section 4.3, Theorem 4.7 supports the Cond-EP-PRG and (pK^t\le rK^t) outline. The exposition is a proof outline, not a line-by-line reproduction or independent proof verification.

## Remaining checks before submission

1. Render the current Markdown to PDF and DOCX, or inspect the uploaded binaries, and compare their extracted text against the updated Markdown.
2. Inspect every PDF page for equation rendering, clipping, line breaks, and reference formatting.
3. Confirm the author/date/license line in both binary files.
4. Have the author approve the final artifacts before any MathDB submission.

**Disposition:** The Markdown source has been corrected and committed. The PDF and DOCX are confirmed present in the repository, but their internal content and visual rendering are not yet certified. This report is an editorial quality-control record, not independent peer review, committee certification, or proof of prize eligibility.
