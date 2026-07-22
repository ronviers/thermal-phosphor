# thermal-phosphor — handoff to next session

*Written 2026-07-22. Read [`../CLAUDE.md`](../CLAUDE.md) (the guards) and [`../STATE.md`](../STATE.md) (the thinking) first — this is "what changed and where to pick up," and specifically **how the work forks from here.***

## What this session did

Turned gate 6 (the one open gate — fidelity on the tape) from a description into a **self-certifying witness challenge**, then ran it. The method: hand a solver an explicit construction task with a mechanical acceptance oracle whose conditions *are* the guards (on-tape, drive-off collapse, heritable, above Eigen). We verify by recomputing a few numbers — never by refereeing biology. This is now the project's core direction (installed in [`../CLAUDE.md`](../CLAUDE.md) and [`../STATE.md`](../STATE.md)).

**Five attempts, logged in [`challenge-attempts.md`](challenge-attempts.md):**
1. A strong solver declared C0 impossible — a **misparse** (conflated legal local-state-dependent rates with forbidden substring-addressing). Refuted; C0 sharpened.
2–3. **Two independent clamp-motif witnesses** (mine + Gemini) pass C0–C4 but hit the same **off-tape ceiling** (~`d²`). Forced condition **C5** (capacity on the tape).
4–5. **Two independent cascade attempts** to clear C5 both fail: mine needed a forbidden **sliding read-head**; Gemini's is in-bounds (emergent latching) but a **delay line** that can't stack stages (saturates, depth-independent).

**The finding these converge on:** unbounded, tape-set fidelity needs `n` *independent* proofreading stages acting on one site → `n` elements *in contact* with it → **folding**. A 1-D bounded window caps this at O(1) (~`d²`). The 1-D challenge did its job and located its own edge: it proved sequence-encoded, drive-carried fidelity is real and buildable, and proved 1-D can't reach capacity. **It is now closed** — keep [`../CHALLENGE.md`](../CHALLENGE.md) as the record; don't re-run it.

## The fork (this is the part to get right)

The work now **pseudo-forks** into two tracks. They share everything upstream — the gate-6 target, the guards, and the findings above — and they will reconverge (Track A's generator is the blueprint Track B runs). Same repo; distinguished by artifact.

### Track A — the folding grammar (the math proof) — LIVE, immediate
The abstract question: **does a minimal self-folding sequence-encoded catalyst exist that passes C0–C5 on a lattice?** This is the "theoretical right to exist" — the rigorous argument that a capacity-unbounded replicator can run under uniform local rules without smuggling in a machine.
- **Artifact:** [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md) (my v0, written this session). Gemini's parallel v0 is at [`../gemini draft folding grammar v0.md`](../gemini%20draft%20folding%20grammar%20v0.md) — **first next-session action is to compare the two v0 folding grammars**, same as we compared witnesses.
- **Workflow:** the same drag-to-a-model loop. Drag `CHALLENGE-fold.md`, framing line "Solve this challenge…", grade the returned witness against G + C0–C5, log it in `challenge-attempts.md`.
- **The live risk (Gemini flagged it, take it seriously):** frontier models are strong on 1-D string logic and weak on 2-D/3-D coordinates, overlaps, and folding. If solvers immediately hallucinate overlapping coordinates or fictitious contacts, **that is the LLM spatial-reasoning wall** — record it, park the folding challenge, and revisit in a model generation. Finding that wall fast is itself a result, not a failure.

### Track B — TP's geometric substrate (the evolutionary engine) — NOT STARTED, eventual
TP's native geometry — sphere caps, the medial axis, inversive geometry (the massless bit of [`../CLAUDE.md`](../CLAUDE.md)/[`../STATE.md`](../STATE.md)) — is the sandbox where you can **actually run the loop and watch lineages climb the Eigen threshold**. Track A gives a blueprint `W` on paper; only Track B lets you watch Darwin happen. Begin this when Track A either yields a clean `W` or parks at the spatial wall. This is the loop-closure: the oracle work drove the abstract challenge *back* to the geometric substrate TP started from.

## Shelved decisions — do not lose these

- **C6 — von Neumann self-description.** The degenerate all-`1` tape passes C0–C5 while encoding zero information. C0–C5 don't yet demand the copier be a *description that constructs the copier*. Fold C6 in when a witness actually exploits this.
- **C3 cold-baseline strengthening.** Gemini's witness passed C3's *letter* (tape-control vanishes at `A=0`) while being a mostly-cold copier (`Q(A=0)=0.99`). Strengthen C3 to demand the fidelity *itself* be drive-carried only if a witness cheats through it. (Attempt #2's `Q(A=0)=½` is the clean form.)
- **Folding-grammar open design questions.** The 2-D 4-neighbours-per-site limit may force 3-D for deep pockets; how exactly the daughter is "grown"; keeping everything hand-checkable. These are Track A's to resolve as witnesses come in.

*Discipline reminder (why this went well): each attempt passed the current oracle and thereby exposed the next gap. Harden by attacking, not by adding clauses speculatively. Convergence between independent solvers is the signal; a solver that forfeits by naming the blocking condition is a success, not a failure.*

## Where everything lives

- [`../CHALLENGE.md`](../CHALLENGE.md) — the 1-D challenge, C0–C5. **Closed** (proved its point). The record.
- [`../CHALLENGE-fold.md`](../CHALLENGE-fold.md) — Track A, the folding grammar v0. **Live.**
- [`challenge-attempts.md`](challenge-attempts.md) — the running log (5 attempts + evaluations + the shelved gaps). Continue it for Track A.
- [`../STATE.md`](../STATE.md) — the thinking; frontier, the oracle's edges, the folding finding, the fork.
- [`../CLAUDE.md`](../CLAUDE.md) — the guards + the gate-6 method (installed this session).
- [`../where-we-are.md`](../where-we-are.md) — the visualization brief (still 1-D-framed; would want a folding panel + the C5/capacity story added before the next hand-off to a video/infographic model).
