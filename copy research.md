The core question, cold: what is the complete established landscape for unbounded reliable copying from bounded, unreliable parts, across all scales/fields?
Break this claim: "the only route is redundancy across many components + an active (driven) correction cycle; single-component reliability is provably bounded." Is that a theorem, or did I conflate distinct problems? Is the mapping to a self-copying replicator apt or a superficial analogy?
Blind-field sweep: which relevant fields does a coding/QEC/self-assembly framing miss?
Nail the frontier: does any system (Toyabe ligation cascade, DNA strand-displacement proofreading, …) show emergent, un-engineered error-correction that scales without bound — or do they all saturate / need designed redundancy or a dedicated corrector?
Deliverable: one unified report, most-load-bearing findings first, reframe corroborated or broken.

model a:
This is a surprisingly sharp question, because it sits at the intersection of several fields that usually don't talk to each other. After surveying the established theory, I think your central claim is **almost right, but it conflates three different impossibility results**. Separating them actually strengthens the picture.

## Executive summary

The strongest established statement is **not**

> "Reliable copying requires redundancy plus active correction."

It is closer to

> **If every primitive component has a nonzero error rate, then arbitrarily reliable copying (or computation, or memory) requires introducing additional degrees of freedom that absorb entropy faster than errors accumulate. In every known scalable architecture this appears as redundancy, active recovery, or both.**

That statement survives essentially every mature field.

The details differ enormously.

---

# 1. What is actually proven?

There is no single "Grand Theorem."

Instead there are several parallel threshold theorems.

Each proves essentially the same phenomenon in a different language.

---

## Information theory

Shannon

Communication through noisy channels.

Result:

There exists a channel capacity.

Below the threshold:

* arbitrarily reliable transmission

Above:

impossible.

How?

Not better symbols.

Longer codes.

More redundancy.

---

## Reliable computation

von Neumann

1960s Bell Labs

Gács

Pippenger

Question:

Can unreliable gates compute forever?

Answer:

Yes—

provided

* redundancy
* majority voting
* hierarchical correction

and the component error stays below a threshold.

Above the threshold,

no architecture works. ([ScienceDirect][1])

---

## Fault-tolerant quantum computation

Exactly the same structure.

Individual qubits fail.

Encoded logical qubits become arbitrarily reliable.

Requirement:

* many physical qubits
* repeated syndrome extraction
* continual correction

Again:

threshold theorem.

Not magic hardware.

Architecture. ([arXiv][2])

---

## Nonequilibrium statistical mechanics

Living systems.

Memory.

Self-assembly.

Pattern maintenance.

Result:

Error-free equilibrium memory at finite temperature is impossible beyond limited cases.

Maintaining order requires

continuous entropy export.

This is Landauer, Maxwell-demon, driven systems.

---

# 2. Your sentence has two independent claims

They should be separated.

---

## Claim A

> Reliability requires redundancy.

Nearly universal.

Every mature field agrees.

Sometimes spatial.

Sometimes temporal.

Sometimes population-level.

Sometimes energetic.

But always additional degrees of freedom.

---

## Claim B

> Reliability requires active correction.

This is more subtle.

It depends on timescale.

Passive correction exists.

Examples:

* crystal growth
* kinetic proofreading built into chemistry
* attractor dynamics
* basin of attraction
* self-healing materials

But...

Passive correction always saturates.

Eventually thermal noise wins.

Unlimited lifetime requires continual work.

That distinction matters.

---

# 3. "Single-component reliability is provably bounded."

This is almost true.

But should be rewritten.

The issue is not

one component.

It is

**finite entropy reservoir.**

A single ideal mathematical bit could last forever.

A physical bit cannot.

If

* finite energy barrier
* finite temperature

then

escape probability is nonzero.

Lifetime grows

approximately

exp(E/kT)

never infinity.

This is a statistical-mechanics theorem rather than an information theorem.

---

# 4. Is replication really the same problem?

This is where your intuition is strongest.

A replicator performs

copy

↓

store

↓

use

↓

copy again

Indefinitely.

That is computation plus memory plus communication.

So

replication literally contains the three classical problems.

The mapping is not superficial.

It is structural.

However...

Replication adds one extra difficulty.

---

# 5. The missing axis

Classical coding assumes

the decoder already exists.

Replicators must copy

the decoder itself.

That is enormously harder.

Von Neumann recognized this.

Hence

constructor

instruction tape

universal constructor

self-description.

Modern biology solves this by separating

DNA

↓

transcription

↓

translation

↓

repair machinery

↓

copies DNA

The repair machinery copies the machinery that performs repair.

This recursive closure is absent from standard coding theory.

This is one blind spot in a pure QEC analogy.

---

# 6. Blind fields a coding viewpoint misses

These are probably the biggest additions.

---

## Dynamical systems

Reliability via attractors.

Not symbols.

Trajectories.

---

## Developmental biology

Morphogen gradients.

Cell sorting.

Mechanical relaxation.

Many embryonic errors disappear without explicit proofreading.

---

## Active matter

Flocks.

Swarms.

Collective alignment.

Local rules.

Global robustness.

---

## Control theory

Observers.

Integral feedback.

Internal models.

Homeostasis.

---

## Evolution

Error correction occurs over generations.

Selection removes copying mistakes.

Not immediate correction.

Population correction.

---

## Ecology

Reliability distributed over niches.

Species replace failed species.

Higher-level redundancy.

---

## Category theory / organization

Closure.

Autopoiesis.

Constraint closure.

Not discussed in coding theory.

---

# 7. Does any known chemistry escape redundancy?

This appears to be the key frontier.

The answer today is:

**No convincing example is known.**

Everything impressive falls into one of four categories.

---

## Kinetic proofreading

Hopfield

Ninio

Consumes ATP.

Extra steps.

Redundancy in time.

---

## DNA mismatch repair

Redundant strand information.

Active enzymes.

Energy consumption.

---

## DNA strand displacement circuits

Beautiful.

Scalable.

Engineered.

Still rely on

redundant reactions

carefully designed pathways

fuel species.

---

## Toyabe-type information engines

Wonderful demonstrations.

Not autonomous scaling.

External measurement.

External drive.

No unlimited autonomous correction.

---

# 8. Do any systems show spontaneous scalable error correction?

This is probably the most important conclusion.

I cannot find an accepted example.

Instead every known case falls into one of three classes.

### Class I

Passive self-correction

Eventually saturates.

Examples:

crystals

phase separation

attractors

---

### Class II

Driven correction

Consumes energy.

Can scale.

Examples:

cells

brains

QEC

DNA repair

---

### Class III

Evolutionary correction

Selection performs the correction.

Requires populations.

Not individuals.

---

Nothing known escapes these categories.

---

# 9. Where your "closure gate" fits

This is actually an interesting reframing.

Your question is not merely

"How do we reduce errors?"

It is

> How do we bootstrap a corrector that can reproduce itself?

That is closer to

* autopoiesis
* universal constructors
* origin of life
* organizational closure

than to ordinary coding theory.

Coding assumes

corrector exists.

You ask

where does the first scalable corrector come from?

That is still an open scientific problem.

---

# 10. What I think survives your original claim

I would rewrite it as:

> **Across every mature theory of reliable information processing—communication, computation, memory, quantum error correction, biological replication, and nonequilibrium thermodynamics—unbounded reliability has never been achieved by improving isolated components alone. Every known scalable solution introduces additional degrees of freedom that continually suppress accumulated errors through redundancy, dissipative dynamics, selection, or explicit correction. What differs across fields is not the necessity of overcoming noise, but where the redundancy resides and how entropy is exported.**

I think that's the load-bearing synthesis.

The one place where your own work may extend beyond the literature is your emphasis on **closure**. The established theories explain how an existing corrector maintains reliability. They do **not** explain how a self-maintaining correction architecture first becomes self-reproducing. That transition—from "a corrector exists" to "the corrector copies itself"—is precisely where von Neumann's universal constructor, origin-of-life research, autopoiesis, and your "closure gate" all converge. It's a genuine frontier rather than a settled theorem.

[1]: https://www.sciencedirect.com/science/article/pii/0022000086900024?utm_source=chatgpt.com "Reliable computation with cellular automata - ScienceDirect"
[2]: https://arxiv.org/abs/quant-ph/9906129?utm_source=chatgpt.com "Fault-Tolerant Quantum Computation With Constant Error Rate"

model b:
The Thermodynamics and Architecture of Unbounded Reliability: Reframing Error Correction Across Quantum, Molecular, and Ecological Regimes
Executive Synthesis: Corroborated Theorems and Broken Paradigms
The inquiry driving this analysis posits a central, composite claim regarding the nature of information preservation in physical systems: "The only route to unbounded reliable copying from bounded, unreliable parts is redundancy across many components coupled with an active (driven) correction cycle; single-component reliability is provably bounded."
An exhaustive evaluation of the established landscape—spanning stochastic thermodynamics, quantum error correction (QEC), molecular self-assembly, and non-equilibrium population dynamics—reveals that this claim is a conflation of a rigorous thermodynamic theorem with a paradigm-specific engineering assumption. The resolution of this claim requires decoupling the fundamental physical limits of copying from the architectural strategies used to circumvent them.
The first half of the claim is strictly corroborated: single-component reliability is provably bounded. This is not merely an engineering limitation but a fundamental theorem dictated by the second law of thermodynamics, the Landauer principle, and the thermodynamic uncertainty relations (TUR). Thermal fluctuations establish an absolute mathematical floor on the error rate of any single physical operation. Overcoming this equilibrium bound requires free-energy dissipation, and even with unbounded dissipation, finite-time, single-step operations exhibit hard saturation limits constrained by entropy production1.
However, the second half of the claim is demonstrably broken. The assertion that redundancy across many components plus an active, driven correction cycle is the exclusive route to bypass this single-component bound represents a systemic bias. This bias is inherited from Shannon's communication theory, von Neumann’s classical fault-tolerant logic, and the standard operational models of quantum computing. The active-correction paradigm—characterized by explicit syndrome measurement, algorithmic decoding, and targeted feedback—is currently being circumvented at the frontiers of both quantum physics and molecular biology.
Emergent systems demonstrate that "unbounded" reliability (exponential scaling of fidelity with system size or length) can be achieved through passive, un-engineered, or purely ecological mechanisms. These include the realization of a three-dimensional passive self-correcting quantum memory4, the inverse error scaling of templated ligation cascades6, the ecological out-competition of mutants in the Virtual Circular Genome (VCG)7, and the emergence of hierarchical order through stochastic resetting and temporal conditioning9.
The mapping of reliable copying to a self-copying replicator is not a superficial analogy; it is the exact physical instantiation of the thermodynamic copying problem, bridging the gap between abstract information theory and mesoscopic physics. When assessing whether any of these emergent systems scale "without bound," the physical reality dictates that all finite-energy, finite-time systems ultimately saturate at a thermodynamic floor. However, by leveraging topological and kinetic architectures, these systems achieve exponential suppression of errors, effectively rendering the reliability unbounded relative to the constraints of the local environment.
The Theorem of Bounded Single Components
To understand why macroscopic systems must invoke complex architectures to achieve high fidelity, it is necessary to establish the physical constraints governing single-component operations. At the molecular and sub-atomic scales, copying is fundamentally limited by thermal noise, rendering perfect copying impossible. The reliability of a copying process is inextricably linked to the entropy it produces and the work it dissipates.
Equilibrium Limits and Non-Equilibrium Saturation
Information processing operates under the constraints of stochastic thermodynamics, where the master equation governs the time evolution of state occupation probabilities across a network of chemical or physical states11. For any templated copying machine—such as a biological polymerase or an artificial nanoscale replicator—the average net rates of incorporating correct () versus incorrect () monomers define the error fraction .
When a copying process operates quasi-statically at thermodynamic equilibrium, the velocity of the copying approaches zero (). In this reversible regime, the error rate is bounded purely by the energetic difference between the correct and incorrect matches. The equilibrium error is given by 1. This represents Bennett’s mechanism of reversible copying. While arbitrary precision is theoretically possible if the energy gap is scaled to infinity, physical systems operate within finite energy landscapes, and the infinite time scales required for reversible copying render it practically useless for dynamic systems1.
To operate at a finite speed, systems must be driven out of equilibrium by expending chemical work. Non-equilibrium protocols can reduce the error far below the equilibrium value, a mechanism famously modeled as kinetic proofreading by Hopfield and Ninio14. Kinetic proofreading leverages free energy (typically via ATP or GTP hydrolysis) to introduce irreversible, dissipative loops into the reaction network. Reaction intermediates that lead to incorrect products are afforded a temporal delay, during which they preferentially unbind before the final, irreversible incorporation step occurs14.
However, this non-equilibrium error correction is strictly bounded. The Thermodynamic Uncertainty Relation (TUR) formulates a rigid trade-off between the precision of a dynamical process, the speed of that process, and the associated entropy production11. Furthermore, universal thermodynamic expressions link the copy error directly with non-equilibrium observables. At a fixed work budget, the error decreases exponentially with the total entropy produced per wrongly copied bit, but this reduction eventually saturates1. The minimum entropy production  generated during the erasure or resetting of the machinery is bounded by Landauer’s principle ()3.
Recent advancements in information thermodynamics extend the dynamical Landauer principle to reveal that the thermodynamic cost of establishing correlations (the essence of copying) implies that transmitting  bits of classical information dissipates energy equivalent to at least 20. The Holevo-Landauer bound further demonstrates that the initial mixedness of a memory component fundamentally limits the ability to create redundancies while preserving the integrity of the copied information21. Consequently, single-component reliability is provably bounded; a single copying step, regardless of the magnitude of energy dissipated, cannot achieve an error rate of zero in finite time1.
The Von Neumann Threshold and the Origin of the Active Paradigm
The recognition that individual physical components are thermodynamically bounded necessitated architectural solutions. This problem was formally addressed by John von Neumann in 1956 regarding the synthesis of reliable organisms from unreliable components23. Von Neumann modeled computation using probabilistic logics where each gate fails independently with probability .
Von Neumann proved that a system built from unreliable components can compute reliably only if  is below a critical threshold. For simple three-input majority gates, this threshold was later formalized by Hajek and Weller, who proved that if , reliable computation is strictly impossible; the probability of error converges to , rendering the output entirely uncorrelated with the input25. The threshold dictates that arbitrary Boolean functions can be computed with a bounded error probability only if the components themselves possess a minimum baseline reliability.
Von Neumann's proposed solution was multiplexing: processing information in redundant bundles where the failure of individual parallel components is overridden by majority consensus23. This foundational theorem birthed the classical engineering orthodoxy that unbounded reliability from noisy components requires redundant encoding followed by active error-correction cycles, such as cyclic redundancy checks and parity bit measurements27.

Thermodynamic and Information-Theoretic Bounds on Single Components
Mechanism and Implication
Reference
Equilibrium Copy Error ()
Error is bounded by the Boltzmann factor of the energy difference between correct and incorrect matches: . Achievable only at zero velocity.
1
Thermodynamic Uncertainty Relation (TUR)
Formalizes the trade-off between process precision, speed, and entropy production. Defines the physical limit to precision for a given amount of dissipation.
11
Dynamical Landauer Principle
Transmitting  bits of classical information requires a minimum of  transmitted energy. Establishes an absolute floor for the mismatch cost in copying.
20
Holevo-Landauer Bound
The mixedness of an initial memory limits the ability to accurately transfer information to redundant components. Entropy production imposes constraints on information accessibility.
21
Von Neumann Error Threshold
Systems built from components with an independent failure probability  can only compute reliably if  is below a critical threshold (e.g.,  for 3-input majority gates).
25

Breaking the Active Correction Paradigm: Quantum Frontiers
The classical von Neumann approach naturally scaled into the quantum domain via Quantum Error Correction (QEC). Quantum information is exceptionally fragile, restricted by continuous environmental decoherence and the no-cloning theorem, which prohibits the deterministic duplication of unknown arbitrary quantum states30. The quantum analogue to classical noise involves both bit-flip and phase-flip errors.
The Orthodoxy of Active Syndrome Measurement
In orthodox QEC architectures, such as surface codes and color codes, logical qubits are encoded non-locally across highly entangled states of many physical qubits. Unbounded reliability is theoretically achievable via the threshold theorem, provided the physical error rate is below approximately  for topological codes31.
However, standard two-dimensional (2D) stabilizer codes exhibit a memory lifetime  at any finite temperature5. Thermal fluctuations create point-like excitations at the ends of string operators. Because these excitations cost no additional energy to separate once created, they freely propagate across the lattice via thermal diffusion, destroying the encoded logical state5. Therefore, these systems require a relentless, active correction cycle:
Ancilla qubits continuously extract parity checks (syndromes) from the data qubits without collapsing the logical state.
The classical syndrome data is routed into an algorithmic decoder (e.g., Minimum Weight Perfect Matching or neural network frameworks).
The classical algorithm calculates the most probable error chain.
Physical feedback operations actively reverse the identified errors31.
This active paradigm is highly resource-intensive. It requires a massive overhead of physical components, continuous energy dissipation to power the classical control electronics, and precisely timed interventions31. The assumption that unbounded reliability requires this active loop stems from the historical inability of low-dimensional quantum systems to sustain topological order at finite temperatures.
Passive Self-Correcting Quantum Memory
The central break in the prompt's claim occurs in the assumption that an active (driven) correction cycle is fundamentally required. A passive self-correcting memory stores information in the ground state of a many-body system and protects it solely through the system's intrinsic equilibrium dynamics when coupled to a thermal bath, requiring no external algorithmic intervention, measurement, or feedback5.
In classical computing, the 2D Ising model acts as a self-correcting memory because flipping a macroscopic magnetic domain requires overcoming an energy barrier that scales with the boundary length, making it thermally stable35. For quantum systems, it has long been established that the 4D toric code is passively self-correcting. Its excitations are extended membrane-like objects that cost energy proportional to their size to deform, yielding a macroscopic energy barrier that naturally suppresses thermal errors33.
However, the existence of a 3D passive self-correcting quantum memory remained one of the most prominent open questions in quantum condensed matter and information theory. Conventional 3D translation-invariant stabilizer codes (such as Haah's cubic code) possess only a logarithmic  energy barrier, resulting in  memory lifetimes due to the existence of string or fractal generators5.
In 2026, Balasubramanian, Davydova, and Lin conclusively resolved this by constructing a 3D Pauli stabilizer Hamiltonian whose ground state encodes a qubit for an exponential time () when coupled to a thermal bath4. The breakthrough bypasses previous no-go theorems by intentionally breaking translation invariance. The mathematical construction applies a sequence of recursive geometric transformations to a seed Hamiltonian, systematically increasing the energy barrier and the memory lifetime while strictly maintaining geometric locality in 5.
This proves that structural geometry and the energetic penalties embedded directly within a system's Hamiltonian can functionally replace active syndrome measurements. The thermal bath itself thermalizes the system back into the code space; the environment serves as the corrective restoring force rather than a disruptive agent38. Passive error correction demonstrates that redundancy need not be explicitly measured to be effective.
Single-Shot Error Correction: A Transitional Paradigm
A transitional architectural step between fully active and fully passive systems is "single-shot" error correction. In single-shot codes—such as the 3D gauge color code and intertwined toric codes—the structural redundancy of the check operators ensures that error syndromes form extended, confined loops32.
Traditional active QEC requires repeated measurements over time to distinguish between physical data errors and measurement errors. Syndrome confinement in single-shot codes allows the system to correct errors using only a single round of noisy measurement data, because any residual noise affects only a bounded, localized number of qubits32. While not fully passive, single-shot codes demonstrate that the topological geometry of the encoding can drastically reduce the required temporal activity and classical processing overhead of the correction cycle.
Emergent Un-Engineered Error Correction: Molecular Frontiers
If quantum mechanics demonstrates that active feedback is not strictly necessary for unbounded reliability, molecular biology and non-equilibrium synthetic chemistry demonstrate that explicit, engineered redundancy (where an identical master copy is multiplexed across multiple isolated channels) is similarly circumventable.
The Error Catastrophe and the Replicator Mapping
The mapping of reliable copying to a self-copying replicator is not a superficial analogy; it is an exact physical instantiation of the thermodynamic copying problem, bridging information theory and statistical mechanics. Biological copying maps exactly to the thermodynamic costs of information transmission, distinguishing between information transmitted by exact copying versus information transmitted by transformation22.
The origin of life and the emergence of replicators present a paradox known as Eigen's error threshold, or the error catastrophe. For a primitive, non-enzymatic replicator to transmit heritable information, the copying fidelity must scale with the length of the genome. If the mutation rate exceeds a critical threshold, errors accumulate faster than natural selection can purge them, leading to total informational decay and a random walk through sequence space7. Early prebiotic copying systems lacked the sophisticated, energy-consuming proofreading polymerases found in modern cells, making the reliable copying of extended polymers physically prohibitive under classical models of chain-growth polymerization7.
The Ecological Architecture of the Virtual Circular Genome (VCG)
The Virtual Circular Genome (VCG) architecture bypasses the error catastrophe through macroscopic ecological dynamics rather than algorithmic redundancy or active proofreading. In a VCG, no single physical molecule encodes the full genetic information. Instead, information is distributed across a highly complex "soup" of overlapping, interacting short segments (e.g., 25-nucleotide DNA or RNA fragments) that map to a virtual circular consensus sequence7. Replication proceeds via thermally-driven, non-enzymatic melt-anneal-extend cycles.
The VCG suppresses mutations profoundly without any active error-recognizing enzymes and without explicit, identical redundancy tracking. The suppression is driven entirely by competition for productive binding partners7.
Distributed Routing and Exhaustive Coverage: Wildtype sequences that perfectly match the consensus overlapping network have numerous reverse-complementary binding partners. This affords them multiple ecological routes to act as either primers or templates8.
Mutational Isolation: A mutant sequence creates a singular, isolated defect in the network. The mutation breaks the hybridization symmetry of the overlapping segments, limiting the mutant's ability to find fully complementary partners8.
Terminal Stalling: When a mutant fragment acts as a primer, the non-complementary base pair (particularly when located near the  terminal end) drastically alters the local thermodynamics. The extension of the polymer past a mismatch incurs an exponential kinetic time penalty ()8.
Ecological Out-competition: Because the system is driven by periodic thermal cycling, fragments have a finite time window () to extend. Stalled mutant sequences fail to extend before the next melting phase occurs. They are marooned as short, non-contributing products. Conversely, wildtype sequences consume the available activated monomers and templates rapidly, out-competing the mutants for resources8.
In the VCG, unbounded reliability emerges from a chaotic pool. The redundancy is not  identical parallel components monitored by a classical logic gate, but rather a distributed mesh of overlapping thermodynamic contexts. The "correction" mechanism is simply the thermodynamic and temporal death of the mutant trajectory.
Ligation Cascades and Prebiotic Proofreading
The classical assumption in polymer copying (chain-growth polymerization) is that errors accumulate linearly with chain length, directly exacerbating the error catastrophe6. As sequence length increases, maintaining high fidelity becomes exponentially more challenging.
However, recent experimental demonstrations by Aoyanagi, Magi, and Toyabe (2025) reveal that replication via templated ligation cascades fundamentally alters this scaling behavior6. In templated ligation, multiple short oligomers bind adjacently on a longer template strand and are covalently joined by a ligase. This cascade replication intrinsically inherits a kinetic proofreading mechanism without requiring a dedicated proofreading exonuclease6.
Because the shorter sub-fragments continuously bind and unbind from the template before the ligation step occurs, any mismatched sequence significantly destabilizes the hybridization free energy ().
The system undergoes multiple evaluations of the matched state before the final, irreversible covalent bond is formed.
Crucially, the experimental data and corresponding simulations demonstrate that in a templated cascade, the error rate decreases as the strand length increases. This diametrically opposes the chain-growth paradigm where errors inevitably accumulate6.
This implies that reliable, long-chain molecular information replication does not require a highly evolved, actively driven enzyme. The structural reaction network of the cascade itself drives the error rate down. While the error rate does not scale to absolute zero (it is mathematically bounded by the non-equilibrium thermodynamic limits of the ligation driving force), it is suppressed effectively without bounds relative to the single-step equilibrium limit, allowing the system to circumvent the error catastrophe6.
Asymmetric Cooperativity and Zero-Extraneous-Energy Proofreading
Further eroding the active-correction claim is the demonstration of non-enzymatic error correction that occurs without an extraneous energy supply. Hopfield's classical formulation of kinetic proofreading assumes the consumption of a secondary, dedicated chemical fuel to drive the discard pathway out of equilibrium14.
Recent theoretical frameworks by Ghosh, Sahu, and Subramanian (2025) demonstrate that the free-energy gradient driving the primary strand growth itself is sufficient to act as the energy source for error correction50. This relies on asymmetric cooperativity—a kinetic asymmetry where a pre-existing base pair (a hydrogen bond) influences the formation or dissociation of neighboring base pairs unidirectionally49.
Under optimal thermodynamic driving forces, the simple catalysis of the phosphodiester covalent bond provides a structural kinetic barrier that naturally filters out incorrect base pairings50. The non-equilibrium drive required for reliability is scavenged directly from the primary polymerization reaction. This negates the need for a dedicated, independently driven "correction cycle" or structurally explicit enzymatic discriminators, demonstrating that persistent molecular order can emerge purely from the thermodynamic gradient favoring strand elongation51.
Synthetic DNA Strand Displacement
The principles of kinetic proofreading have also been successfully engineered into completely synthetic, enzyme-free nucleic acid systems. Research by Ouldridge and colleagues utilizes toehold-mediated strand displacement (TMSD) networks to achieve enhanced molecular recognition54.
In these systems, an invader strand displaces an incumbent strand from a target duplex. By introducing intermediate bound states and utilizing a supply of DNA-based chemical fuel, the system drives the recognition interaction out of equilibrium57. Mismatched base pairs impose position-dependent kinetic barriers that render the branch migration rate-limiting. A single free-energy difference between a correct and incorrect target is exploited multiple times during the displacement cycle55. While this is an engineered system, it proves that the active, algorithmic measurement paradigm of digital computation is not required to harness non-equilibrium thermodynamics for extreme specificity.

Mechanisms of Emergent Error Correction
Primary Modality
Scaling Behavior and Thermodynamic Limits
Reference
Virtual Circular Genome (VCG)
Ecological competition and  terminal stalling during thermal cycling.
Circumvents error catastrophe; mutant propagation is suppressed exponentially as overlapping networks starve isolated errors.
7
Templated Ligation Cascades
Non-equilibrium network evaluation prior to covalent bonding.
Error rate decreases with chain length, breaking the chain-growth accumulation paradigm. Saturates at TUR bounds.
6
Asymmetric Cooperativity
Kinetic asymmetry driven by the free-energy gradient of polymerization.
Achieves high fidelity (e.g.,  error ratios) without extraneous fuel. Catalysis of the phosphodiester bond acts as the filter.
49
Strand Displacement Proofreading
Fuel-consuming TMSD cycles exploiting mismatch kinetic barriers.
Amplifies a single free-energy difference multiple times to achieve super-equilibrium specificity in synthetic networks.
54

The Blind-Field Sweep: What Information Theory Misses
The persistent conflation of unbounded reliability with active redundancy originates from a "blind field" within traditional Shannon communication theory, digital error correction, and early QEC frameworks. These disciplines fundamentally frame information transmission as an algorithmic problem: a source encodes discrete symbols; these pass through a noisy channel; an observer reads the output, computes a syndrome, and applies a targeted corrective operator21.
This discrete, observer-centric framing misses several fundamental physical realities exploited by biological systems, active matter, and topological condensed matter physics.
1. The Thermodynamics of Erasing vs. Discarding
In standard QEC and classical computing, a bit or qubit identified as being in error must be logically corrected, which fundamentally requires erasing the error syndrome from the memory of the ancilla or the controller. By Landauer's principle, this erasure incurs a minimum heat dissipation into the environment18. The system is algorithmically forced to "save" the specific physical carrier and explicitly reset it.
In molecular ecologies (like the VCG) or kinetic proofreading networks, the system does not "correct" the physical carrier; it discards the incorrect assembly pathway entirely. A stalled misincorporation is simply allowed to dissociate back into the monomer pool, or a mutant strand is competitively starved into irrelevance8. There is no Maxwell's Demon calculating a syndrome and expending  to flip a molecule back to the wildtype state. The error is purged via thermodynamic and kinetic exclusion rather than algorithmic correction.
2. Conditioning and Stochastic Resets
This concept of "discarding" is mathematically formalized in the study of non-equilibrium population dynamics through stochastic resets and conditioning—most notably explored in the "Socks-before-shoes" models by Husain, Murugan, Szostak, and colleagues9.
Biological systems execute complex multi-step processes reliably despite massive underlying thermal stochasticity. Rather than employing micromanaging machinery to recognize and correct specific temporal errors, populations use a coarse temporal criterion: any process that takes too long is destroyed (reset) without leaving a physical record9.
In unconditioned ensembles, stochastic trajectories are highly disordered, exploring vast areas of configuration space.
In a conditioned ensemble where incomplete attempts are reset at a threshold time , the surviving population is highly ordered, and the trajectory entropy  is drastically reduced.
Because disordered trajectories (errors) carry a heavy time penalty, they are disproportionately annihilated by the reset mechanism10.
Therefore, selection for speed automatically yields selection for order and fidelity9. This represents a profound shift in understanding biological computation: reliability does not require molecular machinery capable of recognizing specific errors (active correction). It requires only a clock and a mechanism to clear trapped kinetic states10. As Murugan notes, when stalling after misincorporations is accounted for, proofreading can actually speed up replication, suggesting that complex error correction can evolve under selection for speed alone, completely devoid of direct fidelity advantages60.
3. Topological Encoding vs. Repetition Encoding
Classical redundancy relies on repetition codes or polynomial equations, which map well to discrete logic gates but poorly to continuous physical systems. Topological quantum codes map information into global geometric properties. In a 3D passive self-correcting quantum memory, the "redundancy" is not an explicit copy of a qubit stored in an isolated register, but rather the entanglement structure of the entire lattice4. The environment's local thermal noise cannot perturb the global topology without overcoming a macroscopic energy barrier, and the system's own Hamiltonian provides the restoring force. The physical architecture is the error correction.
Nailing the Frontier: Unbounded Scaling vs. Thermodynamic Saturation
To definitively answer the frontier question—whether systems like the Toyabe ligation cascade, the VCG, or 3D passive quantum memories scale without bound, or whether they ultimately saturate—requires a precise definition of "unbounded."
Mathematically and thermodynamically, all physical systems saturate. As established by the bounds derived by Sartori and Pigolotti, any finite-energy, finite-time non-equilibrium system must saturate at a non-zero error rate bounded by its entropy production and dissipation1. Achieving an absolute zero error rate (infinite precision) requires either infinite energy dissipation or infinite time (the quasi-static equilibrium limit)12. In the molecular domain, systems like the Toyabe ligation cascade do not scale to absolute zero error; they saturate at the boundary dictated by the non-equilibrium driving force and the  of the sequence mismatches6.
However, from an information-theoretic and practical standpoint, these systems achieve effective unboundedness through exponential scaling relative to system size.
In the 3D Pauli stabilizer Hamiltonian, the memory lifetime scales exponentially with a fractional power of the system size (). By scaling the physical size of the lattice, the reliability exceeds the age of the universe, rendering it functionally unbounded without requiring algorithmic intervention4.
In the VCG, the exponential time penalty of  stalling combined with the exponential decay of mutant amplification routes pushes the effective error rate well below the catastrophe threshold, allowing the genome to scale to lengths necessary for complex enzymatic function8.
In stochastic resetting, the trajectory entropy is suppressed exponentially as a function of the reset time threshold10.
The frontier of reliable copying demonstrates that systems do not require designed redundancy or a dedicated algorithmic corrector to achieve macroscopic reliability. They require specific thermodynamic, kinetic, and topological geometries that naturally sequester, stall, or penalize errors.
Conclusion
The assertion that single-component reliability is provably bounded stands as an inviolable theorem of stochastic thermodynamics. The energy required to definitively distinguish a correct state from an incorrect one on a component-by-component basis scales unfavorably, enforcing a hard limit governed by the Landauer principle and thermodynamic uncertainty relations.
However, the corollary—that unbounded reliability strictly demands explicit redundancy paired with an active, driven correction cycle—is broken. This claim is a superficial extrapolation of classical computing architectures onto the broader physical universe.
As demonstrated by the 3D passive self-correcting quantum memory, information can be topologically protected such that a thermal bath actively stabilizes rather than decoheres the system. As demonstrated by the Virtual Circular Genome, templated ligation cascades, and stochastic resetting, molecular ecologies can suppress errors profoundly through kinetic stalling, competitive starvation, and temporal conditioning. In these frontier regimes, reliable copying emerges not because a secondary mechanism actively monitors and corrects the primary mechanism, but because the physical, temporal, and geometrical architecture of the system ensures that erroneous states are energetically prohibitive, kinetically stalled, or ecologically out-competed. Unbounded reliability is ultimately an emergent property of network topology and thermodynamics.
Works cited
Thermodynamics of Error Correction - UPC Commons, https://upcommons.upc.edu/bitstreams/0628c32e-3bcd-4595-b6eb-08fe6abe5393/download
Thermodynamics of Classifiers - arXiv, https://arxiv.org/html/2605.24365v1
Minimal Energy Cost for Thermodynamic Information Processing: Measurement and Information Erasure - ResearchGate, https://www.researchgate.net/publication/26721192_Minimal_Energy_Cost_for_Thermodynamic_Information_Processing_Measurement_and_Information_Erasure
[2605.10943] A passive self-correcting quantum memory in three dimensions - arXiv, https://arxiv.org/abs/2605.10943
A passive self-correcting quantum memory in three dimensions - arXiv, https://arxiv.org/pdf/2605.10943
Experimental demonstration of kinetic proofreading inherited in ligation-based information replication - arXiv, https://arxiv.org/html/2505.08232v2
Suppression of errors in collectively coded information - arXiv, https://arxiv.org/html/2508.21806v1
Suppression of errors in collectively coded information - PMC - NIH, https://pmc.ncbi.nlm.nih.gov/articles/PMC12407629/
Kabir Husain's research works | University of Chicago, Chicago (UC) and other places - ResearchGate, https://www.researchgate.net/scientific-contributions/Kabir-Husain-2154942336
Conditioning as a route to stereotyped behavior in growing populations - arXiv, https://arxiv.org/html/2605.13009v1
Stochastic thermodynamics for biological functions - PMC - NIH, https://pmc.ncbi.nlm.nih.gov/articles/PMC12806147/
arXiv:1504.06407v2 [q-bio.SC] 11 Dec 2015 - MPG.PuRe, https://pure.mpg.de/rest/items/item_2257688_4/component/file_3024158/content
The thermodynamics of computation—a review - Academia.edu, https://www.academia.edu/3729801/The_thermodynamics_of_computation_a_review
Speed, dissipation, and error in kinetic proofreading - PNAS, https://www.pnas.org/doi/10.1073/pnas.1119911109
Kinetic proofreading - Wikipedia, https://en.wikipedia.org/wiki/Kinetic_proofreading
Thermodynamic Cost, Speed, Fluctuations, and Error Reduction of Biological Copy Machines - ACS Publications, https://pubs.acs.org/doi/10.1021/acs.jpclett.0c00545
(PDF) Thermodynamics of Error Correction - ResearchGate, https://www.researchgate.net/publication/275527262_Thermodynamics_of_Error_Correction
Landauer Principle and Thermodynamics of Computation - arXiv, https://arxiv.org/html/2506.10876v2
Information-Thermodynamic Bounds on Planetary Biosphere Productivity and Their Observational Tests - arXiv, https://arxiv.org/pdf/2512.07199
Dynamical Landauer principle: Thermodynamic criteria of transmitting classical information, https://www.researchgate.net/publication/394319278_Dynamical_Landauer_principle_Thermodynamic_criteria_of_transmitting_classical_information
Unknown measurement statistics cannot be redundantly copied using finite resources, https://arxiv.org/html/2403.07660v3
Minimal Thermodynamic Cost of Communication - arXiv, https://arxiv.org/html/2410.14920v2
(PDF) Unreliable Systems Built from Reliable Parts - ResearchGate, https://www.researchgate.net/publication/291956995_Unreliable_Systems_Built_from_Reliable_Parts
“Reliable organisms from unreliable components” revisited: the linear drift, linear infinitesimal variance model of decision making - PMC, https://pmc.ncbi.nlm.nih.gov/articles/PMC10482797/
On the Reliability of Computational Structures Using Majority Logic, http://www.ece.ualberta.ca/~jhan8/publications/Majority_proof.pdf
On the maximum tolerable noise for reliable computation by formulas - Information Theory, IEEE Transactions on - Bruce Hajek, https://hajek.ece.illinois.edu/Papers/HajekWeller91.pdf
Computer forensics | Computer Science | Research Starters - EBSCO, https://www.ebsco.com/research-starters/computer-science/computer-forensics
Reliable Computation by Formulas in the Presence of Noise - Scholarship @ Claremont, https://scholarship.claremont.edu/cgi/viewcontent.cgi?article=1574&context=hmc_fac_pub
Covert Channel Data Leakage Protection - Institute for Computing and Information Sciences, https://www.cs.ru.nl/masters-theses/2012/A_Cornelissen___Covert_channel_data_leakage_protection.pdf
No-cloning theorem - Grokipedia, https://grokipedia.com/page/No-cloning_theorem
Fault-tolerant quantum computation by anyons - ResearchGate, https://www.researchgate.net/publication/291787199_Fault-tolerant_quantum_computation_by_anyons
Phase diagram of the three-dimensional subsystem toric code - arXiv, https://arxiv.org/html/2305.06389v2
Single-Shot Quantum Error Correction in Intertwined Toric Codes - OSTI, https://www.osti.gov/servlets/purl/2437659
Ultrametric Quantum Computation - ResearchGate, https://www.researchgate.net/profile/Rowan-Quni-Gudzinas/publication/403473023_Ultrametric_Quantum_Computation/links/69cf5f70ac3812287565fe3f/Ultrametric-Quantum-Computation.pdf
Quantum memory at nonzero temperature in a thermodynamically trivial system - PMC - NIH, https://pmc.ncbi.nlm.nih.gov/articles/PMC11697024/
Self-correcting quantum code | Error Correction Zoo, https://errorcorrectionzoo.org/c/self_correct
A passive self-correcting quantum memory in three dimensions - arXiv, https://arxiv.org/html/2605.10943v1
Quantum Memories Now Hold Data For Vastly Extended Periods, https://quantumzeitgeist.com/quantum-memory-lifetime-extension/
Quantum Computing Modalities: Dissipative QC (DQC), https://postquantum.com/quantum-modalities/dissipative-quantum/
Single-shot code - Error Correction Zoo, https://errorcorrectionzoo.org/c/single_shot
A theory of single-shot error correction for adversarial noise, https://eprints.whiterose.ac.uk/id/eprint/142719/1/1805.09271.pdf
Decomposing information into copying versus transformation - PMC - NIH, https://pmc.ncbi.nlm.nih.gov/articles/PMC7014805/
Effect of Stalling after Mismatches on the Error Catastrophe in Nonenzymatic Nucleic Acid Replication | Journal of the American Chemical Society, https://pubs.acs.org/doi/10.1021/ja100780p
The Virtual Circular Genome Model for Primordial RNA Replication - ResearchGate, https://www.researchgate.net/publication/346031405_The_Virtual_Circular_Genome_Model_for_Primordial_RNA_Replication
Toward Stable Replication of Genomic Information in Pools of RNA Molecules - eLife, https://elifesciences.org/reviewed-preprints/104043/reviews
Suppression of errors in collectively coded information - ResearchGate, https://www.researchgate.net/publication/395125576_Suppression_of_errors_in_collectively_coded_information
Experimental demonstration of kinetic proofreading inherited in ligation-based information replication - arXiv, https://arxiv.org/pdf/2505.08232
Shoichi Toyabe's research works | Tohoku University, Sendai (Tohokudai) and other places, https://www.researchgate.net/scientific-contributions/Shoichi-Toyabe-14312359
Non-enzymatic error correction in self-replicators without extraneous energy supply, https://www.researchgate.net/publication/401046966_Non-enzymatic_error_correction_in_self-replicators_without_extraneous_energy_supply
Non-enzymatic error correction in self-replicators without extraneous energy supply | Request PDF - ResearchGate, https://www.researchgate.net/publication/393120980_Non-enzymatic_error_correction_in_self-replicators_without_extraneous_energy_supply
Non-enzymatic error correction in self-replicators without extraneous energy supply - PubMed, https://pubmed.ncbi.nlm.nih.gov/41724766/
Non-enzymatic error correction in self-replicators without extraneous energy supply | bioRxiv, https://www.biorxiv.org/content/10.1101/2025.06.26.661679v1
After the unzipping of a small section of anti-parallel DNA is... | Download Scientific Diagram - ResearchGate, https://www.researchgate.net/figure/After-the-unzipping-of-a-small-section-of-anti-parallel-DNA-is-complete-beginning-from_fig10_342268922
Kinetic Proofreading Can Enhance Specificity in a Nonenzymatic DNA Strand Displacement Network - PubMed, https://pubmed.ncbi.nlm.nih.gov/38951503/
Design of DNA strand displacement reactions - Spiral, https://spiral.imperial.ac.uk/server/api/core/bitstreams/641e2adc-fa89-436a-a8f5-54a531f3e731/content
Kinetic Proofreading can Enhance Single Nucleotide Discrimination in a Non-enzymatic DNA Strand Displacement Network - bioRxiv, https://www.biorxiv.org/content/10.1101/2023.08.25.554917v1.full.pdf
Kinetic Proofreading Can Enhance Specificity in a Nonenzymatic DNA Strand Displacement Network - PMC, https://pmc.ncbi.nlm.nih.gov/articles/PMC11258683/
Kinetic Proofreading Can Enhance Specificity in a Nonenzymatic DNA Strand Displacement Network | Journal of the American Chemical Society, https://pubs.acs.org/doi/10.1021/jacs.3c14673
Information Flow in Entangled Quantum Systems - ResearchGate, https://www.researchgate.net/publication/2204093_Information_Flow_in_Entangled_Quantum_Systems
Arvind Murugan's research while affiliated with University of Chicago and other places - ResearchGate, https://www.researchgate.net/scientific-contributions/Arvind-Murugan-82250921
Evolution of error correction through a need for speed - Rob Phillips, http://rpdata.caltech.edu/publications/RavasioHusain2026.pdf
Evolution of error correction through a need for speed - ResearchGate, https://www.researchgate.net/publication/400967352_Evolution_of_error_correction_through_a_need_for_speed

model c:
Unbounded Reliable Copying from Bounded, Unreliable Parts: Complete Landscape, Theorems, and Frontier
Executive Summary
The claim that unbounded reliability requires redundancy across many components plus an active, energy-driven correction cycle, and that single-component reliability is provably bounded, is substantially correct as a cross-field theorem when stated with physical premises. It appears independently as von Neumann's threshold for probabilistic logics, Shannon's noisy-channel coding theorem, the quantum fault-tolerance threshold theorem, Eigen's error threshold, and Winfree's proofreading tile sets. In each case, arbitrarily low logical error is achieved only by coding across many physical parts and by suppressing errors faster than they are created through irreversible, dissipative operations.

The mapping to a self-copying replicator is apt, not superficial, provided the replicator is understood as both a constructor and a copier of its own description, as in von Neumann's universal constructor. Biological and synthetic replicators inherit the same trade-offs, with additional constraints from thermodynamics of copying and stalling.

No experimental system to date demonstrates emergent, un-engineered error correction that scales without bound. Frontier systems — Toyabe ligation cascade, DNA strand-displacement proofreading, asymmetric-cooperativity models, kinetic error filtering — show bounded improvements from 10^-2 to 10^-4 or a reversal of length-scaling, but all saturate or require designed redundancy, fuel-driven cycles, or competition. The 2026 result that selection for speed alone can drive the evolution of proofreading explains why such mechanisms appear easily, but does not provide unbounded scaling.

1. The Claim Under Test
"The only route is redundancy across many components + an active (driven) correction cycle; single-component reliability is provably bounded."

This conflates three distinct statements that must be separated:

Bounded single-component reliability: Any physical component operating at finite temperature, finite barrier height, and finite time has non-zero error probability. This is not a purely logical theorem but a thermodynamic statement.
Necessity of redundancy for unbounded reliability: To make logical error arbitrarily small, information must be encoded across many physical degrees of freedom.
Necessity of active, driven correction: Redundancy alone in equilibrium is insufficient; errors must be actively suppressed by dissipative, time-asymmetric operations that remove entropy.
All three are theorems within their domains, but the domains have different assumptions.

2. Foundational Fault-Tolerance Theorems
2.1 Von Neumann Multiplexing (1956)
Von Neumann's "Probabilistic Logics and the Synthesis of Reliable Organisms from Unreliable Components" proved that circuits built from gates that fail independently with probability epsilon < epsilon_th can compute reliably if gates are replicated in large bundles (N-modular redundancy) and majority voting is iterated. The construction requires:

Redundancy factor scaling as O(log (1/delta)) for target error delta
Restitutive majority organ that itself must be reliable enough, leading to recursive construction
Crucially, von Neumann showed that if epsilon > 1/6 for certain gate models, no amount of multiplexing helps — a sharp threshold 1. The result was explicitly for Boolean circuits with independent failures, not for self-replication, but it introduced the threshold concept.

Historical implementations such as N-modular redundancy and M-of-N voting illustrate the practical principle 2.

2.2 Shannon Noisy-Channel Coding
Shannon (1948) proved that for a noisy channel with capacity C, any rate R < C can be achieved with arbitrarily low block error as block length N → infinity, provided encoding introduces redundancy and decoding actively corrects 3. The theorem does not require physical dissipation in its abstract form, but any physical decoder must dissipate.

The key distinction from von Neumann is that Shannon tolerates errors in transmission, not in the encoder/decoder themselves. Concatenating both yields the full computing stack: reliable computation from unreliable gates plus reliable communication from noisy channels.

2.3 Reliability Theory and Thermodynamic Boundedness
Single-component reliability is bounded by:

Thermal activation: error ~ exp(-Delta G / kT). Finite barrier Delta G implies non-zero error.
Landauer and beyond: erasure costs kT ln 2, but reliable erasure with error epsilon requires additional work diverging as log(1/epsilon) under time-symmetric control. Time-asymmetric driving can reduce but not eliminate this 4.
Nonreciprocal logic: modern analyses show that highly reliable computation under time-symmetric protocols must dissipate work proportional to log(1/epsilon) for nonreciprocal gates like AND, far above Landauer 5.
Thus, bounded single-component reliability is a theorem given finite resources, finite time, and finite temperature, but it is a physics theorem, not a logic theorem. In an idealized reversible, zero-temperature, infinite-time model, you could have arbitrarily reliable single components.

3. Quantum Extension: Threshold Theorem
The quantum threshold theorem states that a quantum circuit with p(n) gates can be simulated with error at most epsilon using polylog overhead, provided physical error per gate p < p_th 1. Current surface code estimates put p_th ~1% 1.

Aaronson's summary captures the essence:

"The entire content of the Threshold Theorem is that you're correcting errors faster than they're created." 1

The quantum case reinforces the necessity of both redundancy (n physical per k logical) and active syndrome measurement and correction — a driven, dissipative cycle. No equilibrium quantum memory with finite-range interactions can be self-correcting in 2D; this is a no-go theorem for passive redundancy.

4. Biological Copying: Layered Correction
DNA replication achieves 10^-9 to 10^-11 error per base in E. coli through three layers 6:

Base selection by polymerase: 10^-4 to 10^-5
3'→5' exonucleolytic proofreading: ~100-fold improvement
Post-replication mismatch repair: 100- to 1000-fold improvement to 10^-9–10^-10
Each layer maps to the abstract claim:

Redundancy: not spatial redundancy but kinetic redundancy — the same decision is probed multiple times along a reaction coordinate.
Driven cycle: ATP/GTP hydrolysis drives irreversible exit steps that discard wrong substrates 7.
Hopfield-Ninio kinetic proofreading shows that equilibrium discrimination limited by Delta G can be squared (or N-powered with N steps) only if energy is dissipated in futile cycles 7. The specificity grows exponentially with number of loops, but at cost of speed and dissipation 7.

4.1 Eigen Error Threshold
Eigen's quasispecies model predicts a critical mutation rate q* above which genetic information is lost — error catastrophe 8. For a genome length L, q* ~ ln(sigma)/L where sigma is selective superiority. This is the replication analogue of von Neumann's threshold: unbounded genome length requires error rate scaling as 1/L, i.e., increasing fidelity mechanisms. The result holds for any self-replicator where the constructor also copies itself, leading to error propagation models for both ribosomes and von Neumann probes 8.

5. Algorithmic Self-Assembly
Winfree introduced the kinetic Tile Assembly Model (kTAM), where tiles attach at rate r_f and detach at rate proportional to exp(-b), b = binding strength 9. By setting r_f = r_{r,2} + epsilon, error probability can be made arbitrarily low as epsilon → 0, but at vanishing speed — the passive route.

Winfree and Bekbolatov's proofreading tile sets show the active route: replace each tile by a k×k block with unique internal glues, forcing that any error must involve ≥k coordinated errors. Error probability scales as epsilon^k 10 9. This is:

Redundancy across many components (k^2 tiles per logical tile)
Active correction via reversible detachment — a driven exploration that corrects faster than it locks in errors
Proofreading maintains assembly size (compact schemes have exponential tile-type blowup) but cannot avoid overhead. Hierarchical self-assembly models can achieve absolute error prevention using geometry, but only with additional constraints.

No passive self-assembly without designed block structure shows unbounded error suppression.

6. Distributed Systems and Self-Replication
Byzantine Fault Tolerance (BFT) requires 3f+1 replicas to tolerate f Byzantine faults, employing redundant servers and proactive recovery — migration-based correction to prevent gradual compromise 11. Approximate fault tolerance can be achieved under weaker (f, epsilon)-resilience when exact 2f-redundancy fails 11.

Von Neumann's universal constructor separates description (tape) from constructor (A) and copier (B) 12. This architecture is fragile: most perturbations cause disintegration, and without error correction, probes suffer runaway deterioration independent of software errors 8. The cell solves this by having ribosomes synthesize ribosomes, but with layered proofreading to stay above the error catastrophe threshold.

The mapping to self-copying replicator is apt if you include:

Tape copying error (Shannon)
Constructor execution error (von Neumann)
Phenotypic error propagation (Orgel, Kowald)
It is superficial if you equate a replicator to a noisy channel alone, ignoring that the decoder (polymerase/ribosome) is itself built from noisy parts.

7. Thermodynamics of Copying
Modern work frames copying as a non-equilibrium process. The free energy driving polymerization (Delta G_C) itself can provide error correction without extraneous fuel, but only to a bounded factor.

The 2026 model of non-enzymatic error correction without extraneous energy supply argues that asymmetric cooperativity — kinetic asymmetry where a formed base pair lowers barrier on one side and raises it on the other — can reduce error from thermodynamic baseline ~10^-2 to ~10^-4 using only the drive for strand growth 13. This reproduces stalling, fraying, next-nucleotide effects, and speed-accuracy trade-offs 13.

Importantly, this does not give unbounded scaling. Accuracy exhibits non-monotonic dependence on drive and saturates 13. Achieving beyond ~10^-4 still requires explicit proofreading with additional dissipation.

8. Blind-Field Sweep: What Coding/QEC/Self-Assembly Misses
A coding-centric framing misses at least seven relevant fields:

Field	Contribution to Landscape	Why Missed
Non-equilibrium thermodynamics, TUR	Error-dissipation-speed Pareto fronts; proof that TUR lower bound limits precision per energy 4	Coding theory is energy-agnostic
Control theory, active matter	Feedback stabilization of unstable fixed points requires continuous measurement and actuation	Assumes open-loop coding
Evolutionary dynamics	Selection for speed alone can drive emergence of proofreading without direct selection for fidelity 14	Coding assumes design, not evolution
Reliability engineering, aging	Wear-out, non-independent failures, correlated errors set error floors (~10^-10 in recent surface code memories)	Threshold theorems assume i.i.d.
Condensed matter, passive self-correction	No-go for 2D self-correcting quantum memory; need 4D toric code or long-range interactions	Tile assembly is classical
Neuroscience, fault-tolerant neural nets	Analog error correction codes in grid cells enable reliable computation from unreliable neurons below sharp threshold	Digital gate model
Cryptographic distributed consensus	BFT, proof-of-work show redundancy + active recovery for long-term reliability under adversarial errors	Assumes stochastic not adversarial
The 2026 Science paper is pivotal: "when stalling after misincorporations is accounted for, proofreading can instead speed up replication" and can evolve under selection for speed alone 14. It also generalizes to multicomponent self-assembly where disassembly mechanisms (dynamic instability) emerge to clear kinetically trapped intermediates 15. This inverts the usual cost model — correction is not a tax on speed but a prerequisite for it.

9. Frontier: Do Any Systems Show Unbounded Emergent Correction?
9.1 Toyabe Ligation Cascade
Toyabe et al. (2025) experimentally demonstrate kinetic proofreading inherited in ligation-based information replication. Templated ligation achieves significant error suppression through cascade replication. A key finding: longer chains show lower error rates, distinct from polymerization where errors accumulate 16.

Mechanism: competition between correct and incorrect strands for template binding leads to 7-fold suppression of inferior ligation in presence of competition (reported in tRNA replicator context) 17. However:

Fidelity per domain ~60-62% in minimal tetramer system without competition 17
With competition, improvement is finite, not unbounded
Cascade architecture is designed: template-directed ligation network, not spontaneous
Simulation shows advantage over polymerization but still saturates with length due to kinetic trapping
Verdict: bounded improvement, reversal of scaling trend, but not unbounded. Requires designed redundancy (multiple fragments) and driven cycles (thermal cycling or fuel).

9.2 DNA Strand-Displacement Proofreading
Mukherjee et al. (JACS 2024) implement non-enzymatic proofreading using DNA strand displacement networks fueled by chemical energy, mimicking Hopfield-Ninio 13. Experiments show discrimination factor improves from ~1 to 3-4 fold with proofreader, with leak-limited yield 18. This is engineered proofreading with fuel, not emergent.

Similarly, kinetic error filtering models exploit stalling to filter erroneous strands via limited time windows, reducing yield to improve fidelity 19. Fidelity-yield trade-off can be circumvented via environmental cycles, but only to produce ~50-mers, not unbounded length 19.

9.3 Asymmetric Cooperativity Model
The 2026 Scientific Reports model claims error correction without extraneous energy supply, using only thermodynamic drive 13. It achieves 10^-4, matching passive polymerase base selection, and reproduces experimental signatures. However:

Error rate saturates; cannot approach 10^-9 without exonuclease and mismatch repair
Relies on assumed asymmetric cooperativity — a specific kinetic design, not emergent from random chemistry
Authors explicitly limit scope to base selection; advanced mechanisms lie beyond 13
9.4 Speed-Selected Emergence
The Ravasio et al. Science 2026 result shows that proofreading can evolve from speed selection alone, because stalling makes uncorrected errors slower than correction 15. This provides a route for un-designed emergence under evolutionary dynamics, but:

Result is evolutionary, not thermodynamic: selection must act over populations
Emerged mechanism is still a driven, dissipative proofreading loop — it does not violate the necessity of active correction, it explains its origin
Scaling remains bounded by number of proofreading steps; unbounded scaling would require infinite steps
Summary Frontier Table
System	Error Scaling	Emergent?	Unbounded?	Requires
Toyabe ligation cascade	Error decreases with length (reversal) but saturates ~10^-2–10^-3 per domain	No, designed fragments and thermal cycling	No	Redundancy (multiple oligos) + driven cycle
Strand-displacement proofreading	4-5x improvement, leak-limited	No, engineered network	No	Chemical fuel + designed proofreader
Asymmetric cooperativity	10^-2 → 10^-4	Partial, assumes cooperativity	No	Thermodynamic drive + kinetic asymmetry (designed)
Kinetic error filtering	Enhanced accuracy via time window, yield loss	No, requires cycling	No, limited to ~50-mer	Environmental cycles
Speed-selected proofreading	Can emerge without fidelity selection	Yes, via evolution	No, bounded by steps	Stalling + dissipation + selection
No system demonstrates un-engineered, unbounded error correction. All either saturate or require designed redundancy or dedicated corrector.

10. Evaluation: Theorem or Conflation?
Is single-component reliability provably bounded? Yes, under finite temperature, finite barrier, finite time. Proof follows from Arrhenius / Kramers rate theory and from thermodynamic uncertainty relations. It is not provable from logic alone; an idealized mathematical gate can be perfect.

Is redundancy + active correction the only route to unbounded reliability? Within all established fault-tolerance models — classical (von Neumann), information-theoretic (Shannon), quantum (threshold), evolutionary (Eigen), self-assembly (Winfree) — the answer is yes, with two qualifications:

Redundancy can be temporal (repeated probing) as in kinetic proofreading, not just spatial. But temporal redundancy is still redundancy across many attempts.
Active correction means correcting faster than creation, which requires non-equilibrium drive. Equilibrium error correction (e.g., larger crystal) cannot achieve arbitrarily low error at finite temperature in low dimensions.
Conflation risks: The claim conflates:

Logical necessity (coding theorems) with physical necessity (dissipation). Shannon's theorem does not need dissipation abstractly, but physical implementation does.
Adversarial vs stochastic errors. BFT thresholds differ from random fault thresholds.
Self-replication vs copying. Copying a tape is Shannon; building a constructor that copies itself introduces error catastrophe not present in channel coding.
With these qualifications, the claim is a theorem-schema, instantiated as separate theorems in each field.

Is mapping to self-copying replicator apt? Apt, provided you model three coupled noisy channels:

Transmission of description (genome) — Shannon/Eigen
Execution of constructor (ribosome, 3D printer) — von Neumann
Phenotypic stalling feedback (wrong piece slows next step) — 2026 speed-selection insight 15
A bare analogy "replicator = noisy channel" is superficial because it omits (2) and (3). Full von Neumann architecture captures (1) and (2); adding stalling captures (3).

11. Conclusion: Reframed Landscape
Unbounded reliable copying from bounded unreliable parts is possible, but only via a specific architecture that recurs across scales:

Encode across many parts (spatial multiplexing, block codes, tile blocks, quasispecies cloud, replica ensemble)
Actively correct faster than errors appear (majority voting, syndrome extraction, exonuclease excision, tile detachment, proactive recovery, ligation competition)
Drive the correction out of equilibrium (clock, ATP hydrolysis, fuel, temperature cycling, measurement)
Single-component reliability is bounded by thermodynamics, and passive redundancy alone (e.g., larger equilibrium crystal) does not give unbounded reliability in low dimensions.

Frontier systems that appear to violate this — non-enzymatic error correction without extraneous fuel, ligation cascades with decreasing error with length, proofreading that speeds up replication — are important existence proofs for bounded improvements from minimal physics, and for how dissipative correction can emerge from speed selection. They do not provide unbounded scaling without designed redundancy or fuel.

Thus the original claim is corroborated as a cross-field principle, not refuted, but should be refined to: Unbounded reliability requires (i) encoding over many physical components (in space or time), (ii) an irreversible, energy-consuming correction cycle that operates faster than error accumulation, and (iii) operation below a critical physical error threshold. Single-component reliability is bounded given finite free energy and time.

Sources
1 Wikipedia — Threshold theorem
2 Stanford CS — Fault Tolerant Computing: How?
3 Wikipedia — Noisy-channel coding theorem
4 arXiv — The thermodynamic cost of reliability and low temperatures: Tightening Landauer's principle and the Second Law
5 Nature Communications — Dissipative quantum error correction and application to quantum sensing with trapped ions
6 PMC — The 3′→5′ Exonucleases of DNA Polymerases δ and ɛ and the 5′→3′ Exonuclease Exo1 Have Major Roles in Postreplication Mutation Avoidance in Saccharomyces cerevisiae
7 Wikipedia — Kinetic proofreading
8 arXiv — Why is there no von Neumann probe on Ceres?
9 CACM — Theory of Algorithmic Self-Assembly
10 Caltech Authors — Proofreading Tile Sets: Error Correction for Algorithmic Self-Assembly
11 CSU — Byzantine Fault Tolerance for Distributed Systems
12 Wikipedia — Von Neumann universal constructor
13 Scientific Reports — Non-enzymatic error correction in self-replicators without extraneous energy supply
14 UCL Discovery — Evolution of error correction through a need for speed
15 Science — Evolution of error correction through a need for speed
16 arXiv — Experimental demonstration of kinetic proofreading inherited in ligation-based information replication
17 eLife — tRNA sequences can assemble into a replicator
18 bioRxiv — Kinetic Proofreading can Enhance Specificity in a Non-enzymatic DNA Strand Displacement Network
19 ResearchHub — A kinetic error filtering mechanism for enzyme-free copying of nucleic acid sequences


