# The One-Way Function Frontier: From Computational Hardness to the Foundations of Modern Cryptography

## An Exposition of Liu–Pass, ITCS 2026

**Author:** Kames xyz  
**Date:** 1 November 2026  
**Problem:** JSP-001025 — Existence of One-Way Functions (MathDB #405776)

> **Document status:** Reconstructed Markdown source prepared from the exposition text supplied in the conversation. This is not a byte-for-byte copy of the user's final PDF/DOCX binaries.

## Abstract

This exposition explains the characterization of one-way functions (OWFs) in terms of worst-case hardness of boundary versions of time-bounded Kolmogorov complexity established by Yanyi Liu and Rafael Pass. It introduces deterministic and randomized time-bounded Kolmogorov complexity, explains the boundary-MINK and boundary-MINrK promise problems, and distinguishes the unconditional randomized-complexity characterization from the conditional deterministic-complexity characterization.

For the parameter choice discussed by Liu and Pass, the existence of OWFs is equivalent to the statement that the corresponding boundary-MINrK^poly problem is not in ioBPP. The analogous boundary-MINK^poly characterization is obtained under a derandomization assumption excluding `E ⊆ ioSIZE[2^(εn)]` for some ε > 0. The exposition also summarizes related worst-case-to-average-case results, weak OWFs and amplification, and an open question concerning ordinary MINK hardness without the boundary promise.

The results are characterizations: they identify complexity-theoretic conditions equivalent to OWF existence; they do not prove unconditionally that OWFs exist.

## 1. Introduction

One-way functions are a foundational primitive in modern cryptography. Informally, an OWF is efficiently computable but computationally infeasible to invert on a randomly selected input, even when an inverter may output any valid preimage.

OWFs are closely connected to pseudorandom generators, pseudorandom functions, and digital signatures, and they are necessary for private-key encryption. Their existence is not known to follow from standard worst-case assumptions such as P ≠ NP. This motivates the search for precise complexity-theoretic conditions equivalent to OWF existence.

Liu and Pass study this question through time-bounded Kolmogorov complexity. Their ITCS 2026 work identifies boundary versions of minimum Kolmogorov complexity whose worst-case hardness characterizes OWFs.

## 2. One-Way Functions

Let
`f : {0,1}^* → {0,1}^*` be a deterministic polynomial-time computable function. It is a one-way function if, for every probabilistic polynomial-time algorithm A, the success probability
```
ε_A(n) = Pr[x ← {0,1}^n]
         [ f(A(1^n, f(x))) = f(x) ]
```
is negligible in n.

The inverter receives the security parameter and the image f(x). It succeeds if it outputs any valid preimage of f(x), not necessarily the original x. Thus, one-wayness concerns inversion of the function value rather than recovery of a particular input representation.

## 3. Time-Bounded Kolmogorov Complexity

Fix a universal machine U and a time bound t. The deterministic time-bounded Kolmogorov complexity of a string x is
```
K^t(x) = min { |Π| : U(Π, 1^{t(|x|)}) = x }.
```
It is the length of the shortest program that outputs x within the prescribed time bound.

The randomized version considered here is
```
rK^t(x) = min { |Π| :
  Pr_{r ← {0,1}^{t(|x|)}}[ U(Π^r, 1^{t(|x|)}) = x ] ≥ 2/3 }.
```
The program Π is fixed while its random tape varies. This model should not be conflated with pK, in which a common random string is available under a different quantifier structure.

The success threshold can be varied; the exposition uses the thresholds appearing in the Liu–Pass boundary formulations.

## 4. Boundary Minimum-Complexity Problems

The boundary promise is designed to focus on strings whose time-bounded description complexity lies close to the maximum possible range. It separates a YES case with a sufficiently short description under a smaller time bound and a sufficiently large complexity under a larger time bound from a NO case with a still larger lower bound.

For the parameter choice δ = 2/3, the deterministic boundary-MINK formulation uses:

- **YES:** `K^{t1}(x) ≤ n − 2` and `K^{t2}(x) > n − log n`.
- **NO:** `K^{t2}(x) ≥ n − 1`.

The randomized boundary-MINrK formulation uses:

- **YES:** `rK^{t1}_{2/3}(x) ≤ n − 4` and `rK^{t2}_{1/3}(x) > n − log n`.
- **NO:** `rK^{t2}_{1/3}(x) ≥ n − 3`.

The randomized thresholds and additive constants are part of the promise formulation. In particular, the expression
`ceil(log2(1/(1−δ)))` equals 2 when δ = 2/3.

## 5. Characterizing OWFs by Boundary Hardness

The central results distinguish randomized and deterministic time-bounded Kolmogorov complexity.

**Theorem 1.2 / Theorem 4.1 (randomized boundary characterization).** OWFs exist if and only if `boundary-MINrK^poly` is not in `ioBPP`. This characterization is unconditional.

**Theorem 1.1 / Theorem 4.2 (deterministic boundary characterization).** Assuming that, for some ε > 0,
`E ⊄ ioSIZE[2^(εn)]`, OWFs exist if and only if `boundary-MINK^poly` is not in `ioBPP`.

The randomized characterization is unconditional, whereas the deterministic characterization relies on the stated derandomization assumption. These qualifications are essential and should not be dropped when stating the results.

The proof strategy also relates weak one-way functions to strong one-way functions. Theorem 4.3 establishes weak OWFs from the relevant randomized boundary hardness. Yao-style hardness amplification (Theorem 2.3 in the cited work) upgrades weak OWFs to strong OWFs. The converse direction is established through the corresponding reduction (including Theorem 4.7). Together these ingredients yield the equivalence.

These theorems do not constitute an unconditional proof that OWFs exist. They give equivalent formulations of their existence in terms of computational hardness.

## 6. Worst-Case-to-Average-Case Connections

Liu and Pass also establish connections between worst-case and average-case hardness for time-bounded Kolmogorov complexity.

**Theorem 1.3.** Under the same derandomization assumption used for the deterministic characterization, `MINK^poly` is not in BPP if and only if `MINK^poly` is not in AvgBPP. The result also implies `NP ⊄ AvgBPP`. The associated reduction addresses the non-gap MINK problem in the large-threshold regime.

**Theorem 1.4.** Unconditionally, `MINK^poly` is not in P if and only if `MINrK^poly` is not in AvgP.

These worst-case-to-average-case statements are related results, but they are logically distinct from the main OWF characterizations. The assumptions and complexity classes in each theorem must be kept separate.

## 7. Cryptographic Significance and an Open Question

The characterization helps clarify what kind of worst-case hardness is sufficient to capture OWF existence. Since OWFs support important cryptographic constructions, the results connect a descriptive-complexity measure to the foundations of cryptography.

The implications should nevertheless be stated carefully. OWFs are necessary for private-key encryption and are sufficient for several major primitives, including pseudorandom generators, pseudorandom functions, and digital signatures. OWFs alone do not imply public-key encryption.

An important open direction is whether hardness of the ordinary MINK problem, without the boundary promise, can imply OWF existence. The boundary conditions are central to the known characterizations, and removing them is not established by the results summarized here.

## 8. An Intuitive Perspective on Description Complexity

Kolmogorov complexity measures the length of the shortest description that generates an object. Under a time bound, it also reflects the computational resources needed to produce the object from that description.

As an educational analogy, one may think of this as a measure of descriptive, morphological, or syntactic complexity: a highly structured object may admit a short description, while an object with little compressible structure may require a longer one. This analogy is explanatory only; it is not a theorem and does not replace the formal definitions.

The boundary formulations examine cases near the high-complexity end of the scale, where small changes in allowed computation time and description length become significant.

## 9. Conclusion

Liu and Pass provide precise links between one-way functions and worst-case hardness of boundary versions of time-bounded Kolmogorov complexity. The randomized boundary characterization is unconditional; the deterministic boundary characterization depends on a stated circuit lower-bound assumption. Their additional worst-case-to-average-case results deepen the connection between Kolmogorov complexity and computational complexity.

The main conceptual contribution is a characterization, not a resolution of the open existence question for OWFs. The boundary promise, randomized-versus-deterministic distinction, and conditional nature of the deterministic theorem are indispensable to an accurate reading of the results.

## References

1. Yanyi Liu and Rafael Pass, “One-Way Functions and Boundary Hardness of Randomized Time-Bounded Kolmogorov Complexity,” *ITCS 2026*, LIPIcs, vol. 362, article 97, pp. 97:1–97:19. DOI: [10.4230/LIPIcs.ITCS.2026.97](https://doi.org/10.4230/LIPIcs.ITCS.2026.97).
2. Yanyi Liu and Rafael Pass, “Hardness Along the Boundary: Towards One-Way Functions from the Worst-Case Hardness of Time-Bounded Kolmogorov Complexity,” *CRYPTO 2025*, LNCS 16000, pp. 617–650. DOI: [10.1007/978-3-032-01855-7_20](https://doi.org/10.1007/978-3-032-01855-7_20).
3. Yanyi Liu and Rafael Pass, “On One-way Functions and Kolmogorov Complexity,” *FOCS 2020*. DOI: [10.1109/FOCS46700.2020.00118](https://doi.org/10.1109/FOCS46700.2020.00118).

---

**Authorship and license note:** This exposition is original explanatory prose based on the cited research. The cited source paper is distributed under CC BY 4.0; that source license does not by itself determine the license of this exposition. The author may designate the exposition's own license separately.
