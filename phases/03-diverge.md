# Phase 3: Diverge

**Goal**: generate 25-50 raw ideas (10-15 in `--quick`) using 4-5 frameworks selected for variety (2 in `--quick`).

## Exit artifact (required before Phase 4)

Emit verbatim:

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

## Process

### A. Select frameworks via the deterministic algorithm

Read `frameworks/INDEX.md` and apply:

1. Filter `frameworks/*.md` where `domain-fit` includes the detected domain (from Phase 1).
2. Group the filtered set by `constraint-type` from each framework's frontmatter: one of `{semantic, structural, random-stimulus, inversion, temporal}`.
3. Compute `seed`:
   - Concatenate `<problem_statement> + <selected reframe>`.
   - Compute a stable hash. Simple recipe: sum the Unicode codepoints of every character, mod 2^32.
   - Record `seed` and `seed mod 5` in your reasoning so the user can verify determinism.
4. **Favorites-bias filter**: if `seed mod 5 == 0`, allow frameworks marked `favorites-bias: true` (SCAMPER, Six Hats, JTBD). Otherwise EXCLUDE them. (This prevents Claude's training-frequency bias from collapsing every session onto the same 3 frameworks.)
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

If short, return to whichever framework yielded fewest ideas and generate 3 more by re-applying its anti-mode-collapse prompts.

## Anti-mode-collapse for Phase 3

- DO NOT skip the deterministic algorithm and pick frameworks "by feel." That collapses to favorites.
- DO NOT cluster ideas in your head. Output them flat. The structure of the artifact (numbered list per framework) defeats the urge to silently de-duplicate.
- DO NOT shrink lists ("I'll just give 3, the user will get the idea"). Hit the quota; quantity defeats convergence.
- DO NOT reuse the same example template across frameworks. Each framework imposes a different constraint type — the outputs should look structurally different from each other.
- DO NOT explain the framework first and then generate. Just generate using the framework's prompts. Explanation is convergence-toward-tutorial.
