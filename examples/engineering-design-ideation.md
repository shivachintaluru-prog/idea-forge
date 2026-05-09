# Worked Example — Engineering Design Ideation

**Prompt**: "Reduce GPU memory pressure during large-model training."

---

## Phase 1 — Frame

```
## Problem Statement
Training a 100B-param model on a fixed GPU budget. Standard memory-saving techniques
(gradient checkpointing, mixed precision, ZeRO sharding) are already applied; further
reductions require techniques outside the textbook. Find ideas that aren't in the
common training-tips lists.

## Domain
engineering
```

## Phase 2 — Reframe

```
## Reframes
1. (False Faces) "We need to fit the model in memory" reversed → memory pressure is a
   SIGNAL, not a constraint; the model doesn't need to live in memory at all.
2. (True/False) The premise "training requires gradient updates on the full graph" is
   assumed; partial-graph training, asynchronous updates, or update-on-event regimes
   are alternatives.
3. (Slice and Dice / time) Memory pressure varies enormously across the training run
   (warmup vs steady-state vs cool-down); decompose by phase rather than treating as
   one workload.

**Selected reframe(s):** #1 (memory as signal) and #3 (phase-decomposition) — both
diverge from "fit-the-model" framing.
```

## Phase 3 — Diverge

```
**Seed:** 1819 (mod 5 = 4; favorites = EXCLUDED)
**Selected frameworks:** triz-contradictions [structural], inversion [inversion],
provocation-po [random-stimulus], slice-and-dice [structural],
analogous-domain [semantic — wildcard]
```

### TRIZ Contradictions
Contradiction: improving memory headroom vs maintaining throughput.
1. Time separation: aggressive offloading during gradient accumulation, full-resident during forward pass
2. Space separation: hot params on GPU, cold params on NVMe with paged-attention-style fetch
3. Part/whole separation: each layer fragile (offloads aggressively); the system robust because layer 1 prefetches while layer N computes
4. Condition separation: memory regime switches based on entropy of recent gradients (high entropy → less offloading; low entropy → aggressive)

### Inversion
"How would we GUARANTEE catastrophic memory pressure?"
- Materialize the full computation graph at every step
- Keep all activations forever
- Random reordering across devices

Inverses:
1. Don't materialize what isn't needed yet (lazy, demand-driven)
2. Activation tournament: keep only the activations whose downstream use was unpredictable
3. Stable-route placement: pre-compute layer-to-device assignment based on memory profile, lock for the run

### Provocation-PO
- Po: GPUs share memory across nodes via a shared address space (impossible at speed today, but explore the idea)
  - Idea: a "compute-at-memory" model where layers migrate to where the activations live, not vice versa; reduces transfers
- Po: training uses no gradients
  - Idea: gradient-free fine-tuning via evolutionary search on parameter subsets; fits in dramatically less memory
- Po: the model is bigger than the planet
  - Idea: hierarchical sharding where most parameters live as compressed lookups (sparse + quantized), only "active" parameters expand

### Slice and Dice (axis: training phase)
- Warmup phase (first 5%): high entropy gradients; can use lossy intermediate representations
- Steady-state (middle 90%): predictable patterns; aggressive caching of repeated computations
- Cool-down (last 5%): convergence-phase; selective high-precision updates only

### Analogous Domain (memory in operating systems)
Properties of OS memory management: virtual memory, demand paging, working sets, NUMA awareness, copy-on-write.
1. Demand paging for parameters — only load layer N when batch reaches it (already partially done; extend to sub-layer granularity)
2. Copy-on-write activation: shared activation across batches until divergent
3. Working-set tracking per training step: log which params were touched; pre-fetch on next step

## Phase 4 — Cross-pollinate

Hybrids:
1. **Entropy-Triggered Mode Switch** — TRIZ condition separation + Slice-and-Dice phase decomposition = memory regime switches automatically based on (gradient entropy AND training phase); different policies for warmup vs steady-state vs end-game.
2. **Activation Tournament** — Inversion #2 + Analogous Domain working-set = keep only activations whose downstream use was UNPREDICTABLE per the working-set tracker; predictable ones recomputed cheaply.
3. **Compute-Migrates-to-Activations** — Provocation #1 + TRIZ part/whole = layers migrate to the device where their input activations are largest; transfers are layer code (small) not data (large).
4. **Sparse-Lookup Backbone** — Provocation #3 + Analogous Domain demand-paging = main weights stored as compressed sparse + quantized lookup; "active" weights are decompressed on-demand into a small working buffer.
5. **Phase-Specific Precision** — Slice-and-Dice phase + TRIZ time-separation = warmup uses int4; steady-state uses fp8; final 5% uses fp16. Memory profile shifts dynamically.

Provocation: "What if memory pressure was the OBJECTIVE, not the constraint?"
- Memory pressure as a regularizer: training schedules deliberately operate near memory cliff to force activation reuse, generating an implicit regularization signal.

## Phase 5 — Surface

```
## Curated Ideas

### Direction A — Adaptive Regimes
1. **Entropy-Triggered Mode Switch** — auto-switching memory regime based on (entropy
   AND phase). Concrete: a controller that watches gradient stats. [hybrid #1]
2. **Phase-Specific Precision** — int4 warmup → fp8 steady-state → fp16 cooldown.
   [hybrid #5]

### Direction B — Working-Set Optimization
3. **Activation Tournament** — keep only unpredictably-used activations.
   [hybrid #2]
4. **Demand-Paging Sub-layer** — paging at finer granularity than layer-level.
   [Analogous Domain #1]

### Direction C — Topology
5. **Compute-Migrates-to-Activations** — layer code migrates to data, reverses normal
   transfer pattern. [hybrid #3]

### Direction D — Storage Form
6. **Sparse-Lookup Backbone** — compressed sparse + quantized lookup as main store.
   [hybrid #4]

### Loonshot Candidates
1. **Memory Pressure as Regularizer** — operate deliberately near memory cliff to
   force activation reuse and implicit regularization.
   Looks fragile: deliberate near-OOM is operationally scary |
   Asymmetric upside: simultaneously reduces memory AND improves generalization;
   if validated, becomes default practice. [provocation #1]
2. **Gradient-Free Fine-Tuning at Scale** — evolutionary search on parameter
   subsets, no backprop required for fine-tuning.
   Looks fragile: search-based tuning at billions of params seems infeasible |
   Asymmetric upside: opens fine-tuning to 10× larger models on 1× hardware;
   different scaling regime. [provocation #2]

### Notes
- Reframes most generative: both #1 and #3 contributed.
- Frameworks contributing most: Provocation-PO and TRIZ Contradictions.
- Dropped on devil's advocate: "shared address space across nodes" (latency makes
  it dominant by 100×) and "all activations forever" (obviously impossible).
```
