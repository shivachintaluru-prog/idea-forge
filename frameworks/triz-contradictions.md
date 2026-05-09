---
name: triz-contradictions
domain-fit: engineering, product, research
constraint-type: structural
secondary-constraint-type: inversion
favorites-bias: false
---

## When to use
Engineering / system design problems where improving one parameter degrades another (e.g., improving speed degrades safety; improving accuracy degrades latency). TRIZ encodes the observation that contradictions are usually NOT genuine — there are repeated patterns by which they can be resolved by SEPARATION rather than COMPROMISE.

## The technique
1. State the contradiction as: "We want to improve X, but doing so worsens Y."
2. Apply the four separation principles. For each, generate 1-2 ideas that resolve the contradiction by separating in that dimension:

   - **Separation in TIME**: have X during one period, Y during another. (e.g., aggressive caching at startup, conservative writes during operation.)
   - **Separation in SPACE**: have X in one location, Y in another. (e.g., hot data on fast storage, cold data on slow storage.)
   - **Separation between PARTS and WHOLE**: have X at the system level, Y at the component level (or vice versa). (e.g., system is robust because individual components are fragile and replaced often.)
   - **Separation by CONDITION**: have X under one condition, Y under another. (e.g., synchronous when load is low, asynchronous when load is high.)

3. For each separation idea, ask: "What's the trigger that switches between modes? What's the cost of the switch?"

## Anti-mode-collapse prompts
- Reject the compromise answer ("a balance of X and Y"). TRIZ explicitly rejects compromise as the inferior answer.
- For each separation principle, the separation must be CONCRETE — name the time, space, part, or condition. Vague "depending on context" is mode collapse.
- If a contradiction "resists" separation, it might be a genuine physical contradiction; in that case, look for second-order separations (separate the SYSTEM from the USER, separate the PERCEPTION from the REALITY).

## Example application (synthetic)
Contradiction: "We want fast page-load (good UX) but rich data fetching (good content)."

- Time separation: render skeleton + critical content first (at fold), stream rich data in after (below fold + interaction-triggered).
- Space separation: critical data on edge CDN, rich data fetched directly from origin only when scrolled.
- Part/whole: pages individually heavy, but session-level state warm-cached so 2nd+ page is instant.
- Condition separation: rich data only on wifi; cellular gets the lean version with explicit "load full version" trigger.

Each is a distinct mechanism. Compromise answer ("only somewhat rich data") is strictly inferior.

## Output format
- The X-vs-Y contradiction statement
- 4-8 ideas across the separation principles
- Each idea names the specific separation mechanism
