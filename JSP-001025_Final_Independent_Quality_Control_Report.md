# JSP-001025 — Independent Quality-Control Report

**Author:** Kames xyz  
**Date:** 1 November 2026  
**Status:** READY FOR AUTHOR REVIEW — source-basis limitation applies

## Scope and evidence

This report records the checks that can be supported from the material available in the conversation. The final PDF and DOCX binaries named in the earlier QC notes were not attached in this session and could not be opened or independently inspected here. Accordingly, this report does **not** certify the layout, pagination, metadata, or byte-for-byte identity of those binaries.

The Markdown exposition committed alongside this report is a reconstructed source based on the exposition text and theorem summaries supplied in the conversation. It should be compared against the author's final PDF/DOCX before submission.

## Mathematical and editorial checks

| Item | Review result |
|---|---|
| OWF definition | The exposition states the PPT inverter definition and negligible success probability; any valid preimage is accepted. |
| Deterministic time-bounded Kolmogorov complexity | Formula and interpretation included. |
| Randomized time-bounded Kolmogorov complexity | Formula, fixed program, random-tape interpretation and 2/3 threshold included. |
| Boundary-MINK | YES/NO promise thresholds included as supplied. |
| Boundary-MINrK | YES/NO promise thresholds included as supplied. |
| Theorem 1.2 / 4.1 | Presented as an unconditional randomized-boundary characterization. |
| Theorem 1.1 / 4.2 | Presented with the assumption E not subset ioSIZE[2^(εn)] for some ε > 0. |
| Weak-to-strong OWF connection | Amplification and converse direction summarized, not reproved. |
| Theorem 1.3 | Worst-case/average-case statement and NP not subset AvgBPP consequence included under the stated assumption. |
| Theorem 1.4 | Unconditional MINK/MINrK relationship included. |
| Cryptographic implications | No claim that OWFs imply public-key encryption. |
| Open question | Ordinary MINK hardness without the boundary promise is identified as unresolved in this exposition. |
| References | Three cited Liu–Pass works and DOI identifiers included. |

## Important qualifications

1. The exposition is an explanation of published results, not a proof that one-way functions exist.
2. The randomized and deterministic boundary characterizations have different assumption status; the deterministic result is conditional.
3. The analogy in Section 8 is pedagogical and is not presented as a formal theorem.
4. This report is an author-side editorial/mathematical consistency checklist. It is not an independent peer review or a certification by the Justin Sun Prize committee.
5. The original final PDF/DOCX files and their full-page rendering were not available for independent inspection in this session. Do not interpret this report as a binary-file QC sign-off.

## Before author submission

- Compare the reconstructed Markdown against the exact final PDF and DOCX.
- Verify all displayed equations, subscripts, superscripts, logarithms, probability quantifiers and theorem numbering against the cited ITCS 2026 paper.
- Inspect every PDF page, including references, headers, footers and page breaks.
- Confirm that PDF and DOCX contain identical substantive text.
- Confirm author name, date, title, DOI links and license statement.
- Use the official MathDB submission route only when the pilot process is activated and the problem entry provides a confirmed exposition-submission link.

**Final QC disposition:** The available source summary supports the mathematical scope listed above, but the reconstructed source and absent binary files mean this is not a final approval of the author's PDF/DOCX. Status remains **READY FOR AUTHOR REVIEW**.
