---
name: idea-forge
description: Use when generating creative ideas, brainstorming new products, features, strategies, or solutions; exploring solution space for a problem; or stuck looking for novel approaches.
---

# The Iron Law

NEVER skip a phase. NEVER apply a single framework. NEVER converge before Phase 5. Each phase exits ONLY when its literal exit artifact appears in the conversation.

# When NOT to use

- Refining or evaluating an EXISTING idea — use `superpowers:brainstorming` instead
- Choosing between known options — use a decision framework
- Feasibility analysis or business-case work — wrong tool
- Prompts with no problem to chew on ("just give me a quick answer")

# Modes

- **Deep (default)**: 5 phases, 4-5 frameworks, ~8-12 turns
- **`--quick`**: compressed — 1 reframe, 2 frameworks, no Phase 4, ~6 turns. **Trade-off**: quick mode weakens or removes 4 of the 10 anti-collapse mechanisms (#1 framework variety becomes ≥2 types not ≥3; #5 provocation step removed with Phase 4; #7 reframe gate is single-reframe; #8 cross-pollination skipped). Use only when time-constrained; deep mode preserves the full mission.

# Process

```
Phase 1: Frame → Phase 2: Reframe → Phase 3: Diverge → Phase 4: Cross-pollinate → Phase 5: Surface
                                                           ↳ skipped in --quick
```

Each phase has a hard exit artifact. Do NOT proceed to the next phase until the artifact pattern appears in the conversation.

| # | Phase | Action | Exit artifact (literal) |
|---|---|---|---|
| 1 | Frame | Clarify problem, detect domain via 4-5 questions | `## Problem Statement` + `## Domain` (single-word tag) |
| 2 | Reframe | Apply 3 reframing techniques (1 in `--quick`) | `## Reframes` + ≥3 numbered (≥1 in quick) + `**Selected reframe(s):**` |
| 3 | Diverge | Pick frameworks via algorithm, generate 5-10 ideas per | `## Raw Ideas` with `### <Framework name>` subsections |
| 4 | Cross-pollinate | Force-combine cross-framework pairs + Worst Possible Idea | `## Hybrid Ideas` with ≥5 numbered (skipped in `--quick`) |
| 5 | Surface | Loonshot lens, False Fail check, devil's advocate, curate | `## Curated Ideas` + `### Loonshot Candidates` ≥2 (≥1 in quick) |

Detail per phase: `phases/01-frame.md` … `phases/05-surface.md`. Read each phase file at phase entry.

# Framework selection (Phase 3 entry)

Use the deterministic algorithm in `frameworks/INDEX.md`. Summary:

1. Filter `frameworks/*.md` where `domain-fit` includes the detected domain
2. Group by `constraint-type`: `{semantic, structural, random-stimulus, inversion, temporal}`
3. Compute seed per the canonical recipe in `frameworks/INDEX.md` Step 3 (first 30 words of problem + first reframe; word_count × 17 + first-letter-ord sum). Record BOTH `seed mod 5` AND `favorites_value = (seed // 13) mod 7`.
4. Exclude `favorites-bias: true` frameworks (SCAMPER, Six Hats, JTBD, first-principles, inversion, blue-ocean-errc — see catalog) UNLESS `favorites_value == 0` (independent ~14% channel).
5. Deep: draw 1 from each of 4 distinct constraint-types + 1 wildcard. Quick: draw 1 each from 2 types.
6. Result must cover ≥3 distinct constraint-types (≥2 in quick).

# Anti-mode-collapse rules

1. Forced framework variety (≥3 constraint-types)
2. Quantity quotas before judgment (≥10 ideas before evaluating any)
3. Constraint injection (apply each framework by its specific constraints, not your paraphrase)
4. Random stimulus (≥1 framework per session must be `random-stimulus` type)
5. Provocation (Phase 4 includes "absurd idea" step + "what's true here?")
6. Loonshot bias (Phase 5 rewards fragile-but-asymmetric ideas)
7. Reframe gate (Phase 2 cannot exit without artifact)
8. Cross-pollination gate (Phase 4 cannot exit in deep mode without artifact)
9. Anti-favorites bias (SCAMPER / Six Hats / JTBD / First Principles / Inversion / Blue Ocean ERRC excluded by default)
10. No idea-killing in early phases (judgment deferred to Phase 5)

Detail with bad-vs-good examples: `references/anti-mode-collapse.md`.

# Red Flags (rationalizations to reject)

| Thought | Reality |
|---|---|
| "User just wants quick ideas" | Use `--quick`, but understand it materially weakens 4 anti-collapse mechanisms. Confirm the user accepts the trade. Do NOT default to `--quick` for brevity if the user wants 'wonderful' over 'fast'. |
| "Phase 2 is overkill, the problem is clear" | Reframing is where breakthroughs are born. The exit artifact is required. |
| "These frameworks all say similar things" | They don't. Apply each by its constraints, not your paraphrase. |
| "I have enough ideas after Phase 3" | Cross-pollination produces ideas no single framework can. |
| "User said 'just generate ideas, skip the reframe'" | The skill's value depends on the gates. Honor them or don't invoke this skill. |
| "I'll pick the 4 frameworks I know best" | Anti-favorites bias is mandatory; let the algorithm pick. |
| "I can shortcut Phase 1 — the prompt is detailed enough" | The Domain tag is required for selection. Emit the artifact. |

# Sub-agent usage (optional)

For Phase 3 framework application, you MAY dispatch sub-agents in parallel — one per selected framework. Each sub-agent receives: the framework file path, the problem statement, the selected reframe, and the framework's anti-mode-collapse prompts. It returns 5-10 ideas. The orchestrator concatenates results into `## Raw Ideas`. This reduces context pressure and produces more independent application of each framework's constraints. Not required, but recommended when running deep mode with the full 5-framework variety.
