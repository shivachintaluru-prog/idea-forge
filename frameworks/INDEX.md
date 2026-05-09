# Framework Index — Selection Algorithm + Catalog

Phase 3 reads this file to select frameworks deterministically. Selection is biased AWAY from training-set favorites and FOR variety across constraint-types.

## Constraint-types

Each framework's `frontmatter constraint-type` is one of:

| Type | Mechanism |
|---|---|
| `semantic` | Transforms meaning of problem elements (substitute, recategorize, transfer across domains) |
| `structural` | Decomposes / recomposes the problem along a different axis (parts, layers, parameters) |
| `random-stimulus` | Forces distance via unrelated stimulus (random word, absurd premise, foreign domain) |
| `inversion` | Reverses, negates, or examines the dual (opposite, reverse, what would fail) |
| `temporal` | Shifts the time axis (incubate, fast-forward, history-reversal, lifecycle) |

## The Selection Algorithm

### Step 1 — Filter by domain
From the 28 frameworks, keep those where `domain-fit` includes the Phase-1 domain tag. If domain is `other`, use the full set.

### Step 2 — Group by constraint-type
Bucket the filtered set into the 5 constraint-type groups.

### Step 3 — Compute the seed
Take the concatenation `<Problem Statement> + <Selected reframe>` (use the FIRST selected reframe if multiple).

Use this practical hash that Claude can compute in conversation:
```
seed = (word_count(input) * 17) + sum(ord(first_letter_of_each_word(input)))
```

Worked example:
- input = "AI products that help small business owners"
- words = 7 → 7 × 17 = 119
- first letters: A,p,t,h,s,b,o → ord = 65+112+116+104+115+98+111 = 721
- seed = 119 + 721 = 840

Record `seed` and `seed mod 5` in the conversation as `**Seed:** <n> (mod 5 = <m>)` so the user can verify determinism.

### Step 4 — Favorites-bias gate
Frameworks with `favorites-bias: true`: SCAMPER, Six Thinking Hats, JTBD.

- If `seed mod 5 == 0`: ALLOW these in the candidate pool.
- Otherwise: EXCLUDE them. (This breaks Claude's training-frequency bias toward these three.)

### Step 5 — Draw the selection

**Deep mode** (5 frameworks):
1. Identify the 5 constraint-type buckets that have ≥1 framework after filtering.
2. From the 5 (or fewer) available types, pick 4 distinct types: use `seed mod 5` to choose which type to drop. (If only 4 types are available, no drop needed.)
3. Within each picked type, select 1 framework by index `(seed // 7 + type_index) mod bucket_size`.
4. Wildcard: from any remaining (unpicked) framework across all types, select 1 by index `(seed // 11) mod remaining_size`.
5. Total: 5 frameworks.

**Quick mode** (2 frameworks):
1. Pick 2 distinct constraint-types, biased to maximize distance: prefer pairs like `(random-stimulus, structural)` or `(inversion, semantic)` — never two of the same type.
2. Use `seed mod (num_pairs)` to pick which pair.
3. Within each picked type, select 1 framework by index `(seed // 7 + type_index) mod bucket_size`.
4. Total: 2 frameworks.

### Step 6 — Variety check
Verify the result covers ≥3 distinct constraint-types (deep) or ≥2 (quick). If short, redraw the wildcard from a constraint-type not yet represented.

### Step 7 — Random-stimulus floor
At least 1 selected framework MUST have `constraint-type: random-stimulus` OR `secondary-constraint-type: random-stimulus`. If neither holds, replace the wildcard with a random-stimulus framework (use `seed mod random_stim_bucket_size` to pick).

### Step 8 — State the picks
Output to the conversation:
```
**Seed:** <n> (mod 5 = <m>; favorites = <allowed | excluded>)
**Selected frameworks:** <Framework A> [<type>], <Framework B> [<type>], ...
```

## Framework Catalog

| Name | constraint-type | secondary | domain-fit | favorites-bias |
|---|---|---|---|---|
| false-faces | inversion | semantic | business, product, engineering, research, creative | false |
| scamper | semantic | structural | business, product, engineering, creative | **true** |
| cherry-split | structural | semantic | business, product, engineering, research | false |
| brutethink | random-stimulus | semantic | business, product, engineering, research, creative | false |
| phoenix | structural | semantic | business, product, engineering, research | false |
| hall-of-fame | semantic | random-stimulus | business, product, creative | false |
| slice-and-dice | structural | temporal | business, product, engineering, research | false |
| tug-of-war | structural | inversion | business, product, engineering | false |
| think-bubbles | structural | semantic | business, product, research, creative | false |
| three-bs | temporal | random-stimulus | research, creative | false |
| phase-separation | structural | inversion | business, product, engineering, research | false |
| false-fail-test | inversion | temporal | business, product, engineering, research | false |
| three-deaths | temporal | structural | business, product, engineering | false |
| p-vs-s-loonshot | structural | semantic | business, product | false |
| bushes-vs-trees | structural | temporal | business, product, engineering, research | false |
| critical-mass | temporal | structural | business, product, research | false |
| six-thinking-hats | semantic | structural | business, product, engineering, research, creative | **true** |
| provocation-po | random-stimulus | inversion | business, product, engineering, creative | false |
| random-stimulation | random-stimulus | semantic | business, product, engineering, research, creative | false |
| triz-contradictions | structural | inversion | engineering, product, research | false |
| jtbd | semantic | structural | business, product | **true** |
| blue-ocean-errc | semantic | inversion | business, product | false |
| inversion | inversion | structural | business, product, engineering, research, creative | false |
| first-principles | structural | semantic | business, product, engineering, research | false |
| analogous-domain | semantic | structural | business, product, engineering, research, creative | false |
| crazy-8s | random-stimulus | semantic | product, creative | false |
| worst-possible-idea | inversion | random-stimulus | business, product, engineering, research, creative | false |
| morphological-analysis | structural | semantic | engineering, product, research | false |

## Worked example: deep mode, business domain

Problem: "AI products that help small business owners"
Selected reframe: "What if small business owners actively want to AVOID software, not adopt it?"

1. Filter by domain `business`: ~22 frameworks remain (all except three-bs which is creative-only).
2. Group by constraint-type:
   - semantic: scamper, hall-of-fame, six-thinking-hats, jtbd, blue-ocean-errc, analogous-domain (6)
   - structural: cherry-split, phoenix, slice-and-dice, tug-of-war, think-bubbles, phase-separation, p-vs-s-loonshot, bushes-vs-trees, first-principles, morphological-analysis (10)
   - random-stimulus: brutethink, provocation-po, random-stimulation, worst-possible-idea (worst-possible has secondary random-stimulus; primary inversion) → 3 primary random-stimulus
   - inversion: false-faces, false-fail-test, inversion, worst-possible-idea (4)
   - temporal: three-deaths, critical-mass (2)
3. Compute seed (using the recipe above) → e.g., seed = 1247, mod 5 = 2 → favorites EXCLUDED.
   - After exclusion: scamper, six-thinking-hats, jtbd removed.
4. Drop type with index `(seed mod 5) = 2` → drop the 3rd type (random-stimulus).
   - This violates step 7 (random-stimulus floor)! → re-run step 4 with the next-lowest type index that doesn't break the floor → drop temporal instead.
5. Pick from the 4 remaining types (semantic, structural, random-stimulus, inversion).
6. Wildcard: a temporal framework — say `critical-mass`.
7. Output: **Selected frameworks:** hall-of-fame [semantic], slice-and-dice [structural], brutethink [random-stimulus], false-faces [inversion], critical-mass [temporal]

(Concrete picks within each bucket depend on `seed // 7`. The key invariant: same problem + reframe → same picks.)

## Notes

- The hash recipe above is deliberately simple so Claude can compute it in-conversation. It's not cryptographically random; it just provides reproducible variability.
- If the user asks for variety on the SAME problem, change the reframe to change the seed.
- The `favorites-bias` flag is a stronger constraint than the seed — it specifically combats Claude's tendency to default to the 3 best-known frameworks.
