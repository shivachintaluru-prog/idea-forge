# Phase 2: Reframe (mandatory gate)

**Goal**: produce ≥3 reframed problem statements (≥1 in `--quick`) so Phase 3 explores divergent territory rather than the obvious one. Reframing alone produces ~50% of the breakthrough delta in real ideation.

## Exit artifact (required before Phase 3)

Emit verbatim:

```
## Reframes
1. <reframe 1>
2. <reframe 2>
3. <reframe 3>
[≥3 in deep, ≥1 in quick]

**Selected reframe(s):** <pick the 1-2 most divergent ones to carry into Phase 3>
```

## Process

Apply 3 reframing techniques (deep) — or only False Faces in `--quick`.

### 1. False Faces (assumption reversal)
- List the 3-5 implicit ASSUMPTIONS in the original problem statement (e.g., "users want speed," "this needs an app," "the bottleneck is X").
- For each assumption, write its REVERSE.
- Pick the most provocative reversal and rewrite the problem statement as if that reversal were true.
- Result: 1 reframe.

### 2. True/False (premise audit)
- For each phrase in the problem statement, mark TRUE (verified, has evidence) vs ASSUMED (taken for granted).
- Replace 1-2 ASSUMED premises with their alternatives.
- Result: 1-2 reframes.

### 3. Slice and Dice (decomposition + recomposition)
- Decompose on a different axis than the user implied:
  - role: whose problem is it really?
  - time: what changes if we 10× the timescale (or compress to 1% of it)?
  - scale: 1 user vs 1M? 1 day vs 10 years?
- Recompose at the new granularity to form a reframed problem statement.
- Result: 1-2 reframes.

## Selection

After ≥3 reframes are generated, select the 1-2 MOST DIVERGENT — furthest from the original framing. These are the ones Phase 3 will operate on.

If you can't tell which reframe is most divergent, pick the one that makes you most uncomfortable / least sure how to solve. That's the signal.

## Anti-mode-collapse for Phase 2

- DO NOT generate "near reframes" (synonyms, rephrases). Each reframe must change the problem's assumption, axis, or scope.
- DO NOT pick a reframe that is closest to the original. Pick the most provocative.
- The user may push back ("the original is fine, just generate ideas"). The Iron Law: emit the artifact regardless. Reframing is where breakthroughs are born; skipping it makes the rest of the skill no better than vanilla LLM output.
- DO NOT skip Slice and Dice in deep mode just because it feels redundant. Time/scale axes routinely produce the most divergent reframes.
