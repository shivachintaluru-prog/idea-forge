---
name: first-principles
domain-fit: business, product, engineering, research
constraint-type: structural
secondary-constraint-type: semantic
favorites-bias: false
---

## When to use
Reasoning by analogy ("X is like Y, so we should do Z") inherits Y's assumptions and constraints. First Principles decomposes the problem to its fundamental physical / economic / informational elements and rebuilds the solution from scratch — often surfacing options that analogy-based reasoning excludes.

## The technique
1. State the problem as currently framed.
2. List the IMPLICIT analogies in the framing. ("This is a SaaS product" implies analogy to SaaS economics; "this is an enterprise tool" implies analogy to enterprise sales.) Each analogy carries baked-in constraints.
3. Decompose the problem to fundamentals. Different problem classes have different fundamental layers:
   - For products: cost-of-goods, value-delivered, distribution-cost, willingness-to-pay
   - For systems: information-flow, latency, error rates, energy/compute cost
   - For organizations: incentives, decision rights, information asymmetry, time horizons
4. At each fundamental layer, ask: "What's the irreducible TRUTH here, independent of how the problem is currently solved?"
5. Rebuild the solution from those truths upward. Don't borrow ANY structure from existing solutions.
6. The reconstruction often produces ideas that don't fit existing categories.

## Anti-mode-collapse prompts
- Step 2 (listing implicit analogies) is the hardest and most-skipped. Force it. Every framing has analogies; finding them is what makes First Principles real.
- At step 4, "irreducible truth" must be specific and physical/economic/informational, not aspirational. "Users want value" is not a first principle; "delivering one unit of compute costs $0.0X with energy + amortized hardware" is.
- Reject reconstructions that secretly look like the original. If your "first-principles" solution has the same shape as a SaaS product or an enterprise tool, you smuggled the analogy back in.

## Example application (synthetic)
Problem: "Improve commute experience for urban workers."

Implicit analogies: "It's a transportation problem" (analogy: optimize the journey); "It's a service problem" (analogy: improve the provider).

Fundamentals: each commuter has 30-90 min of time spent on motion they don't choose. Time has alternative uses (work, rest, social, health). Most current solutions optimize the JOURNEY (faster, smoother), assuming the journey itself is the unit.

First-principles reconstruction: the unit of value is "30-90 min of time-with-someone-else's-control." Solutions that ELIMINATE the commute (remote work) are obvious. But the non-obvious frontier: solutions that REDIRECT the time. What if commuting time were systematically used for high-value asynchronous activities (deep listening to a structured curriculum; therapeutic sleep; rehearsed conversation)?

Idea pool: commute as therapy session (booked 1:1 audio); commute as structured language acquisition (the 90-min daily ritual produces fluency in 18 months); commute as "second sleep" (designed to add an hour of deep rest, with darkening goggles + scheduled stops).

## Output format
- Original framing + implicit analogies
- Fundamental layers + irreducible truths
- 4-8 reconstructed ideas
