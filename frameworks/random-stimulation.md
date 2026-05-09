---
name: random-stimulation
domain-fit: business, product, engineering, research, creative
constraint-type: random-stimulus
secondary-constraint-type: semantic
favorites-bias: false
---

## When to use
Inject genuinely random external stimulus — a word, an image, an unrelated domain — and force a connection to the problem. Differs from `brutethink` in that the stimulus is broader (object, image, domain, era) and the connection technique is multi-step.

## The technique
1. Pick a random stimulus from a pre-built set, NOT something you choose:
   - Random object (open a catalog, point at an item)
   - Random image (a Wikipedia random article's lead image)
   - Random era + place (e.g., 1820s Edinburgh, 1690s Edo, 2050 Lagos)
   - Random profession (forester, lighthouse keeper, gravedigger, paleographer, train conductor)
2. Spend 2-3 minutes characterizing the stimulus: list 8-12 distinctive properties / mechanisms / constraints / norms associated with it.
3. For each property, ask: "How does this property apply to MY problem?" Force a connection even when none seems present.
4. Capture the ideas that emerge from the forced connections. Discard ones where the connection is purely metaphorical with no substance.

## Anti-mode-collapse prompts
- The stimulus must be selected BEFORE you re-read the problem. No "appropriate" stimulus selection.
- The properties list must include SPECIFIC, NON-OBVIOUS items. "Lighthouse keepers are isolated" is obvious — "lighthouse keepers historically rotated in 4-week shifts and counted ships passing as a daily ritual" is specific.
- A connection is only valid if it produces a mechanism, not just a metaphor. "Onboarding is like a lighthouse" is empty; "onboarding rotates duty among existing users in 4-week shifts" is a mechanism.

## Example application (synthetic)
Problem: "Improve documentation quality for an open-source library."

Random stimulus: **a 1920s railway switchman**.

Properties: works alone in remote box; physical levers with tactile feedback; routes thousands of trains per day; can't see the whole network but knows their junction perfectly; logs every switch decision in a paper book; trained for years; replaced by interlocking systems.

Forced connections:
- "Tactile feedback" → docs include working code that actively confirms it works (live executable examples)
- "Logs every switch decision" → docs include an "ADR-style" log of why each API decision was made, not just what it does
- "Knows their junction perfectly" → docs are written from the perspective of a SPECIFIC USE CASE the writer mastered, not a comprehensive manual
- "Replaced by interlocking systems" → docs anticipate their own deprecation by linking to the auto-generated successor

The third and fourth ideas are non-obvious and non-trivial.

## Output format
- The random stimulus + property list
- 5-10 ideas, each tagged with the property and the mechanism (not just metaphor)
