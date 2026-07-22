# Outbound research prompt — can a discrete stacking-order (or topological) Z₂ state be **copied across a separation with closure**? (the closure gate)

> **SUPERSEDED IN ORIENTATION (2026-07-21).** The closure-gate question this prompt's spine asks is **answered** — a clean negative, filed in [`report_closure-gate-z2-heritability.md`](report_closure-gate-z2-heritability.md) (stacking-order Z₂ passes everything *except* strong closure; fidelity lives in the bath, so it sorts, it does not bootstrap). **Do not re-run this prompt as written** — a model will only re-confirm the negative. The live outbound question is now the **rescue path** (Q8 below, currently buried last): *what is the minimal addition that puts copying-fidelity **on the tape** — sequence-encoded affinity, or a driven-multistable bit — without amounting to reinventing full base-pairing?* If another round is commissioned, rewrite with that as the spine and cite this negative as settled context (as this prompt already does for the chirality negative). Kept verbatim for the record.

*Clean v2, 2026-07-21. Round 1's returned answers are filed in [`report_closure-gate-z2-heritability.md`](report_closure-gate-z2-heritability.md) — check it before re-commissioning. The text **below the horizontal rule** is the self-contained outbound prompt; everything above the rule is a note to the operator, **not** part of what the research model is asked to do. (v1 leaked operator notes into the prompt body, which caused some models to "do a status check / rewrite the brief" instead of answering — those instructions are kept out of the prompt this time. v2 also strips the pre-loaded conclusion so a re-run is an independent check, and names the weak/strong-closure distinction that round 1 showed to be the crux.)*

---

## Context (self-contained — you are an outside model with no prior session context)

We are building a thin physical model called **thermal-phosphor**: a driven, mass-carried medium (granular matter / layered deposition — grains, gravity, agitation, jamming, stacking) that we want to assemble, step by step, into a **self-templating replicator**, handing off to Darwinian evolution once selection on heritable variation takes over. We are trying to locate the **single hardest physical step**, and we think it is now isolated: **closure.**

We model the replicator as a minimal **von-Neumann-style circuit** (constructor and tape are the *same object*): a row of monomers ("sticks"), each carrying **≥2 discrete states at the moment of contact**; a blank row laid alongside copies the sequence **by contact** (templated complementarity — base-pairing with the chemistry filed off); the two rows are pulled apart; each copy is *itself* a row of sticks, so it templates the next with **no adapter**; and because the copier is encoded in the sticks it copies, fidelity can **bootstrap** — a better-copying variant copies itself better — as long as it stays above the **Eigen error threshold** (≈ *N*·(1−*q*) < 1 for length *N*, per-unit fidelity *q*).

A prior round **closed the chirality route** (take as given, do not re-litigate): a rank-2 inertia/fabric tensor cannot encode a pseudoscalar; driven achiral grains give a *nematic*, not chiral, fabric; chiral "heredity" in crystals is surface-kinetic, not bulk memory; parity symmetry forecloses minting a chiral sign from achiral parts. So we have pivoted to a *different* discrete-Z₂ realization native to a layered, mass-carried medium: **stacking-order parity** (fcc-like ABCABC vs hcp-like ABAB; stacking-fault parity; polytypes), with **topological mechanical polarization** (Kane–Lubensky isostatic lattices) as a second candidate.

**The bar is deliberately modest — not "protected forever."** The state need only be (1) **discrete at the moment of contact** and (2) **metastable over one generation** (survive from being laid down to templating the next layer). A shallow, shabby "click" is in-bounds; a continuous smear with no discrete value to be right or wrong about is out. Long-term protection is something the system can *evolve toward later* — it is not a precondition.

## The decision — a hereditary channel must satisfy **all** of the following at once

| Requirement | Pass condition |
|---|---|
| **Discrete state** | two distinguishable states at contact (Z₂ suffices) |
| **One-generation metastability** | survives long enough to template the next layer |
| **Contact templating** | existing structure biases the corresponding state in adjacent blank material |
| **Weak closure** | output-is-input: the copied row can itself act as template with **no separate read-head / adapter** |
| **Strong closure** | the **copying fidelity itself** is inherited *on the copied object* — a better-templating variant templates **itself** more faithfully, so improvement is **stored on the sequence**, not in the growth apparatus, fields, catalysts, dislocation lines, or environment |
| **Survives separation** | stays discrete through fracture / cleavage / budding / pinch-off |
| **Above Eigen threshold** | error stays below *N*·(1−*q*) < 1 across generations |

**Passing most-but-not-all is a failure.** The distinction we care about most is **weak vs strong closure**: weak closure (no adapter) is necessary but cheap; **strong closure** (fidelity riding on the tape, so it can *bootstrap* rather than merely be *sorted*) is the hard one, and it is the whole question. A channel that only lets selection *sort a standing population* — without *storing* the improvement on the copied object — does **not** bootstrap.

## Questions (distinguish established result / plausible interpretation / speculation / open; cite fields and papers)

**Q1 — Discreteness + one-generation metastability.** In close-packed or layered assemblies (granular, colloidal, crystalline), is the local stacking state (ABCABC vs ABAB; stacking-fault parity) genuinely **discrete at the growth front** and **metastable long enough to be templated onward**? What sets that lifetime (stacking-fault energy, kinetic sliding barrier, confinement, jamming, temperature, deposition rate, defect pinning)? Permanence is not required — one successful templating event suffices.

**Q2 — Contact templating.** Is there an established mechanism by which a stacking sequence **imposes its own continuation** on newly deposited material *by contact*? (Epitaxial / layer-by-layer templating; Frank screw-dislocation polytype growth in SiC and ZnS; colloidal epitaxy.) Separate **genuine transmission** of the state into previously blank material from **mere persistence** of an already-set stack that does not propagate its state to a neighbour.

**Q3 — Closure (the critical question).** Split it explicitly:
- **(a) Weak closure.** Can the copied row itself serve as a template with no separate read-head / adapter, or does turning a grown sequence back into a template require distinct machinery?
- **(b) Strong closure.** Does the *copying fidelity* become copied along with the sequence — i.e. does a better-templating motif template **itself** more faithfully, so improvement is **stored on the sequence**? Or is fidelity always set by information residing elsewhere (growth front, supersaturation, temperature, catalyst, dislocation network, substrate, boundary conditions, kinetic environment)? We need strong closure because bootstrapping requires **stored, heritable** fidelity; pressure that only *sorts* does not qualify.

**Q4 — Survival through separation.** After a layer is templated, the model **pulls the two regions apart** (budding / pinch-off / fracture / detachment). Does an established stacking or topological state **stay discrete through such a separation**? Is there a **timing constraint** (copy must complete before separation)? Evidence from cleavage, exfoliation, delamination, grain separation, fragmentation — and cases where separation *scrambles* the state.

**Q5 — Topological mechanical Z₂ (second candidate).** (a) Do jammed / isostatic (Maxwell) packings carry a **Kane–Lubensky Z₂ polarization** that is discrete and could be transmitted into a forming region — or does it reduce to a *polar* (favored-direction) quantity a drive continually re-sets? (b) Does copying it across many layers stay above the Eigen threshold, or wash out?

**Q6 — Information localization.** For every viable candidate, state **where the hereditary information physically resides** at each phase: (1) before contact, (2) during contact, (3) immediately after copying, (4) after separation. Does the information ever reside **outside the copied object** (growth front, defect network, catalyst, field, substrate, environmental gradient) and have to be recovered from the environment? If so, does that break strong closure?

**Q7 — Fidelity and the Eigen threshold.** Can a viable candidate stay above *N*·(1−*q*) < 1 across many generations, or does error accumulate until information washes out (error catastrophe)? Is there a parameter regime where fidelity is high enough for heritable *improvements in copying* to accumulate — and can *q* be **climbed from the tape**, or only sorted? Distinguish demonstrated fidelity / theoretical estimate / qualitative expectation / unknown.

**Q8 — If strong closure fails: the minimal rescue.** *If* the honest verdict is that fidelity lives off the tape, what is the **minimal** addition that would put *q* **on** the tape — e.g. sticks with side-affinity that depends on local stacking parity, so sequence encodes binding energy? Is there a version that achieves stored heritable fidelity **without** amounting to reinventing full base-pairing / molecular chemistry — i.e. how much chemistry is *forced*, and can it still be read as "a layered medium plus one affinity bit" rather than "import DNA"?

## Output wanted

One **unified synthesis** (not a per-model dump). For each candidate mechanism, a decision table:

| Criterion | Verdict |
|---|---|
| Discrete state? | Yes / No |
| One-generation metastability? | Yes / No |
| Contact templating? | Yes / No |
| Weak closure (no adapter)? | Yes / No |
| Strong closure (fidelity on the copied object)? | Yes / No |
| Survives separation? | Yes / No |
| Above Eigen threshold in principle? | Yes / Probably / Unknown / No |
| **Overall** | **PASS / FAIL** |

Then answer directly:

> **Can a driven, layered, mass-carried medium copy a discrete stacking-order (or analogous topological) state across a physical separation by contact, while the copying fidelity itself rides on the copied sequence (strong closure), giving a bootstrappable hereditary channel above the Eigen error threshold?**

If **no**, state plainly where the argument fails and where the fidelity actually lives. If **yes**, name the mechanism that satisfies strong closure, how fidelity is inherited, what limits the error rate, and the evidence. **A clean negative is exactly as valuable to us as a positive — do not soften it.**
