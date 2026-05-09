---
name: false-fail-test
domain-fit: business, product, engineering, research
constraint-type: inversion
secondary-constraint-type: temporal
favorites-bias: false
---

## When to use
Many ideas have already been "tried and failed" — but the failure was due to context, timing, implementation, or framing rather than the idea itself. The False Fail Test mines the graveyard of dead ideas for ones that deserve resurrection under different conditions.

## The technique
1. List 5-10 ideas in your problem space that are commonly considered "tried and failed" — the obvious dismissals, conventional wisdom about what doesn't work.
2. For each, ask the False Fail diagnostic:
   - **Was the idea bad, or was the context wrong?** (Wrong era, wrong audience, wrong distribution channel, wrong technology, wrong economic conditions.)
   - **Was the idea bad, or was the implementation flawed?** (Wrong team, wrong execution sequence, premature scaling, inadequate funding.)
   - **Was the idea bad, or was the framing misleading?** (Marketed as one thing when it was actually another.)
3. For ideas where the diagnostic suggests a False Fail: write the resurrected version with the corrected context/implementation/framing.
4. Tag the resurrected idea with the specific change that makes it viable now.

## Anti-mode-collapse prompts
- Do NOT skip "obvious failures." The most valuable False Fails hide behind the strongest social consensus that they "don't work."
- The diagnostic must produce a SPECIFIC corrected condition, not a vague "if done right." If you cannot name the specific change, the failure was probably real.
- The resurrected idea should pass a "would I bet on it now, given the change?" test. If you wouldn't, you haven't found a True False Fail.

## Example application (synthetic)
Idea graveyard: "Pay-per-use software pricing for B2B."

- Common dismissal: "Enterprises hate variable bills."
- False Fail diagnostic:
  - Wrong context? Pre-cloud, variable cost was operationally hard. Post-cloud + post-FinOps, variable cost is the default for infra.
  - Wrong implementation? Earlier attempts metered awkward dimensions (CPU-seconds, query count) that didn't map to user value. Metering dimensions like "successful outcomes delivered" reframes the bill.
  - Wrong framing? Marketed as cost-savings when it should have been marketed as outcome-aligned partnership.
- Resurrected version: B2B SaaS priced per "successful outcome" (definition co-designed with the buyer at contract time). Bill is variable but tied 1:1 to value capture.

## Output format
- 5-10 graveyard ideas
- Diagnostic per idea
- 2-4 resurrected versions with specific corrections noted
