# Phase 4: Cross-pollinate (mandatory gate; SKIP in `--quick`)

**Goal**: generate ≥5 hybrid ideas by force-combining ideas from different frameworks. This phase produces ideas no single framework can generate.

**In `--quick` mode**: skip Phase 4 entirely; proceed straight to Phase 5.

## Exit artifact (required before Phase 5; deep mode only)

Emit verbatim:

```
## Hybrid Ideas
1. **<short label>** — <hybrid idea description, 1-2 sentences> (sources: <Framework A idea #X> + <Framework B idea #Y>)
2. ...
[≥5 hybrids TOTAL, including §B force-combined pairs + §C worst-possible-derived insights + §D provocation-derived ideas]
```

## Process

### A. Compress raw ideas (token-budget protection)

Before cross-pollinating, compress Phase 3's `## Raw Ideas` into a brief table:

| Framework | Top 3 idea labels (one-liners) |
|---|---|
| <Framework A> | <#1>, <#2>, <#3> |
| ... | ... |

This frees context for Phase 4 + Phase 5 work.

### B. Force-combine pairs (≥5 pairs in §B alone — these are the floor, additional hybrids come from §C and §D)

For at least 5 pairs:

1. Pick 1 idea from Framework A + 1 from Framework B where the two frameworks have DIFFERENT `constraint-type` tags.
2. Ask: "What would a real implementation look like if it satisfied BOTH constraints simultaneously?"
3. Write the hybrid in 1-2 sentences.
4. Pair-selection bias: prefer pairs from constraint-types FARTHEST apart (e.g., `random-stimulus` + `structural`, NOT `semantic` + `semantic`).

The hybrid must produce a NEW property neither parent had alone. If the "hybrid" is just A-plus-B with no synthesis, it's not really a hybrid — drop it.

### C. Worst Possible Idea pass

**Skip rule**: If `worst-possible-idea` was among Phase 3's selected frameworks, skip §C entirely — that framework already produced this output. Note the skip in Phase 5's `### Notes` (e.g., "Phase 4 §C skipped because worst-possible-idea was a Phase 3 framework"). Proceed directly to §D.

1. From Phase 3 outputs, list 3 ideas you'd reflexively dismiss as bad.
2. For each, ask: "What's actually TRUE about this idea? What would have to be different for this to work?"
3. The insights that emerge become additional hybrid ideas. Of the 3 dismissed ideas, AT LEAST 1 must yield a numbered entry in `## Hybrid Ideas` (alongside §B force-combined pairs). Mark it with `(from §C)` so Phase 5 can trace lineage.

This is inversion-driven creativity — the dismissed ideas often have a kernel of truth that doesn't show up in "good" ideas.

### D. Provocation step (PO operator)

1. Pick 1 deliberately absurd statement: "What if [opposite of an obvious assumption]?" or "What if this had to use [completely unrelated domain element — e.g., obstetrics, ant colonies, medieval guilds]?"
2. Generate 2-3 ideas that flow from the absurd statement, taking it seriously.
3. Add the surviving (coherent) ones to the hybrid list, but FIRST emit the provocation's literal text as a labeled block in `## Hybrid Ideas`:
   ```
   **Provocation:** "<the absurd statement>"
   <next-numbered-id>. **<surviving idea label>** — <description, 1-2 sentences> (sources: provocation)
   <next-numbered-id>. ...
   ```
The labeled `**Provocation:**` block is the artifact-level enforcement of anti-mode-collapse mechanism #5. Without it, provocation can be silently skipped (the most common skip mode).

The provocation step is where the truly novel ideas come from. It's also where Claude's mode collapse is loudest — every instinct will say "this is silly, the absurd premise gives nothing useful." Push past it.

### E. Coherence filter

Drop hybrids that are genuinely incoherent — i.e., the combination is a category mistake with no synthesis (e.g., "AI plumbing" + "subscription model" → "AI plumbing subscription" is just A-then-B, not a hybrid). Aim for hybrids where the combination IS the new thing.

Keep at least 5 hybrids. If filtering drops you below 5, re-enter step B with farther-apart pairs.

## Anti-mode-collapse for Phase 4

- DO NOT pair ideas that are conceptually close. The point is distance.
- DO NOT prematurely judge hybrids. Capture, then judge in Phase 5.
- DO NOT skip the Worst Possible Idea pass. Inversion finds value in dismissed ideas.
- DO NOT skip the Provocation step in deep mode — even when it feels pointless. That feeling IS the mode-collapse signal; the step is specifically designed to break it.
- DO NOT pick safe pairs (close constraint-types) to look productive. Distance is the engine.
