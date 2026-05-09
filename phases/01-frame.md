# Phase 1: Frame

**Goal**: extract a tight problem statement and a domain tag so Phase 3's algorithm can select frameworks deterministically.

## Exit artifact (required before Phase 2)

Emit verbatim:

```
## Problem Statement
<2-3 sentence problem statement, specific enough to anchor framework selection>

## Domain
<one of: business | product | engineering | research | creative | other>
```

## Process

1. **Ask 4-5 clarifying questions** to extract:
   - WHAT problem — the gap, friction, or goal
   - WHY it matters — consequences of inaction, value of solving
   - WHAT constraints — resources, time, dependencies
   - WHO benefits — user, customer, stakeholder
   - WHAT does success look like — criteria, metrics

   If the user's prompt already provides enough information, skip redundant questions but verify your understanding back to them.

2. **Detect the domain** using `references/domain-detection.md`. If none of the 5 domains fit cleanly, tag as `other` — the selection algorithm uses a broader framework set for the fallback.

3. **Emit the exit artifact** verbatim. Do NOT proceed to Phase 2 until both `## Problem Statement` and `## Domain` are visible in the conversation.

## Minimum viable framing

If the user's prompt is genuinely under-specified (e.g., "ideas for a tagline"), Phase 1 must elicit at least:
- 1 sentence describing the problem context
- 1 explicit constraint
- 1 success criterion

If the user refuses to provide more context, frame what was given and proceed; flag the under-specification in the final Phase 5 output.

## Anti-mode-collapse for Phase 1

- DO NOT accept a vague problem statement ("I want creative ideas"). Push for specificity: who, what, why, when.
- DO NOT skip the Domain tag — it's mandatory for the selection algorithm. Even `other` must be tagged explicitly.
- DO NOT solve the problem in Phase 1. The instinct to "just answer" is mode collapse. Frame, don't solve.
- DO NOT compress the problem statement to 1 sentence if 2-3 are needed for specificity.
