---
name: bushes-vs-trees
domain-fit: business, product, engineering, research
constraint-type: structural
secondary-constraint-type: temporal
favorites-bias: false
---

## When to use
Ideation has two modes: **bush** (broad shrub of many shallow branches — explore widely, don't commit) and **tree** (deep focused exploration of one branch — develop one thing fully). Most teams default to one mode and miss the value of explicit alternation. Bushes-vs-Trees forces both modes within a single ideation session.

## The technique
1. **Bush phase (5-10 min)**: generate 15-30 idea seeds, each one sentence, no elaboration. Width is the goal. Reject the urge to "develop" any one of them.
2. Pick 2-3 of the most surprising bush seeds. Surprise = the seed where you cannot predict what the developed version looks like.
3. **Tree phase (per seed)**: take each picked seed and develop it deeply: what does the full version look like? What's the mechanism? What's the unit economics? What are the failure modes? Aim for 100-200 words per tree.
4. **Re-bush after each tree**: a fully developed tree often reveals NEW seeds (subtrees, adjacent ideas, inversions). Add these to the bush pool.
5. Iterate. The session ends when bushes and trees stop generating new entries.

## Anti-mode-collapse prompts
- During bush phase, reject the impulse to develop any seed. Width before depth — that's the contract.
- The "most surprising" criterion for tree-picks is critical. The most LIKELY-TO-WORK seed is the mode-collapse pick. The most surprising one is the one whose tree you cannot predict.
- After each tree, you must re-bush. Trees grow new bushes — skipping this step is the failure mode.

## Example application (synthetic)
Problem: "Reduce churn for a B2B SaaS product."

Bush seeds (sample): churn-reasons-as-product-features; reverse-onboarding for at-risk users; pre-emptive partial refunds; customer success replaced by customer-managed tools; usage-based discount auto-applied; switch cost engineering; gradual deprecation as a feature; community ownership transition; etc.

Tree-picked: "switch cost engineering."

Tree (developed): build features that compound value as the customer's data accumulates IN the product (custom views, learned preferences, integrations stitched). At month 12, the cost of leaving = recreating those compounded artifacts. Mechanism: every action in-product creates persistent state that's user-owned but product-bound. Failure mode: customer perceives lock-in, brand suffers.

Re-bush from this tree: "lock-in transparency" (show the user explicitly what they'd lose); "exportable lock-in" (let them export the compounded artifacts); "lock-in as a SHARED asset" (between vendor and customer).

## Output format
- Bush list (15-30 seeds, one line each)
- 2-3 trees (100-200 words each)
- Updated bush list with re-bushed seeds
