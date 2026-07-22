# Challenge (folding, v0) — a self-folding copier whose fidelity *capacity* rides on its own sequence

Same target as the 1-D challenge: a driven copier whose copying fidelity is **encoded in the copied sequence** and **vanishes when the drive is cut**. New ingredient: the copier may **fold**. Folding is the one thing that lets a *bounded* local interaction reach an *unbounded* stretch of sequence — by bringing sequence-distant monomers into spatial contact — which is exactly what an *improvable* fidelity needs. (The 1-D version proved sequence-encoded, drive-carried fidelity is real, but showed its capacity caps at ~`d²`: a single proofreading stage is all a 1-D neighborhood can provide. Only folding stacks more.)

Answer with a **witness, not an argument** — an explicit construction that passes a mechanical oracle. If you cannot satisfy every condition, name the one that blocks you; do not revise the challenge.

## The arena (object grammar)

- **Lattice.** Monomers occupy sites of the 2-D square lattice (integer coordinates). *(Use the 3-D cubic lattice only if the mechanism provably needs more than 4 contacts per site; state which.)*
- **The chain.** A tape of length `N` is a **self-avoiding walk**: monomers `1…N`; consecutive monomers on adjacent sites (unit distance); **no two monomers on the same site** (hard no-overlap).
- **Alphabet.** `S`, `k = |S| ≥ 2`. `c : S → S` the intended copy map.
- **Contacts (this is where folding works).** Two monomers that are **lattice-adjacent but not sequence-adjacent** form a *contact*. A contact lets a sequence-distant monomer sit next to a growth site.
- **Drive.** Scalar affinity `A ≥ 0`; `A = 0` is detailed balance.
- **Generator `W` — spatially local and uniform.** One rate function applied identically everywhere. A transition's rate may depend only on the monomer states within a **fixed bounded spatial neighborhood** (lattice-distance ≤ `r`, small fixed `r`) of where it acts — and on nothing else: not absolute position, not sequence-index, not a named region. **Folding must itself emerge from `W`** (complementary monomers latch when they come into contact); it is never imposed by hand, and there is no read-head that slides the tape.
- **Copy dynamics.** A daughter chain is grown against the template; per-site fidelity `qᵢ = P(daughterᵢ = c(Tᵢ))` at read-out; `Q = minᵢ qᵢ`.

## Deliverable

For a specific tape, give — all hand-checkable:
- the sequence **and its explicit folded coordinates** (so overlap and contacts can be verified by hand);
- `W` as its explicit local rate function over spatial neighborhoods;
- `Q(Tₐ; A)`, `Q(T_b; A)`, `Q(T; 0)`;
- a higher-`Q` variant and its `Q`;
- the `N` meeting the Eigen margin.

## Acceptance — qualifies iff all hold

**G — valid geometry.** The folded configuration is a genuine self-avoiding walk (consecutive monomers adjacent; no two monomers share a site); every claimed contact is an actual lattice-adjacency.

**C0 — spatially-local, no privileged machinery.** `W` is one uniform rate function of a bounded spatial neighborhood. Folding emerges from `W`; no imposed structure, no sliding read-head, no monomer or interaction existing solely to serve copying.

**C1 — discrete & templated.** Read-out is discrete; `qᵢ` depends on `Tᵢ`.

**C2 — on the sequence.** `Q` depends on sequence content (exhibit two tapes with different `Q`).

**C3 — carried by the drive.** At `A = 0`, `Q` is sequence-independent (collapses to the equilibrium value; `1/k` if no equilibrium discrimination); fidelity rises above equilibrium *only by spending drive*. Show as a detailed-balance identity.

**C4 — heritable & above the bar.** (a) The folded copier is copied by the same dynamics — no separate machinery. (b) A variant gives strictly higher `Q`. (c) `N ≥ 2` with `N·(1 − Q) < 1`.

**C5 — unbounded capacity by independent stages.** For every `q* < 1`, some sequence folds into a pocket achieving `Q ≥ q*`, the higher fidelity bought by a **larger/richer folded copier** — not a rule constant. **Each fidelity increment must be a distinct, independent, irreversible driven discard contributed by a distinct contact in the pocket** (a real proofreading stage). A *delay* does not count: a longer dwell merely equilibrates to single-stage discrimination and saturates. The check is: count the stages, confirm each is a separate driven discard from a separate contact, and confirm the count scales with the folded copier without a rule-fixed ceiling.

## Known non-qualifying constructions

- Any 1-D construction (no folding) — caps at ~`d²`, **fails C5**. *(This is the whole reason for folding.)*
- A downstream-gated **delay line** — saturates at single-stage discrimination, depth-independent, **fails C5**.
- A **sliding read-head** or postulated catalyst — **fails C0**.
- A folded configuration with **overlaps or fictitious contacts** — **fails G**.
- A **cold** copier that discriminates at `A = 0` — **fails C3**.

## How your answer will be checked

Verify **G** from the coordinates (walk self-avoiding, contacts real); recompute `qᵢ` and `Q` from `W` over the spatial neighborhoods; confirm **C0** uniform + spatially-local, folding emergent; **C3** by the `A = 0` identity; **C2** by swapping sequence; **C4** by locating the variant and `N`; **C5** by counting the independent driven-discard stages, checking each comes from a distinct contact, and that the count grows with the folded copier with no rule-fixed ceiling.

*(v0 caveat for the operator, not the solver: hand-checkability is the make-or-break here — keep lattices small and coordinates explicit. If solvers hallucinate overlaps or fictitious contacts, that is the LLM spatial-reasoning ceiling, and finding it fast is itself the result.)*
