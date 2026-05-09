---
name: cherry-split
domain-fit: business, product, engineering, research
constraint-type: structural
secondary-constraint-type: semantic
favorites-bias: false
---

## When to use
A concept feels monolithic. Split it into independent attributes and recombine the parts in unexpected ways to surface novel configurations.

## The technique
1. Identify the seed concept.
2. List 3-5 distinct ATTRIBUTES of it (function, form, audience, timing, medium, pricing, ownership, etc.).
3. For each attribute, list 3 alternative values that make sense for it (or that don't — both work).
4. Recombine: pick one value from each attribute column. Walk through several combinations.
5. Flag the combinations that produce a NEW kind of thing rather than a variant of the original.

## Anti-mode-collapse prompts
- Pick attributes whose default values you've never questioned. ("Pricing" defaults to "user pays" — but ad-funded, employer-funded, gift-funded, scarcity-rationed are all real.)
- Reject combinations that just produce a slightly-different version of the seed. The interesting cells are the ones that change the *category*.
- If 2 attributes always co-vary in your examples, you've smuggled an assumption — split them again until they truly vary independently.

## Example application (synthetic)
Seed: "Restaurant"
- Attributes: food (cooked-by | sourced-from), service (presence | absence), space (private | public | virtual), payment (per-meal | subscription | barter)
- Recombinations:
  - Cooked-by-self + service-absent + private-space + barter → home cooking club, members trade meals
  - Sourced-from-supplier + service-presence + virtual-space + subscription → "restaurant" delivers a meal kit + 1:1 video coaching
  - Cooked-by-pro + service-absent + public-space + per-meal → vending machine with chef-quality output

The third option exists. The first two are unfamiliar configurations — exactly the territory Cherry Split is for.

## Output format
- Attribute table (rows = attributes, columns = values)
- 5-8 recombined configurations, with 1-line description of each
