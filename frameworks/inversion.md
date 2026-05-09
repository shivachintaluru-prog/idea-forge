---
name: inversion
domain-fit: business, product, engineering, research, creative
constraint-type: inversion
secondary-constraint-type: structural
favorites-bias: false
---

## When to use
Instead of asking "how do we achieve X," ask "how do we GUARANTEE the OPPOSITE of X?" — then enumerate everything that would cause failure, and avoid those. This often produces more concrete, actionable insights than direct goal-pursuit, because failure modes are easier to enumerate than success conditions.

## The technique
1. State the goal positively ("achieve high user retention").
2. Invert: "How would we GUARANTEE catastrophic user churn?"
3. Generate 10-15 failure mechanisms — concrete things you'd do if you wanted users to leave fastest. Be specific and aggressive ("send a 6 AM marketing email every day," "hide the unsubscribe button," "rotate the UI weekly," etc.).
4. For each failure mechanism, derive its INVERSE — the action that prevents that specific failure.
5. The inverses are your idea pool. Many will be ideas that ordinary "how do we improve retention" ideation would never reach because they're framed as ABSENCES (don't do X) rather than presences (do Y).

## Anti-mode-collapse prompts
- Step 3 must produce SPECIFIC, AGGRESSIVE failure mechanisms — not vague "bad UX." Specificity is the engine.
- Don't censor in step 3. The inversion technique requires committing to the destructive scenario fully. Self-censorship reduces idea generation by ~80%.
- The inverse derived in step 4 should sometimes be a NEGATIVE action (something you DON'T do or actively prevent). Many "do" lists miss the value of "don't do."

## Example application (synthetic)
Goal: "Engineering team produces high-quality code."

Inversion: "Engineering team produces maximally low-quality code."

Failure mechanisms: no code review; reviews are perfunctory rubber-stamps; tests are written after deployment; rotating engineers across services so no one owns anything; reward velocity over correctness in performance reviews; merge directly to main; senior engineers above-the-fray and don't review junior work; production access for everyone; flaky tests tolerated indefinitely; tooling that doesn't catch issues at PR time; postmortems blame individuals.

Inverses (idea pool):
- Reviews require an explicit "what could go wrong" comment per PR (not just LGTM)
- Tests as a PR gate, with coverage measured pre-merge
- Service ownership tied to on-call rotation, decoupled from team boundaries
- Performance reviews measure incidents-attributable, not velocity
- Production access tiered, expanded by demonstrated reliability
- Flaky test triage SLA — flaky tests blocked at the org level after 48h
- Postmortems use blameless rootcause analysis with a documented protocol

The "performance reviews measure incidents-attributable" inverse is non-obvious and would not surface from "improve code quality" framed positively.

## Output format
- Goal + inversion
- 10-15 failure mechanisms
- 7-12 inverse ideas (note which are NEGATIVE actions)
