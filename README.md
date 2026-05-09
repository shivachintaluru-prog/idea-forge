# `idea-forge` — A Claude Code Skill for Generating Wonderful Ideas

A multi-phase ideation skill that fights LLM mode collapse — the tendency to produce most-likely-and-therefore-generic responses. Instead of a single round of brainstorming, `idea-forge` runs a structured 5-phase session that orchestrates 4-5 different creative-thinking frameworks per session, with explicit anti-mode-collapse mechanisms at every step.

## When to use

Invoke when:
- Generating ideas for new products, features, strategies, or solutions
- Exploring solution space for a problem
- Stuck looking for novel approaches
- The obvious ideas feel obviously inadequate

## When NOT to use

- **Refining or evaluating an existing idea** — use `superpowers:brainstorming` instead. That skill is convergent; `idea-forge` is divergent.
- **Choosing between known options** — use a decision framework
- **Feasibility analysis or business-case work** — wrong tool
- **"Just give me a quick answer" requests with no problem framing** — the skill needs a problem to chew on

## How it works

Every session runs 5 phases (or a compressed 4-phase `--quick` variant). Each phase has a hard exit artifact (a literal pattern in the conversation) so it cannot be silently skipped.

| Phase | Action |
|---|---|
| 1. Frame | Clarify problem; detect domain |
| 2. Reframe (gate) | Generate ≥3 alternative problem statements |
| 3. Diverge | Apply 4-5 frameworks (selected via deterministic algorithm); generate 25-50 raw ideas |
| 4. Cross-pollinate (gate) | Force-combine ideas across frameworks; generate ≥5 hybrids |
| 5. Surface | Loonshot lens + False Fail check + devil's advocate; curate top 7-10 |

Output includes ≥2 "loonshot candidates" — fragile-but-asymmetric ideas that look weak at first glance but have outsized upside.

## Modes

- **Deep (default)**: full 5-phase session, ~8-12 turns
- **`--quick`**: compressed — 1 reframe, 2 frameworks, no cross-pollination, ~6 turns

## Framework library

28 frameworks across 5 constraint-types:

- **semantic**: SCAMPER, JTBD, Six Thinking Hats, Hall of Fame, Blue Ocean ERRC, Analogous Domain
- **structural**: Cherry Split, Phoenix, Slice and Dice, Tug of War, Think Bubbles, Phase Separation, P-vs-S Loonshot, Bushes vs Trees, TRIZ Contradictions, First Principles, Morphological Analysis
- **random-stimulus**: Brutethink, Provocation (PO), Random Stimulation, Crazy 8s
- **inversion**: False Faces, False Fail Test, Inversion, Worst Possible Idea
- **temporal**: Three B's, Three Deaths, Critical Mass

The selection algorithm picks 4-5 (deep) or 2 (quick) frameworks per session, biased away from the most-trained-on three (SCAMPER, Six Hats, JTBD) by default — those only appear when `seed mod 5 == 0`.

## Distinction from `superpowers:brainstorming`

| | `superpowers:brainstorming` | `idea-forge` |
|---|---|---|
| Direction | Convergent (idea → design) | Divergent (problem → many ideas) |
| Use case | "I have an idea, help me design it" | "I have a problem, help me find unconventional solutions" |
| Output | A spec / plan | A curated set of 7-10 ideas |
| Mechanism | Clarifying questions, design proposal | Multi-framework rotation with anti-mode-collapse gates |

The two skills are complementary. A typical workflow: `idea-forge` to generate ideas → `superpowers:brainstorming` to refine the chosen one into a design.

## Install

Copy the skill into your `~/.claude/skills/` directory:

```powershell
Copy-Item -Path "<this-directory>" -Destination "$env:USERPROFILE\.claude\skills\idea-forge" -Recurse -Force -Exclude "_dev","README.md"
```

The `-Exclude "_dev","README.md"` keeps dev-only artifacts out of the install. After install, invoke as `/idea-forge` from any Claude Code session.

## File structure

```
idea-forge/
├── SKILL.md                  # main skill file (loaded on invocation)
├── phases/                   # 5 phase files with exit-artifact specs
├── frameworks/               # 28 framework files + INDEX.md (selection algorithm)
├── references/               # anti-mode-collapse, domain-detection, idea-quality-criteria
└── examples/                 # 5 worked end-to-end examples (business, product, eng, research, creative)
```

The `_dev/` subdirectory in this development copy contains pre-build baseline measurements; it is NOT shipped.

## Status

v1, built 2026-05. Worked-example coverage: business, product, engineering, research, creative. Verification pending (see plan file).
