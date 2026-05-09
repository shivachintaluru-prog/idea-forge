---
name: jtbd
domain-fit: business, product
constraint-type: semantic
secondary-constraint-type: structural
favorites-bias: true
---

## When to use
Reframe the problem as a JOB — what is the user trying to accomplish, in what context, with what desired outcome? The reframe shifts focus from features to causation: people don't buy products, they hire them to do a job. The "job" framing exposes alternatives the user could have chosen instead.

## The technique
1. Write the canonical job statement: "When [situation], I want to [motivation], so I can [expected outcome]."
2. List the COMPETITIVE SET — every alternative the user might "hire" for this job, including non-obvious ones (procrastination, asking a friend, doing nothing). Aim for 8-12 alternatives.
3. Identify the FAILURE MODES of each alternative — why does the user reject or eventually leave each one?
4. Generate ideas that:
   - Combine the strengths of multiple competitive alternatives
   - Eliminate a specific failure mode that all current alternatives share
   - Serve a JOB that's actually a sub-job or super-job of the original (re-segment by job, not demographic)
5. Tag each idea with which alternative(s) it cannibalizes.

## Anti-mode-collapse prompts
- The job statement must NAME a specific outcome, not a generic want. "I want to learn faster" is empty; "I want to retain new domain vocabulary 6 weeks after first exposure" is a job.
- The competitive set must include NON-OBVIOUS alternatives. "Hiring a tutor" is obvious; "writing about it on social media to perform learning" is non-obvious. Force at least 3 non-obvious alternatives.
- Avoid feature-as-idea. Every idea must be framed in the user's outcome language, not the product's capability language.

## Example application (synthetic)
Job: "When I'm preparing for a difficult conversation at work, I want to anticipate the other person's likely responses, so I can avoid being blindsided."

Competitive set: rehearsing in head; talking to a friend; writing a script; ChatGPT roleplay; postponing the conversation; "winging it" with confidence; reading a relevant book chapter.

Failure modes: rehearsal in head fails because you can't simulate counter-arguments well; friends are biased toward you; scripts feel rigid; ChatGPT is generic; postponement compounds anxiety; winging it has high variance.

Ideas:
- Pair-rehearsal with someone playing devil's advocate from a known opposing-disposition profile (e.g., "play this as if you were maximally dismissive")
- Real-time coach during the actual conversation (earpiece + LLM listening to the other party)
- Post-conversation diagnostic: record + replay + identify the moments you were blindsided

## Output format
- Job statement
- 8-12 alternatives + failure modes
- 5-8 ideas, each tagged with cannibalized alternatives
