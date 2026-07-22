# Challenge — a driven copier whose copying fidelity rides on its own tape

Build the smallest **driven copying system** in which the *copying fidelity is encoded in the copied sequence itself* and *vanishes when the drive is switched off*.

Background: kinetic proofreading (Hopfield 1974; Ninio 1975) shows that a thermodynamic drive can lift copying fidelity above its equilibrium value, and that this enhancement relaxes when the drive stops. In known proofreading the fidelity is set by fixed rate constants — it does not depend on the sequence being copied. This challenge asks for the proofreading capacity to be **part of what gets copied**, so that a better‑copying variant copies *itself* better (von Neumann's constructor–tape unity) and a lineage can climb past the Eigen error threshold. In one grid, the target is the lower‑right corner:

| | fidelity **not** drive‑elevated | fidelity drive‑elevated |
|---|---|---|
| fidelity **sequence‑independent** | crystal / ROM — sorts a fixed population | standard proofreading — sorts a fixed population |
| fidelity **sequence‑encoded** | — | **the target — a lineage that can climb** |

## What to build (object grammar)

A construction is a tuple `(S, N, c, A, W)`:

- `S` — a finite monomer alphabet, `k = |S| ≥ 2`. A **tape** is a string in `Sᴺ`.
- `c : S → S` — the intended copy map (what a faithful daughter site holds, given the template site).
- `A ≥ 0` — a single scalar **drive affinity**: the net thermodynamic force cycling the copy machinery. `A = 0` is detailed balance.
- `W(A; T)` — the generator (continuous‑time rate matrix / master equation) of the templated copy dynamics on template tape `T` at drive `A`. From `W`, compute:
  - `qᵢ(T; A)` — probability the daughter site `i` equals `c(Tᵢ)` at read‑out (steady state or first passage);
  - `Q(T; A)` — the per‑site fidelity governing register persistence, defined as `minᵢ qᵢ(T; A)`.

A driven cellular automaton or a templated chemical‑reaction network is an acceptable encoding, provided it presents these same computable objects.

## Acceptance — your construction qualifies iff all of C0–C5 hold

**C0 — no privileged machinery.** `W` is a single rate function applied identically at every site. The transition rates at a site **may** depend on the monomer states within a fixed, bounded window around it — and on nothing else: not on the site's absolute position, not on any global label, not on any designation of some region as "the copier." The same function acts everywhere, blind to which substring (if any) turns out to carry the fidelity.
  - **Permitted:** rates that vary with *local monomer content*, so some sequences copy better than others under the one rule. *(A rule that slows incorporation whenever the two template neighbors are both in state `1` is fine — it reads local content, uniformly, everywhere.)*
  - **Forbidden:** a rate switched by *which region* it is in, or by a named "copier" substring; or a monomer type or interaction that exists only to serve copying. *(A rule that slows incorporation "inside the copier gene at positions 5–9" is not allowed — it reads a designated region.)*
  - **Processivity — permitted if emergent, forbidden if postulated.** Directional growth or folding that *emerges* from the one local rule (a site may lock only once its neighbor has locked; complementary monomers latch and bring sequence-distant sites into contact) is in-bounds — constructor–tape unity. A postulated read-head or catalyst that grabs the tape and *slides* along it is not: any processivity must fall out of the local rule, never be a machine added on top.

  So a "copier" is never a machine that reads the tape — it is whatever local motif, under this one uniform rule, happens to raise `Q`.

**C1 — discrete & templated.** Read‑out is discrete (`daughterᵢ ∈ S`, not an average) and templated (`qᵢ(T;A)` depends on `Tᵢ`).

**C2 — on the tape.** `Q` depends on the tape: exhibit two equal‑length tapes `Tₐ, T_b` with `Q(Tₐ;A) ≠ Q(T_b;A)`, the difference arising from the monomer content of the tapes — not from `A` or any external parameter.

**C3 — carried by the drive.** At `A = 0` the tape's control of fidelity vanishes: `Q(T;0)` is independent of tape content — it collapses to the equilibrium value set by the fixed local energetics (`1/k` if there is no equilibrium discrimination at all). Fidelity can rise above equilibrium *only by spending the drive*. Show this as an identity from detailed balance, not a sampled estimate.

**C4 — heritable & above the bar.** (a) The high‑fidelity substring is copied by the same dynamics — it is part of `T`, read by the same rule, with no separate machinery. (b) A variant of it gives strictly higher `Q`. (c) The achieved `Q` admits `N ≥ 2` with `N·(1 − Q) < 1` (a length‑`N` register persists a generation; `N = 2` needs `Q > ½`).

**C5 — capacity on the tape** *(no off‑tape ceiling).* The fidelity attainable is not bounded above by any constant the rule fixes independently of the tape: for every target `q* < 1`, some tape achieves `Q ≥ q*`, with the higher fidelity bought by a longer or richer copier‑substring — not by a bath constant. Equivalently `sup_T Q = 1`. *Rejects a construction where the tape only tunes fidelity within a fixed window whose ceiling is set off‑tape — a fidelity knob, not a fidelity capacity (the subtle re‑appearance of the stacking‑order failure: a single clamp motif saturates at a fixed discrimination and stops).*

## Constraints

Use only: discrete‑state monomers, contact templating, the drive `A`, metastability (a latch), and separation (a pinch). Minimize `k`, the number of distinct rate parameters, and the length of the fidelity‑bearing substring. A construction that qualifies with the fewest, simplest parts is the strongest answer.

## Known non‑qualifying constructions

- A crystal / read‑only store — fails **C3** (it discriminates cold, with no drive).
- Standard kinetic proofreading, or a stacking‑order / polytype record — fails **C2** (`Q` is set off the tape).
- A copier‑substring read by a programmable catalyst that sets the rates — fails **C0** (sequence‑addressed machinery).
- A single clamp/proofreading motif whose fidelity saturates at a ceiling fixed by an off‑tape constant (a bounded *knob*) — fails **C5** (`sup_T Q < 1`).

## Deliverable

Provide, explicitly and as small as you can:

- the tuple `(S, N, c, A)` and `W` written out as its explicit local rate function;
- the fidelity‑bearing substring;
- the computations of `Q(Tₐ;A)`, `Q(T_b;A)`, and `Q(T;0)`;
- the higher‑`Q` variant and its `Q`;
- the `N` meeting the Eigen margin.

Every number must be hand‑checkable from the rule. The object is the answer; no prose proof is required.

If you cannot satisfy every condition, do not revise the challenge — state which condition (C0–C5) blocks you, and why.

## How your answer will be checked

Recompute `qᵢ` and `Q` from your generator; confirm `W` is local and uniform (**C0**); verify **C2** by swapping tape content; verify **C3** by setting `A = 0` and confirming tape‑independence as an identity; verify **C4** by locating the variant and the `N`; verify **C5** by checking that higher fidelity requires only a longer or richer copier‑substring, with no rule‑fixed ceiling below 1.
