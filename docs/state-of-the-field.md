# State of the field — unbounded reliable copying from bounded, unreliable parts

*Reference capture, 2026-07-23. Distilled from the multi-model outbound report [`../copy research.md`](../copy%20research.md) (three independent models on the brief "what is the established landscape for unbounded reliable copying from bounded unreliable parts") plus this session's own web survey. **This supersedes the earlier coding-only reframe.** Provenance is marked: **[triangulated]** = all three models + independent search agree (high confidence); **[report]** = report-sourced, not independently re-verified here.*

## The load-bearing conclusions

1. **Single-component reliability is provably bounded — a *thermodynamic* theorem, not merely information-theoretic.** [triangulated] Finite temperature + finite barrier + finite time ⟹ nonzero error (Kramers/Arrhenius); the floor is set by Landauer + the thermodynamic uncertainty relations (TUR). An idealized zero-temperature/infinite-time gate could be perfect; a physical one cannot. This half of the earlier claim survives cleanly — but the reason is thermodynamic, not coding-theoretic.

2. **"Unbounded reliability needs redundancy + active driven correction" is corroborated as a *theorem-schema*, with three corrections** [triangulated]:
   - **Redundancy generalizes** beyond spatial copies to **temporal** (kinetic proofreading probes one site repeatedly), **population/ecological**, and **topological** redundancy.
   - **The load-bearing invariant is dissipation, not the code:** "correcting errors faster than they are created" (the threshold-theorem essence). The redundancy *structure* is secondary to the entropy-export.
   - **Passive (equilibrium) self-correction exists but does not copy and does not scale in general:** topological memories (4D toric code; a reported 3D passive self-correcting quantum memory [report]) protect a *bit* with a size-scaling energy barrier — but they are memory-only and need special geometry/dimension. Passive redundancy alone (a bigger crystal) saturates.

3. **Frontier verdict: no known system shows un-engineered, unbounded, emergent error correction.** [triangulated] Every real system saturates at a thermodynamic floor OR requires designed redundancy, fuel, or population selection:
   - **Templated-ligation cascade** (Toyabe et al. 2025, [arXiv 2505.08232](https://arxiv.org/abs/2505.08232)): error *decreases* with chain length — a genuine reversal of chain-growth accumulation — and inherits proofreading; but **saturates (~10⁻²–10⁻³ per domain, TUR-bounded), and the cascade is a designed fragment network + driven cycling.** [scaling reversal verified this session; saturation/designed verdict = report]
   - **Asymmetric-cooperativity proofreading** (Ghosh/Sahu/Subramanian, 2025–26): error correction that **scavenges the primary strand-growth free-energy gradient — no extraneous fuel.** Reaches ~10⁻⁴, then **saturates** (cannot reach 10⁻⁹ without a dedicated exonuclease). [report] *The closest chemistry to "gate 6 with the least added machinery."*
   - **Virtual Circular Genome (VCG):** a **distributed** genome — no single molecule holds it; errors suppressed by ecological competition + terminal stalling under thermal cycling. [report] A genuinely different architecture: the register is a *population of overlapping fragments*, not one tape.
   - **Speed-selected proofreading** (Ravasio/Husain/Murugan/Szostak, Science 2026): proofreading can **evolve from selection for speed alone** — stalling makes uncorrected errors slower, so correction is a prerequisite for speed, not a tax on it. [report] Explains how a corrector *arises*; the mechanism is still a driven dissipative loop, bounded by step count.

4. **The genuine open frontier — flagged independently by all three models — is CLOSURE / self-description.** [triangulated] Coding/QEC/fault-tolerance theory *assumes the decoder/corrector already exists*. A replicator must **copy its own corrector.** That transition — "a corrector exists" → "the corrector reproduces itself" — is where von Neumann's universal constructor, autopoiesis, origin-of-life, and TP's closure gate converge, and it is **not a settled theorem in any field.** This is the real gate 6.

## Blind fields a coding/QEC framing misses [report]

Non-equilibrium thermodynamics / TUR (the true floor); control theory & active matter (feedback-stabilized unstable states); evolutionary dynamics (population-level correction; speed-selection); reliability engineering (correlated / wear-out failures break the i.i.d. assumption); condensed matter (topological passive correction + no-go theorems); neuroscience (analog codes, grid cells); distributed consensus / Byzantine fault tolerance; developmental biology; autopoiesis / constraint-closure.

## The corrected invariant for gate 6

Not "a code." Rather: **entropy exported faster than errors are created, across redundant degrees of freedom (spatial / temporal / population / topological), with the corrector itself copied (closure).** Single-site *unbounded* capacity — what the 1-D and folding challenges demanded — is confirmed the **wrong target**: temporal-redundancy proofreading gives *bounded* single-site improvement (Toyabe, asymmetric cooperativity both cap), consistent with our folding wall. The live problem is **closure + minimal machinery**, and the drive-scavenging of asymmetric cooperativity is the standing minimal-machinery lead.

## What TP can actually contribute (imports, not claims)

Lay the frontier systems alongside the circuit and score them against the closure-corrected gate 6. The two most relevant imports: **asymmetric cooperativity** (drive-scavenged proofreading — gate 6 with minimal added machinery, capped) and the **VCG** (a distributed register — heredity without a single tape). The native lead is the **anisotropically-driven topological register** — see [`../STATE.md`](../STATE.md) §Field reconciliation (a candidate "top," marked named-not-built; its promise is that *drive-as-universal-corrector* attacks the closure gate directly).

*Full report + citations: [`../copy research.md`](../copy%20research.md).*
