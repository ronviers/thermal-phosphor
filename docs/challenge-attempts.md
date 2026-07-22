# CHALLENGE.md — attempts log

One row per attempt at [`../CHALLENGE.md`](../CHALLENGE.md). Raw external-model transcripts behind these entries live in [`external/`](external/) (e.g. Gemini's attempts #3/#5 in [`external/gemini_clamp-motif-and-cascade.md`](external/gemini_clamp-motif-and-cascade.md)). Per-condition outcome: `✓` pass · `✗` fail · `—` not reached · `?` unverified. `verdict` captures the overall result; when a solver forfeits it names the condition it declared as the block.

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
