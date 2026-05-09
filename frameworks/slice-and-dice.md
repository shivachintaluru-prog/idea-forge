---
name: slice-and-dice
domain-fit: business, product, engineering, research
constraint-type: structural
secondary-constraint-type: temporal
favorites-bias: false
---

## When to use
Decompose the problem along a non-obvious axis and recompose at a different granularity. The act of choosing a different decomposition reveals the assumed one — and assumed decompositions are mode-collapse machines.

## The technique
1. List 5-7 candidate decomposition axes:
   - Parts (components / modules)
   - Layers (data / logic / interface, or stack levels)
   - Lifecycle (pre / during / post; or onboarding → routine → expansion → churn)
   - Time (minute / day / month / year / decade)
   - Role (user / admin / vendor / regulator / non-user)
   - Scale (1 user / 1K / 1M / 1B)
   - Geography (local / regional / global / virtual)
2. Pick the axis you would LEAST naturally use for this problem.
3. Decompose the problem along that axis.
4. Recompose at a NEW granularity — combine 2-3 cells, split one cell into smaller pieces, or skip a cell entirely.
5. The recomposed version is your reframe + idea source.

## Anti-mode-collapse prompts
- The "least natural axis" rule is critical. If your problem is a SaaS tool, the natural axis is "feature parts" — explicitly skip that and pick lifecycle, role, or geography instead.
- Recomposition must produce something STRUCTURALLY different, not just a renamed version. If your "new granularity" makes the same components appear in the same order, redo.

## Example application (synthetic)
Problem: "Improve customer support."

Default axis (skip): channels (email / chat / phone).

Picked axis: **lifecycle** (pre-purchase, install, daily-use, expansion, churn).

Decomposition:
- Pre-purchase: support questions become marketing collateral
- Install: support becomes a setup wizard
- Daily-use: support becomes contextual nudges in-product
- Expansion: support becomes a "what's next" advisor
- Churn: support becomes an exit interview that informs roadmap

Recomposition: combine pre-purchase + churn cells. The exiting customer's last conversation becomes the prospective customer's first. Same artifact, both ends of the lifecycle.

## Output format
- Picked axis + cells
- 5-8 ideas, one per cell or per recomposed combination
