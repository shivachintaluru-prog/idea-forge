---
name: scamper
domain-fit: business, product, engineering, creative
constraint-type: semantic
secondary-constraint-type: structural
favorites-bias: true
---

## When to use
Apply 7 specific transformations to an existing concept to systematically generate variants. Best when there's a well-defined seed concept to mutate.

## The technique
For each letter, generate 2 candidate transformations of the seed concept; keep the more surprising one:

- **S — Substitute**: replace one component with something different (material, role, process)
- **C — Combine**: merge with another concept (often unrelated) to form a hybrid
- **A — Adapt**: borrow a mechanism from a different domain
- **M — Modify / Magnify / Minify**: change scale, frequency, intensity
- **P — Put to another use**: same artifact, different user/context
- **E — Eliminate**: remove a component and see what remains useful
- **R — Reverse / Rearrange**: invert the order or roles

Generate 7 ideas (one per letter). Beat-the-obvious bar: if your S-substitution is the first one that came to mind, generate two more before committing.

## Anti-mode-collapse prompts
- For each letter, list 3 candidates and pick the most surprising — not the first.
- Reject candidates that just rephrase the original ("substitute the word X with synonym Y").
- The Reverse step is where most transformations cluster on triviality. Force a structural reverse, not a label swap.

## Example application (synthetic)
Seed: "AI scheduling assistant for small teams."
- **S**: Replace AI with a recurring 5-min human concierge. (Substitute the autonomy axis.)
- **C**: Combine with calendar billing — schedule + invoice in one act.
- **A**: Adapt the protocol used in air-traffic-control handoffs.
- **M**: Compress to a single SMS exchange per scheduling event.
- **P**: Use it as a mood-tracker (when meetings get rescheduled, flag patterns).
- **E**: Remove the calendar entirely; it's a meeting-purpose negotiator only.
- **R**: Schedule the past — retroactive meetings (record-and-fill).

## Output format
7 ideas, one per letter. Each ≥1 sentence.
