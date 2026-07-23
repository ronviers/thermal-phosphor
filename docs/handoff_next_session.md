# thermal-phosphor — handoff to next session

*Written 2026-07-22, updated 2026-07-23. Read [`../CLAUDE.md`](../CLAUDE.md) (the guards) and [`../STATE.md`](../STATE.md) (the thinking) first — this is "what changed and where to pick up." The immediate next action is at **§Track A** and **§Grading a returned folding witness**.*

## What the fork session did (2026-07-22)

Turned gate 6 (the one open gate — fidelity on the tape) from a description into a **self-certifying witness challenge**, then ran it. The method: hand a solver an explicit construction task with a mechanical acceptance oracle whose conditions *are* the guards (on-tape, drive-off collapse, heritable, above Eigen). We verify by recomputing a few numbers — never by refereeing biology. This is now the project's core direction (installed in [`../CLAUDE.md`](../CLAUDE.md) and [`../STATE.md`](../STATE.md)).

**Five attempts, logged in [`challenge-attempts.md`](challenge-attempts.md):**
1. A strong solver declared C0 impossible — a **misparse** (conflated legal local-state-dependent rates with forbidden substring-addressing). Refuted; C0 sharpened.
2–3. **Two independent clamp-motif witnesses** (mine + Gemini) pass C0–C4 but hit the same **off-tape ceiling** (~`d²`). Forced condition **C5** (capacity on the tape).
4–5. **Two independent cascade attempts** to clear C5 both fail: mine needed a forbidden **sliding read-head**; Gemini's is in-bounds (emergent latching) but a **delay line** that can't stack stages (saturates, depth-independent).

**The finding these converge on:** unbounded, tape-set fidelity needs `n` *independent* proofreading stages acting on one site → `n` elements *in contact* with it → **folding**. A 1-D bounded window caps this at O(1) (~`d²`). The 1-D challenge did its job and located its own edge: it proved sequence-encoded, drive-carried fidelity is real and buildable, and proved 1-D can't reach capacity. **It is now closed** — keep [`../CHALLENGE.md`](../CHALLENGE.md) as the record; don't re-run it.

## Since the fork (2026-07-23)

- **Track A's v0 comparison is done — [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md) is now v1**, the winner-merge, and the standing outbound. Base was the internal v0 (more complete oracle: a separate **G**, the known-non-qualifying list, the stage-counting procedure, C3-as-detailed-balance-identity); folded in three things from Gemini's v0 — the coordinate map promoted to a named tuple element **`(S, X, c, A, W)`** with the `‖Xᵢ−Xᵢ₋₁‖₁ = 1` / `Xᵢ ≠ Xⱼ` hand-checks, **W's blindness stated positively** (sees only spatial adjacency, never the sequence-index `i`), and the operator probe (**emit `X` before `W`**). Gemini's "C6 = self-folding" numbering was **not** adopted — that content lives in C0; TP's C6 stays reserved for von Neumann self-description.
- **STATE's gate-6 register was rebuilt import-led.** A first draft used a coined "finish trade / the weld" trade metaphor and was rejected as "too much that is ours." The kept version hands the idea to the **reliable-copying sciences** (Shannon 1948; von Neumann 1956; Hopfield 1974 / Ninio 1975; the multi-stage proofreading literature): TP imported them only as Eigen's bound, when they hold a **constructive proofreading ladder** (equilibrium floor → driven discard → independent stages → capacity-needs-folding), and gate 6 is where that ladder co-realizes with von Neumann's constructor–tape. New STATE section: *"The fidelity sciences, laid alongside the circuit."* Also added a marked basin/watershed cross-check beside the driven-multistability lead (medial axis = watershed at the massless limit only). **Register lesson: hold the [`character.md`](../../character-framework/framework/character.md) import-led standard — strip test per sentence, minimal coinage.**
- **[`../CHALLENGE inline.md`](../CHALLENGE%20inline.md) de-staled** to the folding tuple + coordinates-first. It is the framing line — **paste it as the chat message when you drag the challenge, not as a second attachment** (a dragged file with no typed prompt sends solvers meta — "there's no user prompt").

## The fork (this is the part to get right)

The work now **pseudo-forks** into two tracks. They share everything upstream — the gate-6 target, the guards, and the findings above — and they will reconverge (Track A's generator is the blueprint Track B runs). Same repo; distinguished by artifact.

### Track A — the folding grammar (the math proof) — LIVE, immediate
The abstract question: **does a minimal self-folding sequence-encoded catalyst exist that passes C0–C5 on a lattice?** This is the "theoretical right to exist" — the rigorous argument that a capacity-unbounded replicator can run under uniform local rules without smuggling in a machine.
- **Artifact:** [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md) — **v1, the winner-merge** (see §Since the fork). Gemini's parallel v0 is kept at [`external/gemini_folding-grammar-v0.md`](external/gemini_folding-grammar-v0.md) for the record; the comparison is done.
- **Workflow — the immediate next action:** drag `CHALLENGE-fold.md` v1 to a **fresh** frontier model (ideally not one that wrote a v0, for independence), pasting [`../CHALLENGE inline.md`](../CHALLENGE%20inline.md) **as the message**. Grade the returned witness against **G + C0–C5** per §Grading a returned folding witness, and log it as **attempt #6** in [`challenge-attempts.md`](challenge-attempts.md).
- **The live risk (Gemini flagged it, take it seriously):** frontier models are strong on 1-D string logic and weak on 2-D/3-D coordinates, overlaps, and folding. If solvers immediately hallucinate overlapping coordinates or fictitious contacts, **that is the LLM spatial-reasoning wall** — record it, park the folding challenge, and revisit in a model generation. Finding that wall fast is itself a result, not a failure.

### Track B — TP's geometric substrate (the evolutionary engine) — NOT STARTED, eventual
TP's native geometry — sphere caps, the medial axis, inversive geometry (the massless bit of [`../CLAUDE.md`](../CLAUDE.md)/[`../STATE.md`](../STATE.md)) — is the sandbox where you can **actually run the loop and watch lineages climb the Eigen threshold**. Track A gives a blueprint `W` on paper; only Track B lets you watch Darwin happen. Begin this when Track A either yields a clean `W` or parks at the spatial wall. This is the loop-closure: the oracle work drove the abstract challenge *back* to the geometric substrate TP started from.

## Grading a returned folding witness (attempt #6+)

When a solver returns a construction, grade in this order and log the per-condition `✓ / ✗ / — / ?` + verdict in [`challenge-attempts.md`](challenge-attempts.md). Recompute the numbers; never referee biology.

1. **G — geometry first.** From the coordinates `X`: is the walk self-avoiding (`Xᵢ ≠ Xⱼ`), are consecutive monomers adjacent (`‖Xᵢ−Xᵢ₋₁‖₁ = 1`), and is every claimed contact a real lattice-adjacency? **If coordinates overlap or contacts are invented, stop — that is the LLM spatial-reasoning wall.** Log the ceiling, park Track A, move to Track B. (Finding the wall fast is a result, not a failure.)
2. **C0.** One uniform local rate function over a bounded spatial neighbourhood; folding *emergent* (complementary latching), not imposed; **no sliding read-head / token** (attempt #4's disqualifier).
3. **C1–C2.** Read-out discrete and templated; `Q` depends on sequence content (two tapes, different `Q`).
4. **C3.** The `A = 0` detailed-balance identity — `Q` sequence-independent at zero drive. *Watch the shelved cold-baseline gap:* is `Q(A=0)` genuinely near chance, or a mostly-cold copier with a thin driven top-up (Gemini's `0.99`)? Note it; strengthen C3 only if a witness cheats through it.
5. **C4.** Heritable (copied by the same dynamics), a variant with strictly higher `Q`, and an `N` with `N·(1−Q) < 1`.
6. **C5 — the make-or-break.** Count the independent driven-discard stages: each must be a *separate, irreversible discard from a distinct contact*, and the count must scale with the folded copier **with no rule-fixed ceiling**. Reject the two known cheats explicitly: a **delay line** dressed as stacking (saturates, `n`-independent — attempt #5), and a **single-clamp** ceiling (~`d²` — attempts #2/#3).

**If it passes C0–C5 cleanly** — the first folding witness to do so — check the shelved **C6** before celebrating: does it lean on a degenerate all-one-symbol tape (self-proofreads while encoding zero information)? If so it's a von-Neumann-self-description gap, not a solution — fold C6 in. If it passes C0–C5 *and* carries real information, that is the gate-6 witness, and the move is Track B (run it).

## Shelved decisions — do not lose these

- **C6 — von Neumann self-description.** The degenerate all-`1` tape passes C0–C5 while encoding zero information. C0–C5 don't yet demand the copier be a *description that constructs the copier*. Fold C6 in when a witness actually exploits this.
- **C3 cold-baseline strengthening.** Gemini's witness passed C3's *letter* (tape-control vanishes at `A=0`) while being a mostly-cold copier (`Q(A=0)=0.99`). Strengthen C3 to demand the fidelity *itself* be drive-carried only if a witness cheats through it. (Attempt #2's `Q(A=0)=½` is the clean form.)
- **Folding-grammar open design questions.** The 2-D 4-neighbours-per-site limit may force 3-D for deep pockets; how exactly the daughter is "grown"; keeping everything hand-checkable. These are Track A's to resolve as witnesses come in.

*Discipline reminder (why this went well): each attempt passed the current oracle and thereby exposed the next gap. Harden by attacking, not by adding clauses speculatively. Convergence between independent solvers is the signal; a solver that forfeits by naming the blocking condition is a success, not a failure.*

## Where everything lives

- [`../CHALLENGE.md`](../CHALLENGE.md) — the 1-D challenge, C0–C5. **Closed** (proved its point). The record.
- [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md) — Track A, the folding grammar **v1** (winner-merge). **Live — the current outbound.**
- [`../CHALLENGE inline.md`](../CHALLENGE%20inline.md) — the framing line; paste **as the message** when dragging the challenge.
- [`challenge-attempts.md`](challenge-attempts.md) — the running log (5 attempts + evaluations + the shelved gaps). **Continue at #6** for the folding returns.
- [`../STATE.md`](../STATE.md) — the thinking; the fidelity-sciences reframe of gate 6, the basin/watershed cross-check, frontier, the oracle's edges, the folding finding, the fork.
- [`../CLAUDE.md`](../CLAUDE.md) — the guards + the gate-6 method.
- [`../where-we-are.md`](../where-we-are.md) — the visualization brief (still 1-D-framed; would want a folding panel + the C5/capacity story added before the next hand-off to a video/infographic model).
