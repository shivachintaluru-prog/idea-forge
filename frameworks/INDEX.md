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

### Step 3 — Compute the seed (canonical recipe)

**This file (`frameworks/INDEX.md`) is the authoritative home for the hash recipe.** SKILL.md and `phases/03-diverge.md` MUST reference this section rather than restate it. If they diverge, this file wins.

Procedure:

1. Concatenate `<Problem Statement> + " " + <FIRST Selected reframe>`. (If multiple reframes were selected in Phase 2, use the first.)
2. **Truncation rule**: take only the FIRST 30 WORDS of that string (split on whitespace). This bounds variability from long inputs and keeps the seed stable when only the tail of a problem statement is edited.
3. Compute:
   ```
   words            = truncated_input split on whitespace
   word_count       = len(words)
   first_letter_sum = sum(ord(word[0]) for word in words)
   seed             = (word_count × 17) + first_letter_sum
   ```
4. Derived values:
   ```
   seed mod 5       -- type-drop modulus (see Step 5)
   favorites_value  = (seed // 13) mod 7    -- INDEPENDENT channel; favorites allowed iff favorites_value == 0 (see Step 4)
   ```

Record both derived values in the conversation as `**Seed:** <n> (mod 5 = <m>; favorites_value = <f>; favorites = <allowed | excluded>)` so the user can verify determinism.

Worked computation (matches the worked example below):
- input = "AI products that help small business owners What if small business owners actively want to AVOID software, not adopt it?"
- words after split = 20 (under the 30-word cap; truncation is a no-op here)
- word_count = 20 → 20 × 17 = 340
- first letters: A, p, t, h, s, b, o, W, i, s, b, o, a, w, t, A, s, n, a, i
- first_letter_sum (sum of `ord` of each first letter) = 65+112+116+104+115+98+111+87+105+115+98+111+97+119+116+65+115+110+97+105 = 2061
- **seed = 340 + 2061 = 2401**
- seed mod 5 = **1**
- favorites_value = (2401 // 13) mod 7 = 184 mod 7 = **2** → NOT 0 → **favorites EXCLUDED**

### Step 4 — Favorites-bias gate (independent channel)
Frameworks with `favorites-bias: true` (after the catalog updates below): SCAMPER, Six Thinking Hats, JTBD, first-principles, inversion, blue-ocean-errc.

- If `favorites_value == 0` (where `favorites_value = (seed // 13) mod 7`): ALLOW these in the candidate pool.
- Otherwise: EXCLUDE them. (This breaks Claude's training-frequency bias toward these six.)

This channel is INDEPENDENT of the `seed mod 5` type-drop modulus used in Step 5. The independence prevents correlation between "favorites allowed" and "semantic bucket dropped" on the most common (business) domain, which was a defect in the prior version. Approximate favorites-allowed rate: ~14% (1 in 7).

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

### Step 5b — Collision resolution

The selection steps can collide. Resolve deterministically with this precedence (HIGH to LOW):

1. **Step 7 random-stimulus floor** — at least 1 selected framework must have `constraint-type: random-stimulus` OR `secondary-constraint-type: random-stimulus`. This is non-negotiable.
2. **Step 5.2 type drop** — `seed mod 5` selects which constraint-type to drop.
3. **Step 4 favorites gate** — excludes favorites-flagged frameworks unless `favorites_value == 0`.

Concrete rule: when `seed mod 5` points at the `random-stimulus` bucket (i.e., the drop would violate the floor), rotate the drop forward to the next bucket:

```
drop_index = seed mod 5
if drop_index == random_stimulus_type_index:
    drop_index = (drop_index + 1) mod num_populated_types
```

Continue rotating until a non-random-stimulus type is the drop, OR until all populated types have been tried — in that last case, keep all populated types (no drop) and proceed.

**Small-bucket branch (fewer than 5 populated types).** For domains where Step 1 filtering leaves fewer than 5 populated constraint-type buckets (e.g., the `creative` domain after re-tagging has 4 — semantic, structural, random-stimulus, inversion, temporal all populated but with the smallest having 1-2 entries):

- If 5 populated types remain: apply Step 5.2 with the rotation rule above.
- If exactly 4 populated types remain: skip the drop entirely; use all 4 populated types as primary draws and select 1 wildcard from any framework not yet picked. Deep mode targets 5 total; quick mode targets 2 total.
- If fewer than 4 populated types remain: use all populated types as primary draws (1 each); fill the remaining slot(s) with wildcards drawn from the largest bucket via `(seed // 11 + wildcard_index) mod remaining_size`. Deep mode still targets 5 total; quick mode targets 2 total.

### Step 6 — Variety check
Verify the result covers ≥3 distinct constraint-types (deep) or ≥2 (quick). If short, redraw the wildcard from a constraint-type not yet represented.

### Step 7 — Random-stimulus floor
At least 1 selected framework MUST have `constraint-type: random-stimulus` OR `secondary-constraint-type: random-stimulus`. If neither holds, replace the wildcard with a random-stimulus framework (use `seed mod random_stim_bucket_size` to pick).

### Step 8 — State the picks
Output to the conversation:
```
**Seed:** <n> (mod 5 = <m>; favorites_value = <f>; favorites = <allowed | excluded>)
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
| slice-and-dice | structural | temporal | business, product, engineering, research, creative | false |
| tug-of-war | structural | inversion | business, product, engineering | false |
| think-bubbles | structural | semantic | business, product, research, creative | false |
| three-bs | temporal | random-stimulus | research, creative | false |
| phase-separation | structural | inversion | business, product, engineering, research, creative | false |
| false-fail-test | inversion | temporal | business, product, engineering, research | false |
| three-deaths | temporal | structural | business, product, engineering, creative | false |
| p-vs-s-loonshot | structural | semantic | business, product | false |
| bushes-vs-trees | structural | temporal | business, product, engineering, research | false |
| critical-mass | temporal | structural | business, product, research, creative | false |
| six-thinking-hats | semantic | structural | business, product, engineering, research, creative | **true** |
| provocation-po | random-stimulus | inversion | business, product, engineering, creative | false |
| random-stimulation | random-stimulus | semantic | business, product, engineering, research, creative | false |
| triz-contradictions | structural | inversion | engineering, product, research | false |
| jtbd | semantic | structural | business, product | **true** |
| blue-ocean-errc | semantic | inversion | business, product | **true** |
| inversion | inversion | structural | business, product, engineering, research, creative | **true** |
| first-principles | semantic | structural | business, product, engineering, research | **true** |
| analogous-domain | semantic | structural | business, product, engineering, research, creative | false |
| crazy-8s | random-stimulus | semantic | product, creative | false |
| worst-possible-idea | inversion | random-stimulus | business, product, engineering, research, creative | false |
| morphological-analysis | structural | semantic | engineering, product, research | false |

## Worked example: deep mode, business domain

Problem: "AI products that help small business owners"
Selected reframe: "What if small business owners actively want to AVOID software, not adopt it?"

1. **Step 1 — Filter by domain `business`**: 24 frameworks have `business` in their `domain-fit`. Removed: three-bs (creative/research only), crazy-8s (product/creative only), triz-contradictions (engineering/product/research only), morphological-analysis (engineering/product/research only). That leaves 24.

2. **Step 2 — Group by constraint-type** (after the catalog updates above — note first-principles is now `semantic`):
   - semantic: scamper, hall-of-fame, six-thinking-hats, jtbd, blue-ocean-errc, analogous-domain, first-principles (7)
   - structural: cherry-split, phoenix, slice-and-dice, tug-of-war, think-bubbles, phase-separation, p-vs-s-loonshot, bushes-vs-trees (8)
   - random-stimulus: brutethink, provocation-po, random-stimulation (3) [worst-possible-idea is primary inversion]
   - inversion: false-faces, false-fail-test, inversion, worst-possible-idea (4)
   - temporal: three-deaths, critical-mass (2)

3. **Step 3 — Compute the seed** (per the canonical recipe above):
   - input (problem + first reframe, capped at 30 words): "AI products that help small business owners What if small business owners actively want to AVOID software, not adopt it?" — 20 words, under cap.
   - word_count = 20 → 20 × 17 = 340
   - first_letter_sum = 65+112+116+104+115+98+111+87+105+115+98+111+97+119+116+65+115+110+97+105 = 2061
   - **seed = 2401**
   - **seed mod 5 = 1**
   - **favorites_value = (2401 // 13) mod 7 = 184 mod 7 = 2** → NOT 0 → favorites EXCLUDED

4. **Step 4 — Favorites-bias gate** (independent channel). Since `favorites_value = 2 ≠ 0`, favorites EXCLUDED. After exclusion, remove: scamper, six-thinking-hats, jtbd, blue-ocean-errc, first-principles, inversion. Remaining pool:
   - semantic: hall-of-fame, analogous-domain (2)
   - structural: cherry-split, phoenix, slice-and-dice, tug-of-war, think-bubbles, phase-separation, p-vs-s-loonshot, bushes-vs-trees (8)
   - random-stimulus: brutethink, provocation-po, random-stimulation (3)
   - inversion: false-faces, false-fail-test, worst-possible-idea (3)
   - temporal: three-deaths, critical-mass (2)

5. **Step 5 — Draw the selection** (deep mode). All 5 buckets are populated.
   - Type drop: `drop_index = seed mod 5 = 1`. Type order is [0=semantic, 1=structural, 2=random-stimulus, 3=inversion, 4=temporal] → drop **structural**. Not the random-stimulus bucket, so Step 5b rotation is NOT triggered.
   - Primary picks via `(seed // 7 + type_index) mod bucket_size`, with `seed // 7 = 343`:
     - semantic (type_index 0, size 2): (343 + 0) mod 2 = 1 → **analogous-domain**
     - random-stimulus (type_index 1, size 3): (343 + 1) mod 3 = 2 → **random-stimulation**
     - inversion (type_index 2, size 3): (343 + 2) mod 3 = 0 → **false-faces**
     - temporal (type_index 3, size 2): (343 + 3) mod 2 = 0 → **three-deaths**
   - Wildcard from any unpicked framework (alphabetized across remaining = 14 entries): index `(seed // 11) mod 14 = 218 mod 14 = 8`. Ordering: brutethink, bushes-vs-trees, cherry-split, critical-mass, false-fail-test, hall-of-fame, phase-separation, phoenix, **p-vs-s-loonshot**, provocation-po, slice-and-dice, think-bubbles, tug-of-war, worst-possible-idea. Index 8 → **p-vs-s-loonshot** [structural].

6. **Step 6 — Variety check**: 4 distinct primary types + structural wildcard = 5 distinct types. Pass.

7. **Step 7 — Random-stimulus floor**: random-stimulation is in primaries. Pass.

8. **Step 8 — Output**:
   ```
   **Seed:** 2401 (mod 5 = 1; favorites_value = 2; favorites = excluded)
   **Selected frameworks:** analogous-domain [semantic], random-stimulation [random-stimulus], false-faces [inversion], three-deaths [temporal], p-vs-s-loonshot [structural — wildcard]
   ```

The two independent channels (`seed mod 5 = 1` for the type drop, `favorites_value = 2` for the favorites gate) are reported alongside each other so the reader can see they were computed from disjoint slices of the seed.

(The key invariant: same problem + reframe → same picks.)

## Notes

- The hash recipe above is deliberately simple so Claude can compute it in-conversation. It's not cryptographically random; it just provides reproducible variability.
- If the user asks for variety on the SAME problem, change the reframe to change the seed.
- The `favorites-bias` flag is a stronger constraint than the seed — it specifically combats Claude's tendency to default to the 3 best-known frameworks.
