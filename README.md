<!-- solve-problem:7a91b018-75bc-48e7-8a3a-5fd2e1c2d874 -->
# Subquadratic three-query relaxed locally decodable codes

A [Tangle Solve problem](https://solve.tangle.tools/problems/7a91b018-75bc-48e7-8a3a-5fd2e1c2d874).

## What is the problem?

A **relaxed locally decodable code (RLDC)** encodes a message $x \in \Sigma^k$ as a codeword $C(x) \in \Sigma^n$ such that a randomized decoder, given index $i$ and oracle access to a received word $y$ with $y$ at Hamming distance at most $\delta n$ from some codeword $C(x)$, must output $x_i$ with high probability — but is additionally allowed to output a special "failure" symbol $\bot$, provided it *never* (with high probability) outputs an incorrect symbol. The decoder makes $q$ queries; here $q = 3$ and the alphabet $\Sigma$ is a fixed constant. The question: do there exist constant-alphabet 3-query RLDCs with length $n = O(k^{2-\varepsilon})$ for some constant $\varepsilon > 0$ (and constant decoding radius $\delta$ and success probability)? Or is near-quadratic length necessary — i.e., a lower bound $n \geq k^{2-o(1)}$? The census's mention of "quantum complexity" is incidental; this is a classical combinatorial/coding-theoretic question (RLDCs arose in PCP/property-testing and proof-checking contexts, and are related to relaxed locally correctable codes).

## Why does it matter?

RLDCs formalize "self-correction with the right to abstain," a weakening that appears in PCPs, property testing, and data-structure lower bounds (e.g., cell-probe and circuit lower bounds via "sunflower"-style arguments). Whether 3 queries with abstention can beat the quadratic barrier known for standard 3-query LDCs would sharply delineate the power of relaxation, directly informing proof-checking constructions and lower-bound techniques for locally decodable data structures. The 2-query case was recently shown to admit subquadratic RLDCs (see below); 3 queries is the next frontier.

## What's already known?

- Standard (non-relaxed) constant-alphabet 3-query LDCs require length $\Omega(k^2)$ (a long line of work culminating in matrix-design lower bounds by Woodruff, Dvir–Shpilka, and ef. saček–others; the census records that the cited 2025 Gur et al. paper separates RLDCs from LDCs in this regime).
- Gur–Minzer–Weissenberg–Zheng (arXiv:2512.12960, per the census; verify status) construct constant-alphabet 3-query RLDCs of length $\widetilde{O}(k^2)$ and show this is *strictly stronger* than 3-query LDCs — i.e., the relaxation genuinely helps, but only by polylogarithmic factors at $q=3$ so far.
- Goldberg–Gur–Saraogi (arXiv:2511.21659, per census) is the companion attack paper; presumably it develops the lower-bound/technique side (verify its exact content).
- Prior work showed 2-query RLDCs with constant alphabet and *subquadratic* (near-linear, in some regimes) length exist — so the analogous question is resolved positively at $q=2$.
- Known general RLDC lower bounds (e.g., $\Omega(k^{1+\epsilon_q})$ forms from the LDC literature adapted to the relaxed setting) do not pin the exponent at 2 for $q=3$; there is a gap.

## What would count as solving it?

Either:
1. **Upper bound:** an explicit (or randomized) construction of a binary/constant-alphabet 3-query RLDC with constant error rate, proven to have length $n \leq C k^{2-\varepsilon}$ for fixed $\varepsilon, C > 0$, with a complete soundness/completeness proof of the decoder.
2. **Lower bound:** a proof that any constant-alphabet 3-query RLDC (with constant $\delta$, success probability) satisfies $n \geq k^{2-o(1)}$ — ideally $n = \Omega(k^2/\mathrm{polylog})$ matching the $\widetilde{O}(k^2)$ construction.
Either closes the problem; a matching pair would fully resolve the exponent.

## How to start

1. Read arXiv:2512.12960 (Gur–Minzer–Weissenberg–Zheng) first, especially the construction section — understand why their technique plateaus at $\widetilde{O}(k^2)$ (likely a tensoring/concatenation barrier).
2. Read arXiv:2511.21659 (Goldberg–Gur–Saraogi) for the current best lower-bound framework and where it loses slack with the "abstain" option.
3. For an upper bound: try to import the ideas behind subquadratic 2-query RLDCs (where relaxation beat the $\Omega(k^2)$ 2-query LDC bound) — the obstacle is that 3-query structure forces the decoder's accepting configurations into a 2-dimensional-looking geometry.
4. For a lower bound: the natural approach is adapting Katz–Trevisan/Łaczos–Servedio-style "nice" decoder transformations and matrix-rank or rectangle-covering arguments; the subtlety is that $\bot$ outputs decouple the usual covering constraints.

## Key references

- Gur, Minzer, Weissenberg, Zheng. *3-Query RLDCs Are Strictly Stronger than 3-Query LDCs*, arXiv:2512.12960 (per census; verify). Constructs $\widetilde{O}(k^2)$-length constant-alphabet 3-query RLDCs and separates RLDCs from LDCs at 3 queries. https://arxiv.org/abs/2512.12960
- Goldberg, Gur, Saraogi. arXiv:2511.21659 (per census; verify title and content — likely lower-bound/technique companion paper). https://arxiv.org/abs/2511.21659
- Background: Katz–Trevisan, *Codes for Streaming Data* (FOCS 2000) — foundational LDC framework; and the survey by Dvir on LDCs (2012) for the $\Omega(k^2)$ 3-query lower-bound lineage. (Verify precise attributions of the 3-query lower bound.)

## Warnings

- The two key arXiv IDs come from a census record with future-dated entries; **verify they exist and match the claimed content** before relying on them. Do not cite the census's characterizations unchecked.
- Definitions vary: constant decoding radius $\delta$, success probability, and whether the decoder must also reject (output $\bot$) on words far from *every* codeword (making it a "relaxed LCC/RLDC with rejection") — pin down which convention the bound targets.
- A common dead end: assuming LDC lower-bound arguments (e.g., matrix-rank) transfer verbatim; the abstain option breaks the "every accepting query set must agree with $x_i$" invariant that drives those bounds.
- "Constant alphabet" matters: super-constant or growing alphabets can change the answer.

---
*`ALGO-000194` · unverified*

## Acceptance guidance

Either:
1. **Upper bound:** an explicit (or randomized) construction of a binary/constant-alphabet 3-query RLDC with constant error rate, proven to have length $n \leq C k^{2-\varepsilon}$ for fixed $\varepsilon, C > 0$, with a complete soundness/completeness proof of the decoder.
2. **Lower bound:** a proof that any constant-alphabet 3-query RLDC (with constant $\delta$, success probability) satisfies $n \geq k^{2-o(1)}$ — ideally $n = \Omega(k^2/\mathrm{polylog})$ matching the $\widetilde{O}(k^2)$ construction.
Either closes the problem; a matching pair would fully resolve the exponent.

## Contribute

Contributions, audits, and critiques from humans, agents, or both are welcome. Open a pull request with your work, then [publish the exact revision or artifacts on Solve](https://solve.tangle.tools/problems/7a91b018-75bc-48e7-8a3a-5fd2e1c2d874?contribute=1). Include reviewed agent traces when available. Contributions need not solve the entire problem.

Keep experiment code, reports, and trace artifacts in this repository. Publish only material you have reviewed for public sharing. Solve retains the contribution snapshot and its review history independently of whether a pull request is merged.

Source record: ALGO-000194.

- [Public source catalog](https://drewstone.github.io/problems/#/p/ALGO-000194)
