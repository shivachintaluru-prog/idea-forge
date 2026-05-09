---
name: tug-of-war
domain-fit: business, product, engineering
constraint-type: structural
secondary-constraint-type: inversion
favorites-bias: false
---

## When to use
Two opposing forces shape the problem. Most thinking compromises between them. Tug of War generates ideas that AMPLIFY both forces simultaneously, or that TRANSCEND the trade-off altogether.

## The technique
1. Identify the central tension as Force A vs Force B (e.g., fast vs thorough, cheap vs premium, simple vs powerful, local vs global).
2. Reject the "balanced compromise" answer immediately — it's the mode-collapse default.
3. Generate three families of ideas:
   - **Amplify both**: ideas that make BOTH forces stronger at once (often via separation in time, space, or audience)
   - **Transcend the axis**: ideas that change the substrate so the tension dissolves
   - **Pick a side, hard**: ideas that pick ONE force absolutely, ignoring the other; surprisingly often, the consequences of the absolute pick reveal new value

## Anti-mode-collapse prompts
- "Compromise" answers are forbidden. If your idea contains "and reasonably," reject it.
- For "amplify both," look for separation devices — different times, different users, different stages, different SKUs.
- For "transcend," ask: "What if the axis we're balancing is actually a false dichotomy?"
- The "pick a side, hard" frame routinely produces ideas that surprise the picker. Don't skip it just because it sounds extreme.

## Example application (synthetic)
Tension: **fast** vs **thorough** in incident response.

- Compromise (rejected): "Reasonably fast and reasonably thorough."
- Amplify both via separation: "Day 1: ruthlessly fast triage with explicit known-unknowns list. Day 30: thoroughness ritual where every fast Day-1 patch is re-examined."
- Transcend: "Move thoroughness to the FIX, not the response. Response is fast by definition; thoroughness lives in post-mortem culture."
- Pick fast hard: "Auto-rollback at first error signal, no investigation. Consequence: more rollbacks, but each carries 0% risk and forces faster feedback loops."
- Pick thorough hard: "No incident is closed in <72 hours. Consequence: artificial slowness reveals which incidents *needed* fast response."

The "pick thorough hard" idea is genuinely novel and would not surface from compromise thinking.

## Output format
- The Force A vs Force B framing
- 5+ ideas across the three families (amplify / transcend / pick-hard)
