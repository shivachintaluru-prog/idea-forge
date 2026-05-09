# Domain Detection

Phase 1 must emit a single-word `Domain` tag. The selection algorithm in `frameworks/INDEX.md` filters frameworks by `domain-fit`, so the tag matters for which frameworks become available.

## The 5 domains + 1 fallback

| Tag | Meaning | Signals in problem statement |
|---|---|---|
| `business` | Strategy, market positioning, business model, revenue, go-to-market | "market," "customer acquisition," "revenue," "competitive," "pricing," "B2B/B2C," "growth," "retention" |
| `product` | Product features, user experience, product-market fit, individual product decisions | "feature," "UX," "user flow," "onboarding," "engagement," "users want," "use case" |
| `engineering` | System design, architecture, performance, reliability, infrastructure, code quality | "architecture," "scalability," "latency," "throughput," "reliability," "code," "system," "infrastructure" |
| `research` | Investigation, hypothesis, methodology, literature, experiments | "study," "investigate," "hypothesis," "research question," "experiment," "literature," "methodology," "paper" |
| `creative` | Narrative, design, art, writing, music, performance | "story," "narrative," "design aesthetic," "tone," "voice," "scene," "character," "visual" |
| `other` | None of the above fit cleanly | Personal life decisions, philosophical questions, civic / political problems, hybrid problems that span domains, problems with no domain anchor |

## Decision rule

1. If the problem statement contains ≥2 signals from ONE domain and ≤1 from the others → tag with the dominant domain.
2. If the problem spans 2 domains roughly equally (e.g., "design a B2B product"), pick the domain that the USER's role/intent suggests. Example: "I'm a PM trying to ship X" → product. "I'm a founder trying to position X" → business.
3. If the problem genuinely doesn't fit any 5 (e.g., "ideas for my wedding speech," "how should I structure my personal finances") → tag as `other`. The selection algorithm uses the full framework set with no domain filter.

## What the tag does

- Filters `frameworks/*.md` where `domain-fit` lacks the tag.
- For `other`, no filter is applied — the full 28 frameworks are eligible (with normal favorites-bias and constraint-type filters still in effect).

## Edge cases

- **Multi-domain problem**: tag with the user's primary lens, but consider running a SECOND session with a different tag for cross-pollination value. (User-elective.)
- **User explicitly disagrees with the tag**: re-tag per user direction. The tag is for selection, not for the user.
- **Domain unclear after Phase 1 questions**: default to `other`. Better to over-broaden the framework pool than to mis-filter.

## Anti-mode-collapse for domain detection

- Do NOT default to `business` for any vague prompt. The "I want creative ideas" baseline often gets tagged business by reflex; if the problem is actually about a personal project, tag `other` or `creative`.
- Do NOT use `business` as a catchall for product problems. Product is specifically about user-facing decisions; business is about company-level positioning.
- The 6 tags are NOT exhaustive of human problem types. The `other` tag is intentional — the skill scales beyond business by FALLING BACK rather than forcing a tag.
