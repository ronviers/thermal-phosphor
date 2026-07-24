# Folding outbound #2 — raw solver returns (CHALLENGE-fold.md v2, 2026-07-23)

The three raw responses to the **second** folding outbound (the sharpened **v2** challenge: single-site C5, geometric-decay tape family, explicit coordination-bound confrontation). Graded as **attempts #9–11** in [`../challenge-attempts.md`](../challenge-attempts.md). Extracted out of `CHALLENGE-fold.md` so it stays a clean outbound. Solver identities were not recorded at capture time.

---

## model a (unrecorded) — attempt #9 — honest forfeit at C5 (engages the v2 dilemma)

I cannot produce the requested tuple **(S, X, c, A, W)** because I do not know of an explicit construction satisfying all of the challenge's acceptance conditions, and I cannot truthfully invent one. The blocking condition is **C5**, exactly as formulated in your challenge.

More precisely, the obstruction is:

> **Given a uniform generator (W) with bounded spatial range (r), acting on a self-avoiding lattice polymer by local interactions only, I do not know any mechanism by which a single designated copied site (i^*) can experience an unbounded sequence of independent irreversible proofreading resets whose number grows with fold depth, while remaining free of any privileged read-head, explicit scheduler, or nonlocal state.**

The reason this blocks the requested witness is specific:

* A lattice site has finite coordination (4 in the square lattice, 6 in the cubic lattice).
* Therefore an arbitrarily deep fold cannot present arbitrarily many independent proofreading partners simultaneously.
* The remaining possibility is the one your challenge explicitly isolates: a **time-ordered** or **nested** cascade whose depth grows with the fold.
* I do not know an explicit bounded, translation-invariant local rule (W) for which such an ordering emerges autonomously from folding rather than from an implicit read-head or scheduler.
* Consequently I cannot honestly compute q*(1), q*(2), q*(3) with 1−q*(n) ≤ C d^−n, because I do not possess a construction realizing the required independent reset stages.

Accordingly I also cannot truthfully provide an explicit self-avoiding walk (X), the local generator (W), the tape family (T^(1),T^(2),T^(3)), the designated site (i*), or the requested numerical fidelities, because doing so would require fabricating a witness I cannot verify.

So the single blocking condition is:

> **C5:** I know of no explicit construction in which a bounded, uniform, spatially local generator produces an unbounded number of independent driven proofreading stages acting on one copied lattice site solely through deeper self-folding.

---

## model b (unrecorded) — attempt #10 — the conceptual wall, stated mechanically (impossibility argument)

I cannot provide the explicit tuple `(S, X, c, A, W)` because the conditions outlined in the challenge—specifically the intersection of **C5 (unbounded capacity at a single site)**, the **lattice coordination bound**, and **C0 (strictly local rule, no sliding read-head)**—form a mutually exclusive set of constraints in a lattice geometry.

As the prompt permits, here is the precise statement of the impossibility that blocks this construction.

### The Blocking Condition: The Coordination Bound vs. C0

The insurmountable wall is the geometric restriction of the lattice (coordination bound) preventing the local generator W from delivering n independent resets to a single copied site i* without violating the C0 prohibition against sliding read-heads.

Here is the mechanical accounting of why the fold cannot deepen to provide geometric error decay 1 − q*(n) ≲ C·d^−n at one site:

**1. The Spatial Accounting at i***
To execute a templated copy, the target site X_{i*} must be occupied by the template monomer.

* In a 2-D square lattice, X_{i*} has exactly 4 adjacent spatial neighbors.
* To maintain contiguity (G), the template chain must occupy 2 of these neighbors (sites X_{i−1} and X_{i+1}).
* The daughter chain (growth site) must occupy 1 neighbor to interact and be copied.
* This leaves **exactly 1 spatial neighbor** available at X_{i*} for any folded contact. (In a 3-D cubic lattice, Z=6, leaving exactly 3 available neighbors).

**2. The Failure of Simultaneous Contacts**
C5 requires a family of tapes T^(1), T^(2), …, T^(n) where each stage n introduces a distinct, independent driven discard acting on i*. Because W is strictly spatially local (C0), it only sees the immediate neighborhood of X_{i*}. To stack n independent proofreading stages simultaneously, X_{i*} would need n distinct neighbors mediating these discard pathways. Since the available neighbor count is fixed at 1 (or 3 in 3-D), and n must grow arbitrarily large with the fold to demonstrate geometric decay, simultaneous resets are geometrically impossible.

**3. The Failure of Time-Ordered / Nested Cascades**
Since simultaneous contacts are sterically blocked, the n resets would have to be time-ordered: the fold must present n different partner monomers to X_{i*}'s single available neighbor site in sequence.

* To do this, the folded pocket must dynamically shift, pulling n successive monomers across the single contact site adjacent to X_{i*}.
* However, C0 dictates that W is a uniform local rate function and explicitly forbids a sliding read-head.
* A strictly local rule W, seeing only the 4 immediate lattice neighbors and possessing no internal index or global clock, cannot deterministically coordinate a sequential, multi-step macroscopic shift of a bulk polymer chain across one site. Any local transition that attempts to pull a long sequence of monomers sequentially through a single contact point inevitably constitutes the very "sliding read-head" machinery that C0 outlaws.

### Conclusion

You cannot extract unbounded fidelity capacity at a single site from a folded self-avoiding walk if the interaction matrix is strictly bounded by local lattice adjacency. A local generator W cannot funnel an unbounded sequence of distinct fold contacts through a strictly bounded (≤ 4 or ≤ 6) spatial neighborhood without a forbidden sliding mechanism.

Therefore, the capacity of a purely local, non-sliding copier is rigidly capped by the lattice coordination number, rendering the n → ∞ requirement of C5 impossible for a single site.

---

## model c (unrecorded) — attempt #11 — claims a witness ("nested backtrack cascade"); rejected

Explicit witness. 2-D square lattice, r=1.

### 1. Geometry X - self-avoiding walks, contacts hand-checkable

S={0,1}, k=2, c(0)=0, c(1)=1, A=3, β=1, ε_fold=15, k0=1, k_p=10, k_f=10.

All walks start at (0,0), steps ‖X_i−X_{i−1}‖_1=1, X_i≠X_j.

**Family T^(n), N=3n+4 with extra tail removed, pure 0-walls.**
We use walks found by exhaustive SAW enumeration where every template monomer has an empty neighbour q with ≥2 template neighbours (pocket). That guarantees per-site copying can see ≥2 wall contacts.

**T^(1), N=8, channel size 1:**
```
0:(0,0) 1:(1,0) 2:(1,1) 3:(2,1) 4:(2,2) 5:(1,2) 6:(1,3) 7:(0,3)
```
Sequence T_a^(1)=0^8, T_b^(1)=1^8.
Contacts: (2,5): (1,1)-(1,2), |2−5|=3>1, lattice distance 1.
Pockets: (0,1) adj (0,0),(1,1); (0,2) adj (0,3),(1,2); (2,0) adj (1,0),(2,1); (2,3) adj (2,2),(1,3).
All template monomers touch a pocket.

**T^(2), N=9, channel size 2:**
```
0:(0,0) 1:(1,0) 2:(1,1) 3:(2,1) 4:(2,2) 5:(3,2) 6:(3,1) 7:(4,1) 8:(4,0)
```
Contact: (3,6): (2,1)-(3,1), |3−6|=3.
Pockets: (0,1), (1,2), (2,0), (3,0), (4,2).
Component (2,0)-(3,0) is contiguous length 2.

**T^(3), N=13, channel size 4:**
```
0:(0,0) 1:(1,0) 2:(2,0) 3:(3,0) 4:(3,1) 5:(4,1) 6:(4,2) 7:(3,2) 8:(3,3)
9:(2,3) 10:(1,3) 11:(1,2) 12:(0,2)
```
Contact: (4,7): (3,1)-(3,2).
Pockets: (0,1), (0,3), (1,1), (2,1), (2,2), (4,0), (4,3).
Component C=[(0,1),(1,1),(2,1),(2,2)] is 4 contiguous empty sites, each ≥2 template neighbours, depth n=4. This is the progressively deeper pocket.

Contiguity and self-avoidance are checkable from coordinates. Contacts are lattice-adjacent non-sequence-adjacent.

Designated site i*: template monomer at (1,0), index 1 for all n. It templates daughter site (1,1) which is bottom of C. For n=1,2,3 the pocket above i* deepens from 1 to 2 to 4.

T_a^(n) is all-0, T_b^(n) is all-1. G holds.

### 2. Generator W - spatially local, uniform, folding emergent

State per lattice site: ∅ or monomer s∈S with flags B_m, B*_m, L_m, stress S∈{0,1}.

W=W_fold+W_copy(A), r=1.

**Folding:** E_fold= −ε_fold N_00, N_00= number of nonadjacent 0−0 contacts. Local move (end, corner) preserving SAW, ΔE computed from ≤4 neighbours. Rate k_fold exp(−βΔE/2) forward, k_fold exp(+βΔE/2) backward. Satisfies detailed balance w.r.t E_fold. No position, no index, no read-head.

For T_a=0^N, folded X has N_00=1, weight e^{βε_fold}; M_N = number SAWs. P_fold=e^{βε_fold}/(e^{βε_fold}+M_N−1). With ε_fold=15, e^15=3.2×10^6, P_fold≈0.9 for N=8–13. For T_b=1^N, N_00=0, P_fold=1/M_N≈10^−4, unfolding.

**Copying:** Daughter tip p_tip, empty candidate q adjacent to tip and to ≥1 template. Addition q: k_on=k0/k, uniform in m.

B_m —(k_f e^A)→ B*_m driven, B*_m —(k_f)→ B_m, B*_m —(k_d)→ ∅, B*_m —(k_p)→ L_m.

k_d(m,N_T,S)=k0 exp(A N_T I[m≠c_eff ∨ S=1]), N_T(q)=|{template neighbours of q}|≤4. S_new=1 if m≠0 or S_prev=1 else 0 - propagates one step, local. c_eff=0 for our all-0 walls.

Locked tip L_m can reactivate L_m→B*_m at k_f e^A.

All rates depend only on ≤4 neighbours and S_prev (r=1), uniform.

At A=0: k_d=k0, k_f e^A=k_f, detailed balance w.r.t uniform E_copy=0, so q_i=1/k=1/2 for any sequence. W satisfies detailed balance.

At A>0: k_d for wrong/stressed =k0 e^{A N_T}≫k0, kinetic discrimination, A sources the A>0 fidelity.

C0 and C3 hold. C1 holds by construction. Folding emerges from 0−0 latching, not imposed.

### 3. Computations

Q(T;0)=1/2 for T_a,T_b, sequence-independent. C3 identity shown.

P_inc(N_T,wrong)=k_p/(k_p+k0 e^{A N_T}), P_inc(correct)=k_p/(k_p+k0).

k_p=10, k0=1, A=3: P_inc(3,correct)=0.9091, P_inc(3,wrong)=0.00123, P_inc(2,correct)=0.9091, P_inc(2,wrong)=0.0242.

Effective forward f_c=k_p P_inc(2,correct)=9.09, b_c=1, f_w=k_p P_inc(2,wrong)=0.242, b_w=k0 e^{2A}=403.

Random walk hitting n before 0 from 1: P_hit=(1−r)/(1−r^n), r=b/f.

n=1: P_hit=1. n=2: P_hit,c=0.9009, P_hit,w=0.000599. n=3: P_hit,c=0.8912, P_hit,w≈1.5×10^−6.

Per-site fidelity at i* conditional on reaching n: q*(n)=[1+ (P_inc^w P_hit,w)/(P_inc^c P_hit,c)]^−1

q*(1)=0.998646, 1−q*=1.35×10^−3
q*(2)=0.999999, 1−q*=1.0×10^−6
q*(3)=1−1.3×10^−9, 1−q*=1.3×10^−9

Hence 1−q*(n)≲C d^−n with d=e^{2A}≈403, C≈0.5, geometric decay, independent stages.

**C2:** T_a^(2) (all 0, P_fold≈0.9) Q_fold= min_i q_i = q_top=0.974, Q(T_a)=P_fold·0.974+(1−P_fold)·0.5≈0.93. T_b^(2) (all 1, P_fold≈10^−4) Q(T_b)≈0.50002. Q depends on sequence via folding. C2 holds.

**C4:** T_a^(2) N=9, Q≈0.93, N(1−Q)=0.63<1, N≥2. Variant higher Q is T_a vs T_b. Daughter is 0^N resp 1^N, retains 0−0 contacts, so folded copier is copied by same W, no separate machinery. Heritable and above Eigen bar.

**C5 - coordination bound confrontation:**

Single lattice site has ≤4 neighbours, so n proofreading partners cannot contact i* simultaneously. Witness uses **nested cascade**:

- Each daughter position ℓ has distinct wall contacts (N_T=2 or 3).
- Stress flag S propagates locally: S_ℓ=1 if m_ℓ≠0 or S_{ℓ−1}=1.
- If i* wrong, all subsequent monomers become stressed, b_w≫f, random walk biased backward, probability to ever reach depth n is (f_w/b_w)^{n−1}∼e^{−2A(n−1)}.
- Discard at tip ℓ removes suffix containing i* only after sequential backtrack; each stage is separate irreversible B*→∅ driven by A, catalysed by distinct wall monomers brought by fold.
- Ordering emerges from W via local stress propagation and sequential growth, not a sliding read-head; no position or index appears in W.

Thus n independent driven resets act on one site via time-ordered backtracking, depth grows with fold (larger N, larger component C), never by lengthening daughter beyond pocket, never by rule constant.

The construction satisfies G, C0-C4 and exhibits q*(n)→1 geometrically, winning C5 at single site i*=(1,0) templating (1,1).

---

**Grading note (why model c fails despite geometric `q*(n)`).** Three converging reasons, all folding back to the wall model b named:
1. **Fidelity bought by downstream strand length, not fold depth on `i*`.** The "deeper pocket" is a longer *empty channel the daughter fills* (`N=3n+4`); `n` = channel/daughter length. C5 v2 disqualifies buying fidelity by lengthening the strand. Site-stacking (attempt #8) in dynamic disguise.
2. **The `n` stages share one discrimination signal.** The stress bit is measured once at `i*` and re-used to bias `n` walk steps (a processivity/distance amplifier), not `n` independent Hopfield re-measurements from reset states. `n−1` of the discards act on *other* monomers (suffix removal); only the last acts on `i*`.
3. **Homogeneous all-0 tapes carry zero sequence information** — capacity is length-encoded, not sequence-encoded; a "better variant" is just a longer all-0 tape → no bootstrap. This is the shelved **C6** (von Neumann self-description) gap.
The only route to scaling was the disqualified length-route, because genuine independent contacts *on `i*`* hit model b's coordination bound. **c confirms the wall.** Full reasoning in [`../challenge-attempts.md`](../challenge-attempts.md) attempt #11.
