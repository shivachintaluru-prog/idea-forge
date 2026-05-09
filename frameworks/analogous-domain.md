---
name: analogous-domain
domain-fit: business, product, engineering, research, creative
constraint-type: semantic
secondary-constraint-type: structural
favorites-bias: false
---

## When to use
Find a domain that has STRUCTURAL similarity to the problem but operates in a completely different surface area. Map the patterns from that domain onto the problem. The structural-but-not-superficial similarity is what makes the analogy productive — borrowed mechanisms transfer; borrowed labels don't.

## The technique
1. Strip the problem to its abstract structure: what are the FORCES, ACTORS, and CONSTRAINTS, independent of the surface domain?
   - Example: a customer-support problem might abstract to "high-volume incoming requests, variable urgency, asymmetric information, demand for rapid resolution."
2. Identify 3-5 OTHER domains with the same abstract structure but completely different surface areas:
   - Triage in emergency medicine
   - Air-traffic-control routing
   - Fire-station dispatch
   - Old-school newspaper editor's queue
   - Confessional in a busy parish
3. For each analogous domain, list its DOMAIN-SPECIFIC mechanisms — how do practitioners actually solve the abstracted problem?
4. Map each mechanism back to your domain. Some will transfer cleanly; some will require adaptation; some will be inapplicable.
5. The transferred mechanisms become idea candidates.

## Anti-mode-collapse prompts
- The analogous domains MUST have completely different surface areas. "Customer support" → "tech support" is not a useful analogy; same surface domain.
- The abstract structure should be 1-2 sentences and contain no domain-specific words. If you can't strip the words, you haven't abstracted.
- Borrowed mechanisms must be SPECIFIC. "Triage" is a label; "color-coded tags applied at intake based on a 4-question decision tree" is a mechanism.

## Example application (synthetic)
Problem: "Improve quality of code review at scale."

Abstract: "Distributed asynchronous evaluation of intermittent quality artifacts, with variable reviewer expertise and time pressure."

Analogous domains:
- **Peer review in academic journals**: 2-3 reviewers with explicit competence claims, structured rubrics, editor as tiebreaker, recommendation taxonomy (accept / minor / major / reject).
- **Restaurant kitchen line checks**: every plate before service is checked by a single named expediter, who refuses non-conforming plates and the line cook fixes immediately. Real-time, single-reviewer.
- **Theater dress rehearsal**: full-context simulation before "live"; problems found in dress rehearsal are categorized differently than problems found in production.

Mapped ideas:
- Reviewers must declare competence area at top of comment ("I know X subsystem, weak on Y subsystem"). Forces explicit information sharing.
- Single named "code expediter" per service per week — gates all merges, owns quality outcomes, real-time feedback.
- Pre-merge dress rehearsal: PR runs a representative-traffic simulation before review starts. Issues found there are tagged differently from logic review issues.

## Output format
- Abstract structure (1-2 sentences)
- 3-5 analogous domains + specific mechanisms
- 5-8 mapped ideas
