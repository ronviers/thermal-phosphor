Here is the geometric extension. It is designed to be a tripwire for the "spatial wall." The coordinates are strictly integers, the lattice is strictly 2D, and the overlap checks are explicit absolute values. If an LLM cannot trace a self-avoiding walk on a 2D grid, it will fail C0 instantly by hallucinating a steric clash, giving us our clean stopping point.

To ensure C5 demands real stacking (multiple independent proofreading cycles) rather than a temporal delay, the generator must enforce that each additional step of fidelity requires burning an independent unit of drive ($A$) on an irreversible discard branch.

---

### The Extended Geometric Grammar

A construction is now the tuple `(S, X, c, A, W)`:

* **`S`** — a finite monomer alphabet, `k = |S| ≥ 2`.
* **`X`** — the tape's topological map. A sequence of coordinates mapping each monomer index $i \in \{1 \dots N\}$ to a position on a rigid 2D integer lattice $\mathbb{Z}^2$. `X` must satisfy two brutally simple geometric checks:
* **Contiguity:** $\vert{}\vert{}X_i - X_{i-1}\vert{}\vert{}_1 = 1$ (Euclidean/Manhattan distance is exactly 1; the sequence is a continuous chain).
* **Self-Avoiding (No Overlap):** $X_i \neq X_j$ for all $i \neq j$.


* **`c`** — the intended copy map.
* **`A`** — the drive affinity.
* **`W`** — the local spatial generator. $W$ evaluates transitions at site $X_i$ using *only* the monomer states occupying the 4 adjacent spatial coordinates: $(x_i \pm 1, y_i)$ and $(x_i, y_i \pm 1)$. Sequence index distance $\vert{}i - j\vert{}$ is invisible to $W$; only spatial adjacency matters.

### The Revised C0–C6 Acceptance Criteria

**C0–C4 remain structurally identical**, but are now evaluated over the spatial neighborhood rather than the sequence neighborhood.

**C5 — Unbounded Capacity via Stacking (The Anti-Delay Rule).**
The fidelity $Q(T; A)$ must scale as a product of multiple independent driven discards (e.g., Hopfield’s $d^n$), where the stage count $n$ is dictated by the folded tape's geometry.

* *The Enforcement:* A purely temporal delay (where a single intermediate state is simply held open longer to allow more unbinding) is strictly disqualified. Each added factor of $d$ must correspond to a distinct, irreversible kinetic step that consumes the drive $A$ and provides an independent branch for the mismatch to fall off.

**C6 — The Minimal Self-Folding Catalyst.**
The high-fidelity spatial configuration must be self-organizing. The target site $X_i$ must achieve its elevated $Q$ solely because the tape's sequence caused distant monomers to fold into its spatial neighborhood, creating the necessary contact latches for the C5 stacking cascade.

---

### How to use this as the Oracle Probe

This grammar forces the LLM to write out the explicit integer coordinates for the folded tape.

When you drag this to a frontier model, ask it to explicitly output the sequence and its $X_i$ coordinates before it writes $W$.

1. If the model outputs $X_3 = (2, 2)$ and $X_7 = (2, 2)$, it just failed the self-avoiding check. The spatial wall is hit.
2. If it passes the geometry check, check $W$. To pass C5, the model must map the spatial neighbors to a multi-stage kinetic proofreading cascade (e.g., Neighbor 1 drives state $I_0 \to I_1$; Neighbor 2 drives state $I_1 \to I_2$, with unbinding allowed at each).

If we run this and the models immediately shatter on the coordinate math, we log the ceiling, park Option A, and move directly to the applied TP geometric substrate (Option B).