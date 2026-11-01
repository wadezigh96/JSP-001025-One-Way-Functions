# JSP-001025 — Quality-Control Report

**Author:** Kames xyz  
**Date:** 1 November 2026  
**Status:** READY FOR AUTHOR REVIEW

## Scope

The exposition Markdown in this repository has now been replaced with the full text supplied by the author in the conversation. This review checks the structure and claims represented in that text. The actual PDF and DOCX binary files and their download URLs were not attached or included in the message, so their layout, pagination, metadata, and byte-for-byte identity cannot be independently verified here.

## Mathematical and editorial checklist

| Item | Review |
|---|---|
| OWF definition | Includes polynomial-time evaluation, PPT inversion, negligible success, and acceptance of any valid preimage. |
| (K^t) definition | Included with universal-machine and time-bound notation. |
| (rK^t) definition | Included with fixed program and varying random tape. |
| (rK) versus (pK) | Distinction and common-random-string explanation included. |
| Boundary-MINK promise | YES and NO thresholds included. |
| Boundary-MINrK promise | YES and NO thresholds included for (delta=2/3). |
| Theorem 1.2 / 4.1 | Stated as unconditional randomized-boundary characterization. |
| Theorem 1.1 / 4.2 | Stated with the condition (mathrm{E}
otsubseteqmathrm{ioSIZE}[2^{arepsilon n}]). |
| Theorems 4.3, 2.3, 4.7 | Weak OWF, amplification, and converse direction summarized. |
| Theorems 1.3 and 1.4 | Presented as separate worst-case-to-average-case results. |
| Cryptographic implications | Text explicitly avoids claiming OWFs imply public-key encryption. |
| Open question | Ordinary MINK hardness without boundary promise is identified as unresolved. |
| Educational analogy | Explicitly labeled as not a theorem. |
| References | Three Liu–Pass works and DOI identifiers are listed. |

## Limitations and author checks

1. This is an exposition of cited results, not a proof that one-way functions exist.
2. The deterministic boundary characterization is conditional; the randomized characterization is stated as unconditional.
3. This report is an editorial consistency checklist, not independent peer review or committee certification.
4. The PDF and DOCX binaries were not supplied as attachments or accessible download URLs in the conversation. Their typography, equations as rendered, pagination, metadata, and identical content have therefore not been checked.
5. Before formal submission, compare both final binaries against the Markdown source and inspect every PDF page.

**Disposition:** The author-provided text is now published in the repository as Markdown. Binary PDF/DOCX verification remains outstanding.
