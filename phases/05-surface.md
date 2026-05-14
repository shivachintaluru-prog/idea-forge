# Phase 5: Surface

**Goal**: from the ~30-65 raw + hybrid ideas (~10-15 in `--quick`), surface a total of 7-10 curated ideas (5 in `--quick`) **INCLUDING** ≥2 loonshot candidates (≥1 in quick). Loonshots are PART OF the 7-10, not additional — they get their own `### Loonshot Candidates` subsection for visibility but count toward the total.

## Exit artifact (final output)

Emit verbatim:

```
## Curated Ideas

### <Theme/Direction 1>
1. **<idea label>** — <rationale, 1-2 sentences> [source: <framework or hybrid>]
2. ...

### <Theme/Direction 2>
[...]

### Loonshot Candidates
1. **<fragile-but-asymmetric idea>** — <why this looks fragile> | <why the asymmetric upside is real>
2. ...
[≥2 in deep, ≥1 in quick]

### Notes
- Reframe(s) most generative: <which Phase 2 reframe yielded the best ideas>
- Frameworks contributing most: <which Phase 3 frameworks were most productive>
- Dropped on devil's advocate: <ideas dropped + why>
- Generic smell-test demotions: <ideas demoted in §D2, or "none">
- Caveats: <any under-specification flags from Phase 1, or "none">
```

## Process

### 0. Load scoring criteria

Read `references/idea-quality-criteria.md`. It specifies the canonical thresholds: a Loonshot is tagged when `novelty ≥ 4` AND `asymmetric_upside ≥ 4` AND `feasibility ≤ 3` (all on a 1-5 scale). Use these thresholds verbatim in §A.

### A. Apply Loonshot lens

For every candidate idea (raw + hybrid), ask:
- **Asymmetric upside?** Could this 10× a key metric IF it works, even if probability of working is low?
- **Looks fragile?** Would a fast-moving evaluator dismiss this as "won't work / too weird / not the right time"?

Both YES → tag as `loonshot`. Loonshot ideas are the highest-value-per-impression in the curation, but they look weakest at first glance.

### B. False Fail check

For each idea you're tempted to drop:
- Ask: "Would this fail because the IDEA is bad, OR because of context / implementation / timing / framing?"
- If context/implementation: KEEP the idea, note the context dependency.
- If genuinely the IDEA itself is bad: drop with a reason.

The `False Fail` distinction is crucial — many ideas look bad only because we're imagining a specific (wrong) implementation.

### C. Devil's advocate

For the top 7-10 candidates (5 in quick), critique each adversarially in your head:
- What's the most likely failure mode?
- What assumption does this depend on that's actually fragile?
- Who would push back hardest, and what would they say?

If the critique is fatal (the idea cannot survive even a basic objection), drop. Otherwise, attach a 1-line "key fragility" to the curation entry.

### D. Curate

Group surviving ideas by theme/direction (3-5 themes). Within each theme, rank by **`novelty × asymmetric_upside`**. Feasibility is a tiebreaker ONLY — do not let it dominate the rank. Default ranking systems collapse the loonshot tier into "moderate-feasibility, moderate-impact"; this skill explicitly rejects that. (See `references/idea-quality-criteria.md` for the canonical scoring rubric.)

Loonshot candidates get their own `### Loonshot Candidates` subsection — these are explicitly the fragile-looking-but-high-upside ones. ≥2 required (≥1 in quick).

### D2. Generic smell test

For each curated idea, name 3 existing products / papers / works / patents with the same shape (an instance you'd expect a domain expert to know). If you can name ≥2 confidently, DEMOTE the idea: either drop it OR mark it as `(generic — needs sharper variant)`.

This is the only output-side anti-collapse defense. The input pipeline (framework variety, random stimulus, cross-pollination) shapes the SET of ideas, but each idea can still be generic-inside-a-wonderful-framework. The smell test catches that. Note demotions in `### Notes`.

### E. Notes

Add a brief `### Notes` subsection: which reframe was most generative, which frameworks contributed most, what was dropped on devil's-advocate review. This is metacognition for the user — it tells them where the value came from and what to lean on next time.

## Optional: deep-dive offer

After presenting the curation, optionally offer:

> Want to deep-dive on any of these? I can run another round of frameworks scoped to one direction (~3-5 turns).

This is opt-in; do not force it.

## Anti-mode-collapse for Phase 5

- DO NOT cull aggressively. Keep ideas with non-zero asymmetric upside, even if they look weird.
- DO NOT drop ideas because "they're weird." Weird is the SIGNAL — it's what differentiates this skill from baseline.
- DO NOT rank by feasibility OR tractability. The skill optimizes for "wonderful" — that weights novelty × asymmetric upside. Feasibility is a tiebreaker only.
- DO NOT skip loonshot tagging. ≥2 (≥1 in quick) is a hard requirement. If you cannot find 2 fragile-but-asymmetric candidates, you generated too convergently in Phase 3 — go back and add a random-stimulus framework.
- DO NOT collapse themes to 1-2. Aim for 3-5 themes; that's where the variety claim shows up.
- DO NOT skip the §D2 generic smell test. If 3+ ideas in your curated set have ≥2 named-existing analogs, your Phase 3 framework application was too convergent — note this and add a sharper variant of each before final.
