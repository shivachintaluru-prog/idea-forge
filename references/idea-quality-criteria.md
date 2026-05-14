# Idea Quality Criteria

The skill targets "wonderful" ideas. The criteria below define what wonderful means operationally for Phase 5 curation.

## The criteria

A wonderful idea scores well on:

### 1. Novelty
- Would a domain expert say "I haven't heard this before"?
- Does it use a mechanism, not just a label, that wasn't in the candidate's mental "what's been tried" set?
- Does it require a NEW WORD or NEW PHRASE to describe accurately, because the existing vocabulary doesn't fit it?

A high-novelty idea is one whose category isn't pre-existing.

### 2. Asymmetric upside
- IF this idea works, what's the magnitude of the win? (1×, 10×, 100×?)
- IF it doesn't work, what's the cost? (Time? Reputation? Locked-in resources?)
- The asymmetric ratio = upside-magnitude / downside-cost. Higher = more wonderful.

Asymmetric upside is the loonshot signal. Most "feasible" ideas have ratios near 1; the wonderful ideas have ratios of 10+.

### 3. Feasibility (tiebreaker only — NOT primary)
- Could a small team test the central uncertainty in <30 days for <$10K (or analogous low-resource bound)?
- Is there a clear "first experiment" that meaningfully discriminates between the idea working and failing?
- Are there forcing-function constraints (regulation, physics, economics) that would prevent ANY version of the idea from working?

Feasibility is a TIEBREAKER, not a primary criterion. Phase 5 must NOT rank by feasibility first — that destroys the asymmetric-upside signal. Use it only to break ties among ideas that score equally on novelty + asymmetric-upside.

## How to score in Phase 5

For each candidate idea, assign rough scores 1-5 on:
- Novelty: 1 = familiar / well-known; 5 = requires new vocabulary
- Asymmetric upside: 1 = ratio < 2; 5 = ratio > 20
- Feasibility: 1 = requires major change; 5 = testable next week

Composite: `(novelty * asymmetric_upside) + (0.2 * feasibility)`. The multiplicative novelty × asymmetric_upside privileges ideas that are simultaneously novel AND high-upside. Feasibility is a small additive tiebreaker.

The TOP 7-10 (5 in quick) by this composite are the curated set.

## Loonshot tagging

Independent of the score, tag any idea where:
- Novelty ≥ 4 AND
- Asymmetric upside ≥ 4 AND
- Feasibility ≤ 3 (i.e., would be dismissed by feasibility-first thinking)

These are the LOONSHOT candidates. ≥2 must appear (≥1 in quick). They are explicitly highlighted in the curation as the fragile-but-asymmetric tier.

## Anti-mode-collapse for quality criteria

- Do NOT use feasibility as the primary ranker. The whole skill is structured to fight that default.
- Do NOT silently exclude ideas with novelty 5 because "they're too weird." The skill is explicitly weird-tolerant.
- Do NOT inflate novelty scores to feel productive. Score honestly; if all ideas are novelty 2-3, Phase 3 was convergent — return and add a `random-stimulus` framework.
- Loonshot ideas that look "obviously bad" should still be tagged if they pass the criteria above. The False Fail check (in Phase 5) reframes the apparent badness.

---

Phase 5 (`phases/05-surface.md`) is the consumer of this file. It MUST read this before scoring. The canonical formula is repeated in `phases/05-surface.md` §0.
