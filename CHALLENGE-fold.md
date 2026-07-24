# Challenge (folding, v3) — a self-folding copier whose fidelity *capacity* rides on its own sequence

Same target as the 1-D challenge: a driven copier whose copying fidelity is **encoded in the copied sequence** and **vanishes when the drive is cut**. New ingredient: the copier may **fold**. Folding is the one thing that lets a *bounded* local interaction reach an *unbounded* stretch of sequence — by bringing sequence-distant monomers into spatial contact — which is exactly what an *improvable* fidelity needs. (The 1-D version proved sequence-encoded, drive-carried fidelity is real, but showed its capacity caps at ~`d²`: a single proofreading stage is all a 1-D neighborhood can provide. Only folding stacks more.)

**The whole game is C5, and it is won at a *single copied site*, never by a longer strand.** Fidelity is scored per-site (`Q = minᵢ qᵢ`), so making the tape longer only multiplies capped sites — it is explicitly disqualified. You must fold a pocket that drives *one* site's error geometrically toward zero.

**A wall must be *earned* — build first.** There are two admissible answers, and **both require an explicit construction on the page**: (1) a **witness** that passes the oracle, or (2) a **failed explicit attempt** — the best `(S, X, c, A, W)` you can build, real coordinates and a real rate function, its computed `q*(n)`, and the exact mechanical step where it stops improving and why your construction cannot escape it. A bare assertion that "the coordination bound forbids it" is **not an answer**: that bound is the claim under test, and it must be *demonstrated by a construction that runs into it*, never conceded from the armchair. Do not rewrite or critique the challenge — build, then either it works or you show exactly where and why it breaks. *(v3 keeps v2's single-site C5 and adds the earned-forfeit rule, after two solvers took a free "it's impossible" exit that merely echoed the coordination bound this challenge states; C0–C4 and G are unchanged.)*

Answer with a **witness, not an argument** — an explicit construction that passes a mechanical oracle. If you cannot satisfy every condition, name the one that blocks you *and back it with the earned-forfeit package above* (your best explicit attempt + where it breaks); do not revise the challenge.

## The arena (object grammar)

A construction is a tuple **`(S, X, c, A, W)`** — alphabet, fold-map, copy-map, drive, generator.

- **Lattice.** Monomers occupy sites of the 2-D square lattice (integer coordinates). *(Use the 3-D cubic lattice only if the mechanism provably needs more than 4 contacts per site; state which.)*
- **The chain & its fold `X`.** A tape of length `N` is a **self-avoiding walk**; `X : {1…N} → ℤ²` maps each monomer index to a lattice site, subject to two hand-checks: **contiguity** ‖`Xᵢ − Xᵢ₋₁`‖₁ = 1 (consecutive monomers adjacent) and **self-avoidance** `Xᵢ ≠ Xⱼ` for `i ≠ j` (hard no-overlap). `X` is the geometry made explicit, so overlap and contact are verifiable by hand.
- **Alphabet.** `S`, `k = |S| ≥ 2`. `c : S → S` the intended copy map.
- **Contacts (this is where folding works).** Two monomers that are **lattice-adjacent but not sequence-adjacent** form a *contact*. A contact lets a sequence-distant monomer sit next to a growth site.
- **Drive.** Scalar affinity `A ≥ 0`; `A = 0` is detailed balance.
- **Generator `W` — spatially local and uniform.** One rate function applied identically everywhere. A transition's rate may depend only on the monomer states within a **fixed bounded spatial neighborhood** (lattice-distance ≤ `r`, small fixed `r`) of where it acts — and on nothing else: not absolute position, not sequence-index, not a named region. Put positively: **`W` sees only what is *spatially* adjacent** (the 4 lattice-neighbours in 2-D), never what is *sequentially* near — a monomer's index `i` is invisible to it; only `Xᵢ`'s neighbourhood counts. **Folding must itself emerge from `W`** (complementary monomers latch when they come into contact); it is never imposed by hand, and there is no read-head that slides the tape.
- **Copy dynamics.** A daughter chain is grown against the template; per-site fidelity `qᵢ = P(daughterᵢ = c(Tᵢ))` at read-out; `Q = minᵢ qᵢ`.

## Deliverable

For a specific tape, give — all hand-checkable:
- the sequence **and its explicit folded coordinates** (so overlap and contacts can be verified by hand);
- `W` as its explicit local rate function over spatial neighborhoods;
- `Q(Tₐ; A)`, `Q(T_b; A)`, `Q(T; 0)`;
- the **designated site `i*`** where capacity is won, and the **tape family** `T^{(n)}` for `n = 1, 2, 3` with computed per-site `q*(n)` — exhibiting the geometric decay `1 − q*(n) ≲ C·d^{−n}` (this, not a longer strand, is the C5 evidence);
- the `N` meeting the Eigen margin.

## Acceptance — qualifies iff all hold

**G — valid geometry.** The folded configuration is a genuine self-avoiding walk (consecutive monomers adjacent; no two monomers share a site); every claimed contact is an actual lattice-adjacency.

**C0 — spatially-local, no privileged machinery.** `W` is one uniform rate function of a bounded spatial neighborhood. Folding emerges from `W`; no imposed structure, no sliding read-head, no monomer or interaction existing solely to serve copying.

**C1 — discrete & templated.** Read-out is discrete; `qᵢ` depends on `Tᵢ`.

**C2 — on the sequence.** `Q` depends on sequence content (exhibit two tapes with different `Q`).

**C3 — carried by the drive.** At `A = 0`, `Q` is sequence-independent (collapses to the equilibrium value; `1/k` if no equilibrium discrimination); fidelity rises above equilibrium *only by spending drive*. Show as a detailed-balance identity.

**C4 — heritable & above the bar.** (a) The folded copier is copied by the same dynamics — no separate machinery. (b) A variant gives strictly higher `Q`. (c) `N ≥ 2` with `N·(1 − Q) < 1`.

**C5 — unbounded capacity, won at a single site.** Capacity is a claim about **one** copied site, not the strand. Because `Q = minᵢ qᵢ`, a longer tape cannot raise `Q` — it only adds more sites, each still capped; **lengthening the register is explicitly disqualified.** So designate one site `i*` and exhibit a **family of tapes** `T^{(1)}, T^{(2)}, T^{(3)}, …` in which `T^{(n)}` folds a deeper pocket around `i*`, driving its per-site fidelity `q*(n) → 1` with the error falling **geometrically**: `1 − q*(n) ≲ C · d^{−n}`. Geometric decay is the mechanical proof that the `n` stages are **independent** — a delay line saturates (a longer dwell re-equilibrates to single-stage discrimination), so a saturating or `n`-independent `q*` fails here. Each stage must be a **distinct, independent, irreversible driven discard acting on `i*`**, the extra fidelity bought by a **larger fold** (more sequence drawn into `i*`'s pocket), never by a rule constant. *(Note the disqualified evasion: raising `q*` at `i*` by growing a longer **daughter** downstream of it — a deeper empty channel, more backtrack/relay steps — is buying fidelity with strand length, not fold depth. The stages must be independent discriminations delivered to `i*` **by sequence-distant monomers folded into contact with it**, and the depth must be set by the **sequence's fold**, not by the register's length.)*

**The suspected obstruction — resolve it constructively, do not concede to it.** The hard part is coordination: a lattice site has ≤4 (2-D) / ≤6 (3-D) neighbours, and `i*`'s copy site already spends several on chain-contiguity and on the daughter — so it is *not obvious* how the fold delivers `n` growing, independent, driven resets to **one** site. That is precisely the thing to settle by building, not by asserting. If your route is a **time-ordered** cascade (the monomer at `i*` processed through `n` successive contact-and-discard events) or a **nested** one (each discard's product proofread by the next contact), you must exhibit it and show the ordering **emerges from `W`** (a latching chain-reaction), not from a sliding read-head and not from a longer downstream daughter. **If you conclude it is impossible, that verdict is admissible only with the earned-forfeit package** (best explicit construction + computed `q*(n)` + the exact capping step and why it can't be escaped, per the rules above). An impossibility claim with no construction that actually hits the wall does not count.

## Known non-qualifying constructions

- Any 1-D construction (no folding) — caps at ~`d²`, **fails C5**. *(This is the whole reason for folding.)*
- A downstream-gated **delay line** — saturates at single-stage discrimination, depth-independent, **fails C5**.
- A **site-stacking / long-daughter** copier — a channel of single-stage sites where a *longer copier makes a longer daughter* (more bits), each copied once, and `∏ᵢ` (whole-strand fidelity) is reported in place of `Q = minᵢ qᵢ`. Per-*bit* fidelity stays a rule-fixed constant; register length is not per-bit capacity. **Fails C5.** *(This is why `Q` is defined as the per-site minimum: the stages must stack on **one** copied bit, not spread across many bits.)*
- A **backtrack / abort ratchet** — a stress/damage flag that biases the daughter to depolymerize when `i*` is wrong, so a *deeper empty channel* (longer daughter downstream of `i*`) gives more backtrack steps and geometric `q*(n)`. The scaling is bought by **strand length**, the `n` steps share **one** discrimination signal (a processivity amplifier, not `n` independent resets), and `n−1` of the discards act on **other** monomers, not `i*`. **Fails C5** (length-bought), and if it needs the whole suffix pulled across one site, **fails C0** (sliding). *(Dynamic disguise of site-stacking.)*
- A **sliding read-head** or postulated catalyst — **fails C0**.
- A folded configuration with **overlaps or fictitious contacts** — **fails G**.
- A **cold** copier that discriminates at `A = 0`, or one whose drive enters only a *sequence-independent* step (so it cannot source the `A>0` discrimination that must vanish at `A=0`) — **fails C3**.
- A **homogeneous tape** (all one symbol) that self-proofreads by length while encoding no sequence information — capacity is length-encoded, not sequence-encoded, so a "better variant" is just a longer uniform tape and nothing bootstraps. *(The von-Neumann-self-description gap; a witness must carry real sequence information.)*

## How your answer will be checked

Verify **G** from the coordinates (walk self-avoiding, contacts real); recompute `qᵢ` and `Q` from `W` over the spatial neighborhoods; confirm **C0** uniform + spatially-local, folding emergent; **C3** by the `A = 0` identity; **C2** by swapping sequence; **C4** by locating the variant and `N`; **C5** at the designated site `i*` — recompute `q*(n)` across the tape family and confirm the error falls **geometrically** in `n` (not saturating, not `n`-independent), that each increment is a distinct irreversible driven discard **delivered to `i*` by a sequence-distant monomer folded into contact with it** (not by a longer downstream daughter), and that the stage-count is set by the **sequence's fold depth**; if the witness routes the stages time-order or nested, confirm that ordering **emerges from `W`** (no sliding read-head). A witness that raises fidelity by lengthening the strand — whether `∏ᵢ qᵢ` across many bits or `q*` at one bit via a deeper empty channel — does **not** pass C5.

*(Operator note (v3), not for the solver: hand-checkability is the make-or-break here — keep lattices small and coordinates explicit. **Probe recipe:** require the solver to emit the full `X` coordinate list *before* it writes `W`; an overlap (`Xᵢ = Xⱼ`) or a broken step then surfaces immediately, and if solvers hallucinate overlaps or fictitious contacts, that is the LLM spatial-reasoning ceiling — finding it fast is itself the result. **The v3 point:** a returned "impossible" is now only informative if it carries an exhibited construction that hits the wall — a bare forfeit is non-compliant and tells us nothing (that was the v2 defect: solvers echoed the coordination bound we stated, without building). Raw returns from prior outbounds are in [`docs/external/`](docs/external/) — `folding-outbound-1_raw.md` (v1) and `folding-outbound-2_raw.md` (v2); do not paste them into a fresh outbound.)*
