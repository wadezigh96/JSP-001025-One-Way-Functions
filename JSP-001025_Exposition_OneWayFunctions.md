# The One-Way Function Frontier: From Computational Hardness to the Foundations of Modern Cryptography

## An Exposition of Liu–Pass, ITCS 2026

**Kames xyz · 1 November 2026**

## Abstract

This exposition presents the central results of Liu and Pass (ITCS 2026), which characterize the existence of one-way functions in terms of the worst-case hardness of boundary versions of time-bounded Kolmogorov complexity. We introduce the formal definition of one-way functions, time-bounded Kolmogorov complexity \(K^t\), and randomized time-bounded Kolmogorov complexity \(rK^t\), carefully distinguishing \(rK\) from probabilistic Kolmogorov complexity \(pK\). We then explain the promise problems boundary-MINK and boundary-MINrK, including the precise thresholds in the special case \(\delta = 2/3\). The main results are an unconditional equivalence between the existence of one-way functions and the hardness of boundary-MINrK\(^{\mathrm{poly}}\) outside ioBPP (Theorems 1.2 and 4.1), and a conditional equivalence for boundary-MINK under the derandomization assumption that \(\mathrm{E}\) is not a subset of \(\mathrm{ioSIZE}[2^{\varepsilon n}]\) for some constant \(\varepsilon > 0\) (Theorems 1.1 and 4.2). We also discuss the related worst-case-to-average-case results (Theorems 1.3 and 1.4), the role of weak one-way functions and hardness amplification, and the open question of whether ordinary MINK hardness without the boundary promise suffices to imply one-way functions. All mathematical statements are based on Liu and Pass, ITCS 2026, DOI: 10.4230/LIPIcs.ITCS.2026.97.

## 1. Introduction: Why One-Way Functions Matter

One-way functions are the foundational primitive of private-key cryptography. Informally, a one-way function is easy to compute in the forward direction but hard to invert on average. Their existence is equivalent to the existence of pseudorandom generators, pseudorandom functions, and digital signatures. One-way functions are also necessary for private-key encryption and many other central cryptographic tasks (Impagliazzo’s “Minicrypt”). They do not, by themselves, yield public-key encryption.

A central open question in cryptography and complexity theory is whether there exists a natural worst-case hardness assumption that is equivalent to the existence of one-way functions. Liu and Pass have pursued this question through the lens of time-bounded Kolmogorov complexity. Their ITCS 2026 paper provides precise characterizations of one-way function existence in terms of boundary hardness of time-bounded Kolmogorov complexity.

## 2. The Mathematical Definition of One-Way Functions

A function \(f : \{0,1\}^* \to \{0,1\}^*\) is a one-way function if:

A deterministic algorithm computes \(f(x)\) in time polynomial in \(|x|\), for every input \(x\).

For every PPT adversary \(A\), the inversion success probability

\[
\varepsilon_A(n) = \Pr_{x \leftarrow \{0,1\}^n} [ f(A(1^n, f(x))) = f(x) ]
\]

is negligible in \(n\). The probability is over the uniform choice of \(x\) and the internal randomness of \(A\). The adversary succeeds by finding any valid preimage of \(f(x)\), not necessarily the original input \(x\).

## 3. Time-Bounded Kolmogorov Complexity

The classical Kolmogorov complexity \(K(x)\) of a string \(x\) is the length of the shortest program that outputs \(x\) on a fixed universal Turing machine. The time-bounded version \(K^t(x)\) is the length of the shortest program that outputs \(x\) within time \(t(|x|)\).

Formally (Liu–Pass, Section 3):

\[
K^t(x) = \min \{ |\Pi| : U(\Pi, 1^{t(|x|)}) = x \}
\]

The randomized time-bounded Kolmogorov complexity \(rK^t(x)\) is the length of the shortest randomized program \(\Pi\) such that, when its random tape is fixed to a random string \(r\), the resulting deterministic program outputs \(x\) with probability at least \(2/3\):

\[
rK^t(x) = \min \{ |\Pi| : \Pr_{r \leftarrow \{0,1\}^{t(|x|)}} [ U(\Pi^r, 1^{t(|x|)}) = x ] \ge 2/3 \}
\]

In \(rK\), a single program \(\Pi\) is fixed and the randomness \(r\) is varied over its random tape of length \(t(|x|)\). This is distinct from the probabilistic Kolmogorov complexity \(pK\), in which a random string is first chosen and the program may then depend on that string (a common-random-string model). Liu–Pass work with the more standard \(rK\) notion.

## 4. Boundary-MINK and Boundary-MINrK

The ordinary promise problem MINK\(_{t_1,t_2}\) asks whether a string is “structured” (\(K^{t_1}(x) \le n-2\)) or “random” (\(K^{t_2}(x) \ge n-1\)). The boundary version restricts attention to the intermediate regime.

Boundary-MINK\(_{t_1,t_2}\) (Liu–Pass, p. 97:4):

- **YES:** \(K^{t_1}(x) \le n - 2\) and \(K^{t_2}(x) > n - \log n\)
- **NO:** \(K^{t_2}(x) \ge n - 1\)

For the randomized version with parameter \(\delta = 2/3\), we have \(\lceil \log_2(1/(1-\delta))\rceil = \lceil \log_2 3\rceil = 2\). The boundary-MINrK promise is:

- **YES:** \(rK^{t_1}_{2/3}(x) \le n - 4\) and \(rK^{t_2}_{1/3}(x) > n - \log n\)
- **NO:** \(rK^{t_2}_{1/3}(x) \ge n - 3\)

YES instances lie in the near-random boundary region; NO instances remain fully complex even under the larger time bound. The boundary restriction plays a central role in the reductions developed in the paper.

## 5. The Main Characterizations

**Theorem 1.2 / Theorem 4.1 (Liu–Pass).** One-way functions exist if and only if boundary-MINrK\(^{\mathrm{poly}} \notin \mathrm{ioBPP}\). This equivalence is unconditional.

**Theorem 1.1 / Theorem 4.2.** Assume there exists a constant \(\varepsilon > 0\) such that \(\mathrm{E} \not\subseteq \mathrm{ioSIZE}[2^{\varepsilon n}]\). Then one-way functions exist if and only if boundary-MINK\(^{\mathrm{poly}} \notin \mathrm{ioBPP}\).

**Theorem 4.3 (Liu–Pass).** If boundary-MINrK\(^{\mathrm{poly}} \notin \mathrm{ioBPP}\), then weak one-way functions exist. Yao’s hardness amplification (Theorem 2.3) converts any weak one-way function into a strong one-way function, establishing the “if” direction of Theorem 4.1. The converse direction (existence of one-way functions implies boundary-MINrK\(^{\mathrm{poly}} \notin \mathrm{ioBPP}\)) is proved as Theorem 4.7. Together, Theorems 4.3, 2.3, and 4.7 establish the equivalence stated in Theorem 4.1.

These results do not prove that one-way functions exist. They give precise characterizations of what hardness would suffice.

## 6. Separate Worst-Case-to-Average-Case Results

**Theorem 1.3.** Under the same derandomization assumption, MINK\(^{\mathrm{poly}} \notin \mathrm{BPP}\) if and only if MINK\(^{\mathrm{poly}} \notin \mathrm{AvgBPP}\). This result also implies that \(\mathrm{NP} \not\subseteq \mathrm{AvgBPP}\). It provides a worst-case-to-average-case reduction for the exact (non-gap) MINK problem in the large-threshold regime.

**Theorem 1.4.** Unconditionally, MINK\(^{\mathrm{poly}} \notin \mathrm{P}\) if and only if MINrK\(^{\mathrm{poly}} \notin \mathrm{AvgP}\).

These statements are independent of the main one-way-function characterizations and should not be conflated with them.

## 7. Cryptographic Consequences and Open Questions

The existence of one-way functions is equivalent to the existence of pseudorandom generators, pseudorandom functions, and digital signatures. One-way functions are also necessary for private-key encryption and many other central cryptographic tasks. Liu–Pass do not claim that their hardness assumptions imply public-key encryption.

The principal open question remaining is whether worst-case hardness of ordinary MINK\(^{\mathrm{poly}}\) (without the boundary promise) already implies the existence of one-way functions. This remains open.

## 8. Educational Analogy (Not a Theorem)

One may think of Kolmogorov complexity as measuring the “descriptive complexity” of a string, analogous to the morphological and syntactic complexity of a linguistic utterance. A string that is easy to describe with a short program is like a highly regular grammatical sentence; a string that requires a long program is like an irregular, information-rich text. The boundary regime corresponds to sentences that are almost fully complex under a tight descriptive budget but become compressible if more time (or a longer grammar) is allowed. This analogy is purely pedagogical and is not a formal result.

## 9. Conclusion

Liu and Pass (ITCS 2026) show that the existence of one-way functions is equivalent to the worst-case hardness of a natural boundary version of randomized time-bounded Kolmogorov complexity. Under a standard derandomization assumption the same holds for ordinary time-bounded Kolmogorov complexity. These are characterizations, not existence proofs. The work provides precise complexity-theoretic characterizations of the foundations of private-key cryptography.

## References

Yanyi Liu and Rafael Pass. *One-Way Functions and Boundary Hardness of Randomized Time-Bounded Kolmogorov Complexity*. In 17th Innovations in Theoretical Computer Science Conference (ITCS 2026). Leibniz International Proceedings in Informatics (LIPIcs), Volume 362, pp. 97:1–97:19. Schloss Dagstuhl. DOI: 10.4230/LIPIcs.ITCS.2026.97

Yanyi Liu and Rafael Pass. *Hardness Along the Boundary: Towards One-Way Functions from the Worst-Case Hardness of Time-Bounded Kolmogorov Complexity*. In Advances in Cryptology – CRYPTO 2025. LNCS 16000, pp. 617–650. DOI: 10.1007/978-3-032-01855-7_20.

Yanyi Liu and Rafael Pass. *On One-way Functions and Kolmogorov Complexity*. In 2020 IEEE 61st Annual Symposium on Foundations of Computer Science (FOCS). DOI: 10.1109/FOCS46700.2020.00118.

---

This exposition is original explanatory prose based on the cited research. The source paper is CC BY 4.0; the copyright and license of this exposition remain with the author.
