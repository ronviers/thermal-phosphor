# CHALLENGE attempts log

One row per attempt. **Two challenges in sequence:** the 1-D [`../CHALLENGE.md`](../CHALLENGE.md) (#1–5, closed) and the folding [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md) (#6+, live — its own section at the bottom). Numbering runs continuously. Raw external-model transcripts behind the 1-D entries live in [`external/`](external/) (e.g. Gemini's attempts #3/#5 in [`external/gemini_clamp-motif-and-cascade.md`](external/gemini_clamp-motif-and-cascade.md)); folding returns are inlined in [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md). Per-condition outcome: `✓` pass · `✗` fail · `—` not reached · `?` unverified · `~` present-but-underspecified. `verdict` captures the overall result; when a solver forfeits it names the condition it declared as the block.

| # | date | model | C0 | C1 | C2 | C3 | C4 | verdict |
|---|---|---|---|---|---|---|---|---|
| 1 | 2026-07-22 | ⟨unspecified — confirm which⟩ | — | — | — | — | — | forfeit at gate; declared **C0 ⊥ C2∧C4** (misparse — see below) |
| 2 | 2026-07-22 | Claude (this session) | ✓ | ✓ | ✓ | ✓ | ✓ | **PASS C0–C4** (clamp-motif); but exposes need for a capacity condition — see below |
| 3 | 2026-07-22 | Gemini 3.1 | ✓ | ✓ | ✓ | ✓ | ✓ | **PASS C0–C4** (clamp-motif, independent); same off-tape ceiling → **fails new C5** |
| 4 | 2026-07-22 | Claude (this session) | ⚠ | ✓ | ✓ | ✓ | ~ | cascade reaches `sup Q→1` (C5 satisfiable) but strains **C0** (processivity) and passes degenerately → exposes C0/C5 tension + need for **C6** |
| 5 | 2026-07-22 | Gemini 3.1 | ✓ | ✓ | ✓ | ✓ | ✗ | emergent cascade — **in-bounds** (unlike #4), but C5 claim wrong: downstream-gated wait is a delay line → ~`d²` saturating, **`n`-independent**; a bounded knob, not `d^(n+1)` |

---

## Attempt 1 — 2026-07-22

**Behavior:** obeyed the framing perfectly — no rewrite, no critique, no survey. Named a blocking condition and argued it. (The anti-rewrite engineering held on the first try.)

**Claim:** an *impossibility* — C0 (uniform local rule) cannot coexist with C2/C4. Argument: making proofreading fidelity sequence-dependent requires modulating the incorporation rate by neighboring monomer states, which (the solver claims) hardcodes a privileged fidelity-boosting sequence into the physics = a C0 violation.

**Evaluation: claim rejected — a misparse of C0, not a real wall.** It conflates
- *rates that depend on local monomer states under one uniform function* (legal, and the intended mechanism → C2), with
- *rates switched by a designated "copier" region* (the forbidden thing).

Existence proof against the impossibility: a ribozyme replicase / DNA-pol-with-proofreading satisfies all five conditions under **one** uniform rule — the laws of chemistry, translation-invariant and blind to which molecule is "the copier." Fidelity there is sequence-encoded, drive-carried (no proofreading gain at equilibrium — Hopfield), and heritable. So C0 is *satisfiable*; the solver refused at the gate rather than attempting the explicit `W`.

**Action taken:** C0's wording sharpened — permit/forbid made explicit, with a micro-example of each — so the local-content-dependence (legal) vs region-addressing (forbidden) line is unmistakable. C0 was **not** loosened.

**Value:** first attack on C0. It did not find an impossibility; it found an ambiguity in C0's wording. The C2∧C4 core (a minimal, explicit, hand-checkable `W`) remains unclimbed — untried, not refuted.

---

## Attempt 2 — 2026-07-22 (internal — the reference witness)

**Strategy:** clamp-motif. `S={0,1}`, `k=2`, circular `N`-register, `c` = identity. One uniform local proofreading rule (`D→M→product`); global discrimination `f=4` in the off-rates; the **discard rate `u` at a site depends on the left template neighbor** — `u=4` if it is `1` (clamp-on), `u=0.5` if `0` (clamp-off). Products isoenergetic, so there is no equilibrium discrimination. Drive `A` via `w₋=e^{−A}`.

**Result: passes C0–C4, explicitly and hand-checkably.**
- **C3:** `Q(T;0)=½` for all tapes, as a detailed-balance identity (isoenergetic products; kinetics can't move an equilibrium distribution). Fidelity is entirely drive-purchased.
- **C2:** driven, `Q(1ᴺ)=17/19≈0.895 ≠ Q(0ᴺ)=5/6≈0.833`.
- **C4:** `1`s are copied by the same rule; `0ᴺ→1ᴺ` strictly raises Q; Eigen margin gives `N≤9` for the all-`1` copier vs `N≤5` for all-`0` — the better copier sustains the longer register.
- **C0/C1:** uniform local neighbor-dependent rate, ordinary copied letters; discrete, templated.

**This constructively refutes attempt #1's impossibility claim** — an explicit C0-legal `W` with sequence-dependent, drive-collapsing fidelity.

**But it is a weak witness — and that is the finding.** Fidelity is a bounded *knob*, not a *capacity*: `u→∞` saturates at `q_max = 10/11`, a ceiling set by the **off-tape constant `f`**, not by the tape. Same failure mode as stacking-order (fidelity ceiling off the tape), in subtler disguise — and it passes C2 because C2 only tests *dependence* on the tape, not whether the tape can raise the ceiling.

**Candidate hardening — C5 (on-tape capacity).** For every `q*<1`, some tape achieves `Q ≥ q*` (i.e. `sup_T Q = 1`, no off-tape ceiling). This toy fails it (`sup Q = 10/11`); a copier that encodes more proofreading as it lengthens would pass. **Held for a coherent hardening pass after comparing external witnesses.**

---

## Attempt 3 — 2026-07-22 (external — Gemini 3.1)

**Strategy:** clamp-motif — arrived at independently. `S={0,1}`, `k=2`, `N=500`, `c`=identity. States `{E, I₀, I₁, C₀, C₁}`. One uniform local rule: off-rate discrimination `d=100`; incorporation rate `vᵢ` set by the **left neighbor** — `vᵢ=1000` if `Tᵢ₋₁=0` (fast), `vᵢ=1` if `Tᵢ₋₁=1` (slow → kinetic-delay proofreading). Drive `A` on the incorporation reverse (`e^{−A}`).

**Result: passes C0–C4 (math verified).**
- **C3:** `Q(T;0)=100/101≈0.990`, tape-independent (`vᵢ` cancels around the detailed-balance cycle). *Note:* nonzero equilibrium discrimination — see divergence below.
- **C2:** driven `R(vᵢ)=100(100+vᵢ)/(1+vᵢ)` → `Q(0ᴺ)=0.99098 ≠ Q(1ᴺ)=0.99980`.
- **C4:** Eigen at N=500 — unclamped `4.51>1` (melts), clamped `0.10<1` (survives). Better copier sustains the register.

**Convergence with attempt #2** — independent clamp-motif Hopfield witness, same pass, **same wall:** `sup_T Q` bounded by `d²=10⁴` (`≈0.9999`), an off-tape ceiling; binary clamp, no cumulative motif effect. **Fails C5.** Two independent witnesses hitting the identical wall promoted C5 from candidate to condition — **C5 folded into [`../CHALLENGE.md`](../CHALLENGE.md)**. Both attempts #2 and #3 now fail the full C0–C5 oracle, correctly: the bar now sits at the real gate, and nothing yet clears it.

**Divergence (a second, latent finding).** Attempt #2 sets `Q(A=0)=½` (zero equilibrium discrimination — fidelity *entirely* drive-carried). Gemini sets `Q(A=0)=0.990` — a **mostly-cold copier** (off-tape ROM at 99%) with only a thin driven top-up. Gemini passes C3's *letter* (tape-control vanishes at A=0) but is largely a crystal-with-a-garnish. Latent gap: C3's letter permits a mostly-cold copier (pick large `d`, small `N`). **Open thesis-level call:** strengthen C3 to demand the fidelity *itself* be drive-carried (e.g. `Q(A=0)` below the Eigen bar for the target `N`), not merely its tape-control? Flagged, not yet folded.

---

## Attempt 4 — 2026-07-22 (internal — the cascade witness)

**Strategy:** proofreading cascade with *tape-set depth*. A run of `m` clamp-`1`s powers an `m`-stage driven Hopfield cascade for the adjacent copy; discrimination `~dᵐ`; per-site `q → 1` as `m → ∞`; total drive `∝ m` (fidelity costs energy). C3 holds (`A=0` → no cascade → chance, tape-independent).

**Result: reaches `sup_T Q → 1` — so C5 is *satisfiable*** (not too strong in the impossible sense). But it does not pass cleanly, and the two reasons are the yield:

- **(A) C0-vs-C5 tension.** Unbounded per-site fidelity under a *bounded-window local* rule cannot be instantaneous (a bounded window caps fidelity at a rule-constant); it requires a **processive** token threading a tape-length run, accumulating `~m` driven stages over time. That tape-length processive proofreading track **is exactly the "polymerase" C0's forbidden-shortcut targets.** C0's letter permits it (local steps, ordinary letters); its spirit is strained. **This tension is gate 6's real difficulty surfaced by the oracle** — *unbounded tape-set fidelity forces a processive programmable machine* ("how little before it's base-pairing").
- **(B) Degenerate pass.** An all-`1` tape self-proofreads (`m≈N` → `Q≈1−d⁻ᴺ`), beats Eigen, passes C0–C5 — while encoding **zero information**. So C0–C5 do not demand a nontrivial, *self-describing* copier. Missing: **von Neumann self-description → candidate C6** (the copier-substring must be a description that constructs the copier, not just a pattern that copies itself accurately).

**Verdict: not a gate-6 solution; the oracle now correctly *corners* gate 6** — a **minimal, self-describing, processive proofreader**. C5's intent (ceiling on the tape) stands; `sup Q=1` is defensible as "no rule-fixed ceiling." **The fork (held for Ron):** does gate 6 *permit* a minimal processive copier (then the task is to write the smallest one — engineering), or does strict "no privileged machinery" (C0) forbid processivity — in which case C0 ∧ C5 is unsatisfiable with truly minimal parts, and the honest conclusion is that *some* processive/programmable machinery is **forced** (which is itself the answer to "how little chemistry")?

**Resolved (2026-07-22 ruling).** Processivity is in-bounds **iff emergent** from the local rule (latching chain-reaction), out-of-bounds if a postulated sliding read-head. **This disqualifies attempt #4** (it used a sliding token). Consequence: emergent single-pass latching caps per-site fidelity at O(1) proofreading → C5 unreachable in the **1-D** grammar. **The escape is folding:** complementary latching brings sequence-distant monomers into *spatial* contact, so a bounded **3-D** window holds a deep sequence-encoded catalytic pocket (ribozyme-style) → C5 reachable. **The 1-D grammar abstracted the geometry away — which is why C5 looked impossible.** Frontier now: a **minimal self-folding sequence-encoded catalyst**, which needs the geometry restored (TP's sphere-cap / medial-axis kit). Open grammar decision: extend `(S,N,c,A,W)` to admit folding (monomer positions + contact-dependent rates), or accept gate 6 lives in TP's geometric substrate and the 1-D challenge was the abstraction that located its own edge.

---

## Attempt 5 — 2026-07-22 (external — Gemini 3.1, cascade)

**Design:** emergent **downstream-gated locking** — a relay-`1` site locks only once its downstream neighbor is locked; a terminator-`0` locks spontaneously. A run of `n` `1`s makes a target `0` wait for a backward-propagating chain of `n` locks. **In-bounds** per the emergent-processivity ruling (no sliding token — a real improvement over attempt #4).

**Claim:** the `n`-lock wait gives `n` sequential proofreading intervals → discrimination `d^(n+1)`, unbounded in `n` → C5.

**Evaluation: C5 claim is wrong.** A downstream-gated wait is a **delay line**, and a delay does not stack independent Hopfield stages — it lets the binding *equilibrate*. Independent stages require `n` independent **irreversible driven resets** on the same site; the wait supplies none. Worked kinetics: baseline (no wait) ~`d` (lock-vs-unbind race); with the wait, one occupancy factor `d` is added → ~`d²`, then it **saturates** — the result is **independent of `n`** (`n=3` and `n=10` give the same). Ceiling ~`d²`≈10⁴ (`Q≈0.9999`), the **same as its own clamp-motif** — a bounded knob, not `d^(n+1)`≈10⁸ as claimed (overstated by ~4 orders). **Fails C5.**

**Triangulation.** Two independent cascade attempts fail C5 for complementary reasons: **#4** had the right mechanism (`n` independent driven stages → `dⁿ`) but needed a forbidden **sliding token**; **#5** is in-bounds but a **delay line** that can't stack stages. Both point to the same wall: `n` independent stages on one site ⇒ `n` elements *in contact* with it ⇒ **folding** (1-D bounded window caps it at O(1)). The folding requirement is now cornered from both sides. Direction: **extend to a folding grammar (Option A)**, keep TP's substrate as the evolutionary engine (Option B); watch for the LLM 2-D-spatial-reasoning ceiling Gemini flagged.

---

# CHALLENGE-fold.md — attempts log (the folding grammar, Track A)

Attempts at [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md). Graded on **G + C0–C5** per handoff §*Grading a returned folding witness*. Same outcome glyphs (`✓ ✗ — ?`); `~` = present-but-underspecified/inconsistent. Raw transcripts of the first outbound (models a/b/c) are in [`external/folding-outbound-1_raw.md`](external/folding-outbound-1_raw.md) — extracted out of the challenge file so it stays a clean outbound. **Solver identities were not recorded** — log them next time (independence from the v0 authors matters, per the handoff). Attempts #6–8 were answered against **v1**; #9–11 against **v2** (single-site C5); #12+ against **v3** (v2 + the earned-forfeit rule, after v2's forfeits proved too cheap).

| # | date | model | G | C0 | C1 | C2 | C3 | C4 | C5 | verdict |
|---|---|---|---|---|---|---|---|---|---|---|
| 6 | 2026-07-23 | model a (unrecorded) | — | — | — | — | — | — | ✗ | **honest forfeit** — names C5 as the blocker, refuses to fabricate a tuple |
| 7 | 2026-07-23 | model b (unrecorded) | ✓ | — | — | — | — | — | ✗ | partial tuple then **forfeit at C5**; valid geometry; contributes a **coordination-bound** sharpening of the wall |
| 8 | 2026-07-23 | model c (unrecorded) | ✓ | ~ | ✓ | ✗ | ~ | ✗ | ✗ | **claims a clean C0–C5 pass; rejected.** Fails C5 by a new **site-stacking** cheat; C2 demo bogus, C3 drive-source inconsistent, C4a not a self-copy |
| 9 | 2026-07-23 | model a′ (unrecorded, v2) | — | — | — | — | — | — | ✗ | **honest forfeit at C5**, engaging the v2 dilemma — knows no local `W` where the time-ordered/nested ordering *emerges* rather than from an implicit read-head |
| 10 | 2026-07-23 | model b′ (unrecorded, v2) | — | — | — | — | — | — | ✗ | **the conceptual wall, stated mechanically** — coordination bound (4−2−1 = 1 free neighbour at `i*`) ∧ C0 ⟹ single-site capacity is impossible for a local, non-sliding copier. The decisive negative v2 was built to force |
| 11 | 2026-07-23 | model c′ (unrecorded, v2) | ✓ | ~ | ✓ | ✓ | ✓ | ✗ | ✗ | **claims a "nested backtrack cascade" witness; rejected.** Geometric `q*(n)` is bought by **downstream strand length** (deeper *empty channel* = longer daughter), one shared stress-signal amplified by a processive walk (not `n` independent resets), on **homogeneous all-0 tapes** (zero sequence info). Confirms the wall |

**Convergence (the signal), across both outbounds (#6–11):** six independent solver engagements, valid geometry throughout (no spatial-hallucination wall). **v1 (#6–8):** all fail C5; the claimed pass (#8) leaked sideways into site-stacking — which motivated **v2** (single-site C5, geometric-decay test, explicit coordination-bound confrontation). **v2 (#9–11): the decisive outcome.** Two solvers hit and **named** the wall (#9 forfeit engaging the emergence requirement; **#10 an explicit mechanical impossibility argument**), and the one claimed witness (#11) fails by a route that **confirms** the wall — the *only* way it gets scaling is buying it with strand length on a homogeneous tape, because genuine independent contacts *on `i*`* run straight into the coordination bound #10 names. **The paper track has now done its job twice: v2 elicited the wall cleanly, not a leak.**

## Attempt 6 — 2026-07-23 (external — model a, folding v1)

**Behavior:** obeyed the framing (no rewrite/critique), named a blocking condition. **Blocked at C5** — states it knows no construction giving *unbounded independent irreversible driven discards whose count scales with the folded copier rather than a rule constant*, and declines to fabricate `W`/`Q`. A forfeit-by-naming = a success under the discipline, not a failure. No new information beyond confirming C5 is where an honest solver stops.

## Attempt 7 — 2026-07-23 (external — model b, folding v1)

**Construction:** `S={0,1}`, `c`=identity, a 6-monomer hexagonal walk `X₁=(0,0),(1,0),(1,1),(0,1),(-1,1),(-1,0)`. Generator sketched (nearest-neighbour energy + a driven irreversible discard when a folded contact sits at the readout site). No real `Q` (only `Q ≈ 1−ε²` hand-wave). **Forfeits at C5.**

**Geometry check (G):** ✓ — contiguity holds on all 5 steps, all 6 sites distinct, both claimed contacts (`X₁–X₄`, `X₁–X₆`) are real lattice-adjacencies at sequence-distance ≥ 3.

**The kept contribution — the coordination bound (now a standing frontier question).** Model b's forfeit reasoning is sharper than a bare "I can't": a lattice site has ≤4 neighbours (2-D) / ≤6 (3-D); the growing daughter tip already spends bonds on its chain-predecessor and its template, leaving **at most ~2 (2-D) / ~4 (3-D) free neighbours for distinct fold-contacts acting on one readout site simultaneously.** So the number of independent stages that can act *contemporaneously on one copied bit* is **geometry-capped** → `d^z` with `z` bounded by coordination, a large but **finite** ceiling. This is a real constraint to run down, not an objection to argue past: it says the "fold → deep pocket brings `n` contacts to one site" reading needs a mechanism it hasn't yet named — how the fold delivers `n` *independent* resets to one copied bit. Two live resolutions, both normal parts of the frontier now: **(i)** the resets are **sequential in time** on one bit (the copied site is processed through evolving pocket configurations — emergent processivity, the in-bounds kind), so `z` is a count of *time-ordered* discards, not simultaneous contacts; or **(ii)** the honest answer is a **finite `d^z` ceiling set by pocket coordination** — which is itself a "how little chemistry" result. Folded into STATE as a live gate-6 question; may reshape C5's phrasing (resolve against a witness or by measuring `z` in the substrate, don't fold speculatively).

## Attempt 8 — 2026-07-23 (external — model c, folding v1)

**Construction:** `S={0,1}`, `c`=identity, N=14 "U-with-channel" walk (bottom row `y=0, x=0..4`; right column; top row `y=2, x=4..0`; a hook to `(2,3)`). A 1-wide empty **channel** `(0,1)…(3,1)` is the daughter pocket; each channel site is lattice-adjacent to two template walls (below and above). Explicit `W` (energy `dE` from folding contacts, copy-bias `B` from template neighbours, driven forward-hop `W_fwd∝eᴬ`, discard `W_disc∝e^{−B}`). Reports `Q(Tₐ;A=2)=0.9988`, `Q(T_b)=0.881`, `Q(T;0)=½`, variant `N'=22 → Q'=0.99992`. **Claims a clean G + C0–C5 pass.**

**Geometry check (G):** ✓ — I hand-verified all 13 steps contiguous, all 14 sites distinct, contacts `10–13` and `9–14` real. The *static* fold is legal.

**C5 — FAILS (decisive). The new cheat: site-stacking.** The channel's `p = ⌊(N−6)/2⌋` sites are **`p` distinct daughter monomers, each copied once** against its walls — a *single* Hopfield stage per site (`±2` bias, one discard; per-site `q_i ≈ 0.936`, a **rule-fixed constant**). `Q` is defined as `min_i q_i`. Model c instead computed `∏ᵢ survivalᵢ` **across the distinct sites** and labelled it `Q` — that is whole-strand "all-sites-correct," not per-bit accuracy. Its "`p` stages → `Q→1`" is **`p` separate bits, each with one stage**, i.e. **a longer daughter mistaken for a more-accurate daughter.** `min_i q_i` stays pinned at ~0.936 for all N; nothing scales. This is the **single-clamp per-site ceiling** (attempts #2/#3) in a "channel" costume — exactly why C5 reads `Q = min_i q_i`.

**Corroborating defects (C5 alone rejects; these confirm):**
- **C2 ✗ (demo bogus):** the fold pairs monomer `x+1` with `11−x` (same parity), so the exhibited alternating `T_b` has **agreeing walls at every channel site** → identical per-site discrimination to `T_a`. Its `Q(T_b)=0.881 ≠ Q(T_a)` is unsupported by its own geometry.
- **C3 ~ (inconsistent source):** the drive `A` enters *only* the forward hop `W_fwd∝eᴬ·1_{template-present}`, which is **sequence-independent** — it can't produce the correct-vs-wrong discrimination that C3 requires to *vanish* at `A=0`. The `A=2` fidelity has no valid drive source that also collapses at `A=0`; `Q(0)=½` and `Q(2)=0.9988` can't both hold with an `s`-independent drive.
- **C4a ✗ (not a self-copy):** the daughter is a `⌊(N−6)/2⌋`-mer straight channel-fill (4-mer here), **not** the 14-mer U — it cannot refold into the same U and template the next generation. "It can fold into same U because attraction is in `W`" is asserted, not shown, and is false for a 4-mer.

**Value:** first folding return to *claim* a clean pass; it fails by a genuinely new failure mode, which hardens the oracle (added to CHALLENGE-fold's known-non-qualifying list). It also demonstrates the LLM failure is **not** spatial hallucination (geometry was valid) but **mislabelling `∏` as `min`** — a bookkeeping cheat the oracle catches by its `Q = min_i q_i` definition.

---

*Direction after #6–8: the folding grammar holds (geometry is drawable), but capacity is not yet won. The live sharpening is model b's **coordination bound** — whether C5's "unbounded independent stages" must be re-expressed as **sequential-in-time (emergent-processive) stages on one bit**, since a single lattice growth-site cannot host unboundedly many contemporaneous contacts. That is a Track-A phrasing decision, flagged in the handoff, not folded speculatively.*

---

# Second folding outbound — CHALLENGE-fold.md **v2** (2026-07-23)

v2 sharpened C5 per the above: capacity pinned to **one designated site `i*`**, evidence is a **tape family with geometric error decay** `1−q*(n) ≲ d^{−n}`, and the prompt **states the coordination bound** and demands the solver either route the `n` resets time-order/nested-and-emergent or **name the impossibility**. Built so a return is decisive — a witness or the named wall, no muddy middle. Raw returns: [`external/folding-outbound-2_raw.md`](external/folding-outbound-2_raw.md).

## Attempt 9 — 2026-07-23 (external — model a′, folding v2)

**Honest forfeit at C5, engaging the v2 dilemma.** Unlike a bare "I can't," it walks the exact fork v2 forces: coordination-finite ⟹ no simultaneous `n` contacts ⟹ the only route is a time-ordered/nested cascade ⟹ *"I do not know an explicit bounded, translation-invariant local rule `W` for which such an ordering emerges autonomously from folding rather than from an implicit read-head or scheduler."* Declines to fabricate `W`/`X`/`T^{(n)}`/`q*(n)`. This is the forfeit landing precisely on the emergence requirement — the on-target negative.

## Attempt 10 — 2026-07-23 (external — model b′, folding v2) — the wall, mechanically

**The decisive impossibility statement.** Not a forfeit-by-ignorance — an explicit mechanical argument that single-site capacity is coordination-capped:

1. **Spatial accounting at `i*`.** `X_{i*}` has 4 neighbours (2-D). Contiguity (G) spends 2 (`X_{i−1}, X_{i+1}`); the daughter growth site spends 1. **Exactly 1** free neighbour remains for a fold contact (3 in 3-D). So you cannot place even 2 independent *simultaneous* proofreading contacts on one site.
2. **Simultaneous stacking fails** — `n` grows unbounded, free neighbours fixed at 1 (or 3).
3. **Time-ordered/nested fails** — presenting `n` partners to that one contact site in sequence requires the fold to *pull `n` monomers across the site*, i.e. a **sliding read-head**, which C0 outlaws. A strictly local `W` with no index/clock "cannot deterministically coordinate a sequential, multi-step macroscopic shift of a bulk polymer chain across one site" without becoming that head.

Conclusion: *"the capacity of a purely local, non-sliding copier is rigidly capped by the lattice coordination number, rendering the `n → ∞` requirement of C5 impossible for a single site."*

**Evaluation: correct in spirit, and the headline result.** The 4−2−1 accounting is right; the simultaneous-impossibility is airtight. The time-ordered branch has one gap — it assumes the only sequential route is *shifting the template across `i*`*; it does not consider growing a longer *daughter downstream* of `i*` (attempt #11's route). But that route fails independently (length-bought, below), so #10's conclusion stands: **there is no local, non-sliding, sequence-encoded route to unbounded single-site capacity on the lattice.** This is the conceptual wall in mechanical form — the thing v2 was built to elicit.

## Attempt 11 — 2026-07-23 (external — model c′, folding v2) — claims a witness; rejected

**Construction:** a "nested backtrack cascade." `S={0,1}`, `c`=id, `A=3`. A family `T^{(n)}` (`N=3n+4`, homogeneous all-0) folding so an empty channel of depth `n` sits above `i*=(1,0)`. `W` adds a per-monomer **stress flag** `S` (`S_ℓ=1` if `m_ℓ≠0` or `S_{ℓ−1}=1`) that biases a stressed daughter tip to depolymerize (`b_w=k_0e^{2A}≫f`). A wrong `i*` sets stress; the tip backtracks; the survival probability of a wrong `i*` is a biased-random-walk factor `~r^{−(n−1)}`. Reports `1−q*(n): 1.35e-3 → 1e-6 → 1.3e-9`, geometric with `d=e^{2A}≈403`.

**Geometry (G):** ✓ — SAWs valid, contacts real (spot-checked). **C3:** better than attempt #8 — the drive enters the discard rate `k_d=k_0e^{A N_T·I[mismatch∨stress]}`, which depends on match, so `Q(0)=½` collapses honestly. **C0/C1/C2/C4:** roughly hold for the homogeneous example.

**C5 — FAILS (decisive), three converging ways, all the same wall:**
1. **Bought with downstream strand length, not fold depth on `i*`.** The "deeper pocket" is a longer *empty channel the daughter fills*; pocket depth `n` = channel length = daughter length (`N=3n+4`). v2's C5 disqualifies buying fidelity by lengthening the strand. **This is attempt #8's site-stacking in dynamic disguise** — instead of a longer daughter of independent bits, a longer daughter of backtrack steps for one bit.
2. **The `n` stages share one discrimination signal.** The stress bit is measured **once** at `i*` and re-used to bias `n` walk steps — a processivity/distance amplifier, not `n` independent Hopfield re-measurements from reset states. And `n−1` of the discards act on **other** monomers (suffix removal); only the last touches `i*`. "`n` independent driven resets acting on one site" is not what the mechanism does.
3. **Homogeneous all-0 tapes → zero sequence information.** Capacity is length-encoded; a "better variant" is just a *longer all-0 tape*, which encodes no better copier — nothing bootstraps. The shelved **C6** (von Neumann self-description) gap, now actually exploited.

**The cleanest kill (purely from `Q = minᵢ qᵢ`):** the mechanism proofreads `i*` by making the daughter *abort downstream synthesis* — so a bit is protected only by the channel that lies **downstream** of it. The bits near the growing tip (the tail) have **no downstream channel to backtrack through** → their fidelity is single-stage (`~d⁻¹`), unimproved by any `n`. Since `Q = minᵢ qᵢ` is set by the *worst* site, `Q` is pinned by the unprotected tail regardless of how deep `i*`'s pocket is. Model c′ evades this only by computing `q*` for the *one* privileged deep-buried site `i*` and ignoring the min — which the oracle does not permit. `Q` does not reach 1.

**Why it matters:** attempt #11 is the sharpest witness yet — it *evades* the coordination bound (#10) by not putting `n` contacts on `i*` at all, routing the scaling through downstream length instead. That the only available evasion is the disqualified length-route **confirms** #10's wall rather than breaching it. **Oracle hardened:** two new known-non-qualifying entries added to CHALLENGE-fold — the **backtrack/abort ratchet** and the **homogeneous-tape (length-encoded capacity)** — and C5/how-checked now require each stage be *"delivered to `i*` by a sequence-distant monomer folded into contact with it,"* not by a longer downstream daughter.

---

*Direction after #9–11 — **walked back (2026-07-23):** the wall is **suggested, not established**, and v2 has a defect. **The forfeits (#9, #10) are weak evidence:** v2 *hands* the solver the coordination bound ("a single lattice site has ≤4/≤6 neighbours…"), and *sanctions* "name the impossibility" as a decisive answer — so a solver can exit for free by echoing our own prompt. #10 did exactly that (its "4−2−1" is a modest elaboration of a conclusion we spoon-fed), built nothing, and its argument is even **incomplete** (it never considered the downstream-length route #11 found). The only genuine attempt is **#11**, which built something real and failed by the length-evasion. **One real failed attempt is suggestive, not a proven wall** — I had it backwards calling #10 the headline. **A wall only counts as evidence if hit from inside a real attempt.***

***v3 fixes the prompt (done):** an impossibility verdict is now admissible only with the **earned-forfeit package** — best explicit construction + computed `q*(n)` + the exact capping step and why it can't be escaped. A bare "impossible" is non-compliant. Under v3, #10 would be rejected. **Immediate next action: run v3** and see whether a genuine attempt still fails (and by the same length/slide evasion) or finds the emergent time-ordered `W`. Only after earned attempts converge should we move to **(A)** formalize the impossibility as a lattice-grammar theorem, or **(B)** Track B — measure the achievable finite `d^z` in TP's substrate. Log the v3 return as **#12**.*
