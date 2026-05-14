# Phase 3: Diverge

**Goal**: generate 25-50 raw ideas (10-15 in `--quick`) using 4-5 frameworks selected for variety (2 in `--quick`).

## Exit artifact (required before Phase 4)

Emit verbatim:

```
## Raw Idea Dump
1. <idea — 1 sentence, no commentary>
2. ...
... (≥10 ideas, NO framework labels, NO judgment phrasing, NO commentary — just ideas)
```

Then below it:

```
## Raw Ideas

### <Framework Name 1>
1. <idea — 1-2 sentences>
2. ...
[5-10 ideas]

### <Framework Name 2>
[5-10 ideas]

[continue for all selected frameworks]
```

Optional post-artifact (strongly recommended) at the END of Phase 3, after the per-framework idea blocks:

```
### Graveyard
1. <idea you nearly dropped> — <1-sentence dismissal reason>
2. ...
3. ...
[≥3 entries; revisited by Phase 5's False Fail check]
```

## Process

### 0. Emit the flat raw dump

Before applying frameworks, emit ≥10 ideas as a flat numbered list under `## Raw Idea Dump`. No commentary. No filtering. No grouping. This artifact is the OBSERVABLE PROOF that judgment was deferred (anti-mode-collapse mechanism #2). The dump is independent of the per-framework lists below; it is NOT the same content reorganized.

### A. Select frameworks via the deterministic algorithm

Read `frameworks/INDEX.md` and apply:

1. Filter `frameworks/*.md` where `domain-fit` includes the detected domain (from Phase 1).
2. Group the filtered set by `constraint-type` from each framework's frontmatter: one of `{semantic, structural, random-stimulus, inversion, temporal}`.
3. Compute the seed per the canonical recipe in `frameworks/INDEX.md` Step 3. Record BOTH derived values in your reasoning: `seed mod 5` (type-drop modulus, used in Step 5) AND `favorites_value` = `(seed // 13) mod 7` (favorites gate, used in Step 4). Report as `**Seed:** <n> (mod 5 = <m>; favorites_value = <f>; favorites = <allowed | excluded>)`.
4. **Favorites-bias filter**: if `favorites_value == 0`, allow frameworks marked `favorites-bias: true` (SCAMPER, Six Hats, JTBD, first-principles, inversion, blue-ocean-errc — see catalog). Otherwise EXCLUDE them. (This prevents Claude's training-frequency bias from collapsing every session onto the same favorites.)
5. Selection draws (use `seed` for which-of-each pick):
   - **Deep**: 1 framework from each of 4 distinct constraint-types + 1 wildcard from any remaining framework. Total: 5.
   - **Quick**: 1 framework from each of 2 distinct constraint-types. Total: 2.
6. Verify the result covers ≥3 distinct constraint-types (≥2 in quick). If short, redraw the wildcard from a constraint-type not yet represented.

State the picks in the conversation as `**Selected frameworks:** <list with constraint-type tags>` so the user can see the diversity.

### B. Apply each selected framework

For each selected framework, in order:

1. Read the framework file at `frameworks/<name>.md`.
2. Apply its `## Anti-mode-collapse prompts` LITERALLY before generating. These prompts force you out of obvious territory.
3. Generate 5-10 ideas using the framework's specific constraints. Each idea is 1-2 sentences. Use the framework's `## Output format`.
4. DO NOT evaluate ideas during generation. No "but would this work?" — judgment is deferred to Phase 5.

### C. Quantity-quota enforcement

After all frameworks are applied, verify totals:
- Deep: ≥25 ideas
- Quick: ≥10 ideas

If short, distribute the deficit: add 1 idea each to the lowest-yield frameworks (one round). If still short, re-draw a NEW framework via the algorithm (use `seed + 1` to avoid duplicate picks) and apply it for 5 more ideas. Do NOT pile 3+ extra ideas onto a single framework — that compounds mode collapse within that framework's constraint.

### D. Emit the Graveyard

At the end of Phase 3, optionally (but strongly recommended) emit a `### Graveyard` block listing ≥3 ideas you were tempted to drop, each with a 1-sentence dismissal reason. Phase 5's False Fail check will revisit them — many "obvious failures" survive that check. This artifact is the OBSERVABLE PROOF that judgment was deferred (mechanism #10).

## Anti-mode-collapse for Phase 3

- The Raw Idea Dump (≥10 ideas, pre-framework) is the ARTIFACT-LEVEL enforcement of mechanism #2 (quantity quota before judgment). Without it, mechanism #2 is exhortation-only.
- DO NOT skip the deterministic algorithm and pick frameworks "by feel." That collapses to favorites.
- DO NOT cluster ideas in your head. Output them flat. The structure of the artifact (numbered list per framework) defeats the urge to silently de-duplicate.
- DO NOT shrink lists ("I'll just give 3, the user will get the idea"). Hit the quota; quantity defeats convergence.
- DO NOT reuse the same example template across frameworks. Each framework imposes a different constraint type — the outputs should look structurally different from each other.
- DO NOT explain the framework first and then generate. Just generate using the framework's prompts. Explanation is convergence-toward-tutorial.
