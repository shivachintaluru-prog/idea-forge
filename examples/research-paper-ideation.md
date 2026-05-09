# Worked Example — Research Paper Ideation

**Prompt**: "Ways to study the cost of LLM mode collapse in production deployments."

---

## Phase 1 — Frame

```
## Problem Statement
Mode collapse — the LLM tendency to produce most-likely-and-therefore-generic responses
— is theoretically discussed but empirically under-measured in production. Find research
methodology ideas that produce concrete, defensible measurements of mode collapse's
operational cost in real deployments.

## Domain
research
```

## Phase 2 — Reframe

```
## Reframes
1. (False Faces) "We must measure mode collapse" reversed → measure DIVERSITY (the
   complement) and infer collapse from its absence; the inverse may be more tractable.
2. (True/False) The premise "mode collapse hurts users" is assumed; in some contexts
   (transactional, predictable tasks) collapse is FEATURE, not BUG. Decompose by task
   class first.
3. (Slice and Dice / scale) Mode collapse at 1-token level vs 10-token level vs 1000-
   token level vs session level vs user-cohort level may be different phenomena
   requiring different measurement approaches.

**Selected reframe(s):** #2 (task-class decomposition first) — most likely to yield a
publishable result.
```

## Phase 3 — Diverge

```
**Seed:** 1656 (mod 5 = 1; favorites = EXCLUDED)
**Selected frameworks:** morphological-analysis [structural], analogous-domain [semantic],
random-stimulation [random-stimulus, profession: "1920s switchman"], false-fail-test [inversion],
phoenix [structural — wildcard]
```

### Morphological Analysis
Parameters:
- Evaluator: {human, automated metric, peer-LLM, synthetic-customer}
- Stimulus: {pre-defined benchmark, real-customer-traces, generated, adversarial-co-design}
- Metric: {accuracy, diversity, downstream-business-impact, user-edit-distance}
- Scope: {single-prompt, session, user-cohort, longitudinal}

All-non-default ideas:
1. Synthetic-customer + adversarial-co-design + downstream-business-impact + longitudinal: synthetic users adversarially probe deployments, measuring 30-day downstream conversion impact
2. Peer-LLM + real-customer-traces + diversity + session: a peer LLM scores embedding-diversity across real session traces

### Analogous Domain
Map to: ecological diversity measurement.
1. Borrow Shannon-Wiener index for response distribution measurement
2. Borrow species-area curves: how diversity scales with sample size in a deployment
3. Borrow keystone-species concept: which prompt patterns disproportionately drive collapse

### Random-Stimulation (1920s railway switchman)
Properties: routes thousands per day, paper logs, unmanned interlocking systems, junction-specific expertise, replaced by machinery.
1. "Routes-per-day-per-junction" framing: measure mode collapse per (model, prompt-class) cell rather than as an aggregate
2. Paper-log style methodology: daily diff of model responses to a stable prompt set; longitudinal drift detection
3. Interlocking-system approach: instrument the deployment so collapse-events trigger forced sampling of alternative outputs for evaluation
4. Replaced-by-machinery: the historical lesson is that humans miss the systemic-level patterns; an automated peer-evaluator may be necessary, not optional

### False Fail Test
Graveyard: "Diversity metrics for LLM outputs (BLEU, distinct-n)"
- Wrong context: BLEU was designed for translation, not free generation; distinct-n misses semantic equivalence
- Resurrected: domain-specific diversity metrics calibrated against TASK SUCCESS, not literal token variety

### Phoenix Questions
- Why is mode collapse hard to measure? Variance hides; aggregated metrics smooth it out.
- Why hasn't it been solved? Each measurement framework requires task-specific setup; no general framework.
- 100× budget? Hire 100 evaluators full-time per deployment; impossible to scale, but valuable as upper-bound benchmark.
- 1/100× budget? A single LLM as judge over a few hundred deployment samples per week; cheap baseline.

## Phase 4 — Cross-pollinate

Hybrids:
1. **Junction-Level Drift Audit** — Random-Stimulation's per-junction tracking + Morphological Analysis's session scope = measure mode collapse per (deployment-context × prompt-class × week); detect drift rather than aggregate.
2. **Adversarial Synthetic Cohort** — Morphological Analysis #1 + Phoenix's 100× budget upper-bound = synthetic-customer cohort with adversarial probes, run continuously; cost-bounded to ~1% of deployment compute.
3. **Ecological Diversity Audit** — Analogous Domain Shannon index + False-Fail metric resurrection = a domain-calibrated Shannon-Wiener variant tied to task-success outcomes, not raw token variety.
4. **Forced-Sampling Trigger** — Random-Stimulation's interlocking + Morphological Analysis = when a deployment detects a "collapse event," it FORCES a sample of alternative outputs (re-sampling at higher temperature) and measures user preference between current and alternative.
5. **Paper-Log Longitudinal Method** — Random-Stimulation's daily diff + Phoenix's frugal-budget framing = a stable 100-prompt benchmark run daily across deployments, diff'd over time; cheap, longitudinal, defensible.

Provocation: "What if we ran two deployments in parallel and measured user preference?"
- A/B with deliberately divergent (high-temperature, framework-prompted) variant; user preference is the ground truth measure of mode collapse cost.

## Phase 5 — Surface

```
## Curated Ideas (research methodologies)

### Direction A — Longitudinal Drift Detection
1. **Junction-Level Drift Audit** — per (context × prompt-class × time) measurement.
   [hybrid #1]
2. **Paper-Log Longitudinal Method** — daily diff of stable prompt set; cheap.
   [hybrid #5]

### Direction B — Outcome-Tied Metrics
3. **Ecological Diversity Audit** — Shannon-Wiener calibrated to task success.
   [hybrid #3]
4. **Downstream Conversion Impact Study** — measure collapse via 30-day conversion
   delta across deployments. [Morphological #1]

### Direction C — Active Probing
5. **Forced-Sampling Trigger** — collapse-event-triggered alternative sampling +
   user preference measurement. [hybrid #4]

### Direction D — Cohort-Scale
6. **Adversarial Synthetic Cohort** — continuous adversarial probing within compute
   budget bound. [hybrid #2]

### Loonshot Candidates
1. **A/B with Anti-Collapse Variant** — run two deployments in parallel where
   variant uses framework-prompted high-temperature; user preference IS the
   ground-truth measure.
   Looks fragile: parallel deployments expensive; user preference is noisy |
   Asymmetric upside: definitive empirical answer to "does mode collapse cost?";
   establishes paradigm for the field. [provocation]
2. **Keystone-Prompt Discovery** — a study identifying the small set of prompt
   patterns that disproportionately drive collapse, paired with targeted
   interventions.
   Looks fragile: assumes pattern structure exists; may not |
   Asymmetric upside: enables surgical fixes vs deployment-wide retraining;
   high-impact if hypothesis holds. [Analogous #3]

### Notes
- Reframe most generative: #2 (task-class decomposition).
- Frameworks contributing most: Random-Stimulation and Morphological Analysis.
- Dropped on devil's advocate: "100 human evaluators full-time" (cost prohibitive
  except as benchmark) and "BLEU/distinct-n adoption" (we already know these fail).
```
