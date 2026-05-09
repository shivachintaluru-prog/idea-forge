# Anti-Mode-Collapse Reference

Mode collapse: the LLM tendency to converge on the most-likely (= most-generic) response given a prompt. The 10 mechanisms below are the engine of `idea-forge`'s "wonderful ideas" claim. Each mechanism is paired with a bad-vs-good example so the pattern is explicit.

## 1. Forced framework variety per session (≥3 constraint-types)

**Bad**: Apply 4 frameworks all in `semantic` constraint-type because they're the most familiar (SCAMPER, JTBD, Six Hats, Blue Ocean). Outputs all share a "what could we substitute / add / change" shape.

**Good**: Apply 4 frameworks across `semantic, structural, random-stimulus, inversion` constraint-types. Outputs span "what does it become if we recategorize," "what does it become if we decompose differently," "what does an unrelated stimulus suggest," and "what would guarantee the opposite."

The constraint-types map onto fundamentally different *cognitive operations*. Variety across them is variety in the operation, not just the topic.

## 2. Quantity quotas before judgment (≥10 before evaluating)

**Bad**: After idea 3, start labeling ideas as "promising" / "weak." By idea 5, generation slows because each new idea is being silently judged against the others. Total: 5-7 ideas.

**Good**: Generate 10+ ideas with NO commentary, no asterisks, no judgment phrasing. Then, in a separate pass, evaluate. Total: 10-15 raw ideas, evaluated as a SET rather than as a serial filter.

Mode collapse hides as quality control. The fastest way to defeat it: separate generation from evaluation by an explicit quota.

## 3. Constraint injection per framework

**Bad**: "Apply SCAMPER to onboarding" → produce 7 generically-labeled ideas that are all variations of "make onboarding better in some way."

**Good**: "For SCAMPER's Substitute step: list 3 specific substitution candidates for the onboarding flow's PRIMARY ACTOR (currently 'the user'). DO NOT use 'AI' as a substitute (favorites bias). Pick the most surprising of the 3."

The framework is only a framework if its constraints are applied as constraints. Vague application = no framework.

## 4. Random-stimulus floor (≥1 random-stimulus framework per session)

**Bad**: Session uses 4 analytical / structured frameworks. All ideas are within-domain, comprehensible, "sensible." Variety is structural but not topical.

**Good**: Session includes Brutethink with random word "lighthouse" or Random Stimulation with profession "1920s railway switchman." At least 1 idea per session is anchored to an unrelated stimulus, producing connections that wouldn't otherwise exist.

The random stimulus is the escape valve — the explicit forcing function for cognitive distance. Skipping it is the most subtle form of mode collapse.

## 5. Provocation step (Phase 4 absurd idea + "what's true here?")

**Bad**: Phase 4 produces hybrids by combining "sensible" pairs of ideas. All hybrids are minor variants of their parents.

**Good**: Phase 4 includes a provocation: "What if the customer experienced the product before signing up?" Treat as if true. Generate 2-3 ideas that satisfy the provocation literally (sample-of-actual-experience, before-signup retroactive billing, etc.). The seemingly-absurd ideas have real cores.

## 6. Loonshot bias (Phase 5 rewards fragile-but-asymmetric)

**Bad**: Phase 5 ranks ideas by "feasibility × impact." Top 7 are all moderate-feasibility, moderate-impact. Same shape as a corporate brainstorm output.

**Good**: Phase 5 uses (novelty × asymmetric upside) as the primary ranking, with feasibility as a tiebreaker. Loonshot Candidates subsection explicitly contains ≥2 ideas tagged as "looks fragile / would be dismissed" but with named asymmetric upside.

The skill optimizes for "wonderful," not "safe." Default ranking systems destroy the wonderful tail.

## 7. Reframe gate (Phase 2 cannot exit without artifact)

**Bad**: Skill produces a 1-line problem statement and proceeds to ideation. Generates 30 ideas, all anchored to the original framing. Convergent.

**Good**: Skill explicitly emits `## Reframes` with 3+ alternative problem statements. The reframe pool is the seed for Phase 3, not the original framing. Each reframe carries different ideas through.

Reframing is where ~50% of breakthrough thinking happens. Skipping it is skipping most of the value.

## 8. Cross-pollination gate (Phase 4 cannot exit in deep mode)

**Bad**: After Phase 3 produces 30 framework-tagged ideas, skill jumps to curation. The framework-tagged ideas remain in their silos. Curation picks the "best of each silo."

**Good**: Phase 4 forces hybrids across silos. A SCAMPER-Substitute idea + a Random-Stimulation idea = a hybrid that neither silo could have produced alone. Curation in Phase 5 has access to the hybrid pool, not just the silo pool.

Cross-pollination produces ~25% of the final wonderful ideas. They don't exist in any single framework.

## 9. Anti-favorites bias (SCAMPER / Six Hats / JTBD excluded by default)

**Bad**: Every session uses SCAMPER and JTBD. Outputs feel familiar — same shape, similar idea types. Across sessions, the IDEA POOL is constrained to what these 2-3 frameworks produce.

**Good**: Sessions DEFAULT to excluding SCAMPER, Six Hats, JTBD. They only appear when `seed mod 5 == 0` (1-in-5 sessions). The remaining 25 frameworks dominate the diet, producing across-session variety.

Training-frequency bias is real. SCAMPER appears more frequently in Claude's training than Cherry Split. Without an explicit anti-bias mechanism, every session converges on the training-frequency winners.

## 10. No idea-killing in early phases (judgment deferred to Phase 5)

**Bad**: During Phase 3 generation, mark ideas as `(unfeasible)` or `(weak)` inline. Self-prune as you go. By the end of Phase 3, the SET of generated ideas already reflects Phase 5 criteria — convergent.

**Good**: During Phase 3, generate without judgment. Keep ideas raw, including ones that "obviously won't work." Phase 5's False Fail check often resurrects those — many "obvious failures" are False Fails, killed by context not by the idea.

The False Fail check requires a healthy graveyard. Pre-pruning empties the graveyard.

## How to use this reference

Read this file at the start of any `idea-forge` session. The mechanisms above are not optional best-practices — they're the load-bearing structure that distinguishes the skill's output from baseline. Each phase file enforces a subset of these; this reference is the canonical explanation.

If a session output looks like baseline LLM ideation, audit against the 10 mechanisms above. Usually 1-2 were silently skipped — find them and re-run that phase.
