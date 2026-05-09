---
name: critical-mass
domain-fit: business, product, research
constraint-type: temporal
secondary-constraint-type: structural
favorites-bias: false
---

## When to use
At a certain group size or organizational maturity, anti-novelty dynamics dominate — every loonshot gets killed by averaged consensus, risk allocation, or career-protection incentives. Critical Mass forces ideation that accounts for the threshold dynamics: ideas that survive past the inflection, OR ideas that thrive specifically below it.

## The technique
1. Identify the critical-mass thresholds the idea must navigate:
   - **Group size** (~25 people typically; below = small-team novelty rewarded; above = consensus-protection dominates)
   - **Funding maturity** (pre-product-market-fit = experimentation tolerated; post-PMF = "don't break what works")
   - **Organizational age** (early = low antibodies; mature = high antibodies)
   - **Customer base size** (early customers = surprise-tolerant; mass market = stability-demanding)
2. Generate 3 idea categories:
   - **Sub-threshold ideas**: would only survive in a sub-25-person, pre-PMF, early-customer environment. Tag as "stays small or dies."
   - **Trans-threshold ideas**: explicitly designed to survive the inflection. They have built-in mechanisms for the post-threshold environment (e.g., compatibility layers, opt-in cohorts, separated decision rights).
   - **Above-threshold-only ideas**: actually require scale to work (network effects, statistical learning, fixed-cost amortization).
3. Tag every idea with its threshold-class so downstream evaluation knows what environment it needs.

## Anti-mode-collapse prompts
- Reject the implicit assumption that all ideas should survive at all scales. Sub-threshold ideas have legitimate value — they just need a different containment strategy.
- For trans-threshold ideas, name the SPECIFIC mechanism that lets them survive the inflection. Vague "we'll iterate" is mode collapse.
- Above-threshold-only ideas are systematically under-generated because most ideation happens in small teams. Force at least 2.

## Example application (synthetic)
Problem: "Improve internal engineering productivity."

- Sub-threshold ideas: ad-hoc pair programming; rotating "fixer" role; weekly 30-min reflection with no agenda. (These die at scale.)
- Trans-threshold ideas: pair programming PROTOCOL with explicit hand-off rituals (survives because it's codified); fixer role formalized as a quarterly rotation with defined scope (survives because the scope absorbs scale). Mechanism: codification of small-team rituals before they become invisible.
- Above-threshold-only ideas: large-corpus dependency-graph analysis to surface refactoring targets; statistical debugging via aggregated error fingerprints; A/B testing of internal tools across squads.

## Output format
- 3-5 ideas per threshold class (sub / trans / above)
- Each idea tagged with the specific mechanism that ties it to its threshold
