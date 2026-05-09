---
name: six-thinking-hats
domain-fit: business, product, engineering, research, creative
constraint-type: semantic
secondary-constraint-type: structural
favorites-bias: true
---

## When to use
Apply six distinct thinking modes to the problem in sequence. Each "hat" is a different optimization function; rotating through them defeats single-mode collapse and surfaces ideas that one cognitive style would never reach.

## The technique
For each hat, generate 1-3 ideas IN that mode, suspending the others:

- **White hat — facts only**: what data exists about this problem? what would you measure? generate ideas grounded in observable evidence, with explicit data needs called out.
- **Red hat — feeling / intuition**: what does this problem feel like? what's the emotional core? generate ideas that name the gut reaction.
- **Black hat — risks / critique**: what's the failure mode? what's the strongest objection? generate ideas that pre-empt the critiques.
- **Yellow hat — value / optimism**: what would 10× upside look like? what's the best-case world? generate ideas that maximize asymmetric upside.
- **Green hat — creativity / divergence**: what's the most unexpected angle? generate ideas that nobody has considered.
- **Blue hat — process / meta**: what's the right way to think about this problem? generate ideas about the IDEATION process itself.

## Anti-mode-collapse prompts
- Each hat's ideas must be SPECIFIC TO THAT MODE. White hat ideas should look different from yellow hat ideas — different wordings, different shapes, different concerns.
- Reject "balanced" ideas inside any single hat. The whole point is single-mode purity per hat; balance comes from the rotation.
- Blue hat is the most under-used. Force at least 1 idea about how to think differently about this problem class.

## Example application (synthetic)
Problem: "Reduce wasted compute spend on a research GPU cluster."

- White: measure idle GPU-hours per user; correlate with project phase; identify the top-quintile waste pattern.
- Red: this feels like guilt — the system rewards individual peak compute, punishes restraint.
- Black: any quota system creates gaming; users will pre-emptively reserve and rebuild a black market.
- Yellow: the cluster could become 10× more productive if waste was redirected to capacity-on-demand for the most-blocked researchers.
- Green: charge negative prices for predicted idle slots — researchers earn budget by pre-committing to off-peak windows.
- Blue: reframe from "reduce waste" to "improve allocation efficiency." Different metric, different solution space.

## Output format
- 6 hats, 1-3 ideas each, total ~10-15 ideas
- Tag each idea with its hat
