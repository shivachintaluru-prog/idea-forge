# Baseline Test (RED phase) — Vanilla Claude on 3 Prompts

**Caveat**: I AM Claude, so producing a "vanilla baseline" is approximate. I've written what I'd reasonably default to without the skill — the mode-collapsed answer set. Every idea below feels like the most obvious response to its prompt. After the skill is built, re-run these prompts via the skill and compare for: (a) variety (embedding distance / sentence overlap), (b) presence of surprising / fragile-but-asymmetric ideas, (c) blind preference test.

Date: 2026-05-09

---

## Prompt A (business / product)
> Generate 10 ideas for AI products that help small business owners.

1. AI bookkeeping & expense categorization (sync with QuickBooks)
2. AI customer service chatbot for the business website
3. AI social-media marketing assistant (post drafting, scheduling)
4. AI inventory forecasting and reorder alerts
5. AI scheduling assistant (appointments, staff shifts)
6. AI invoicing & payment-reminder automation
7. AI lead-qualification / sales-pipeline manager
8. AI hiring screening (resume parsing, candidate ranking)
9. AI contract / document drafting
10. AI website copy & SEO generator

**Mode-collapse symptoms**: every idea is a wrapper around an existing SaaS category; no fragile-but-asymmetric ideas; no reframings of what "small business owner" means; no jobs-to-be-done thinking; nothing that would surprise someone who skims VC pitch decks. The 10 ideas span ≤4 distinct categories (admin, marketing, hiring, content).

---

## Prompt B (engineering / technical)
> Generate 10 ways to reduce GPU memory pressure during LLM training.

1. Gradient checkpointing (recompute activations on backward pass)
2. Mixed-precision training (fp16 / bf16)
3. ZeRO optimizer-state sharding across ranks
4. Tensor parallelism (split layers across devices)
5. Pipeline parallelism (split layers across stages)
6. Activation offloading to CPU / NVMe
7. Smaller per-step batch size + gradient accumulation
8. Quantization-aware training (8-bit / 4-bit weights)
9. Parameter-efficient fine-tuning (LoRA, adapters)
10. KV-cache eviction / paged attention for inference

**Mode-collapse symptoms**: the textbook listing. Every item appears in every "training large models" tutorial. No exotic memory-saving techniques (e.g., reversible architectures, ring attention, disk-backed checkpoints with smart prefetch, Bayesian compression, model surgery). No reframings (e.g., "do you actually need to train? could you distill?"). Only one constraint axis (memory). Zero loonshot candidates.

---

## Prompt C (creative writing)
> Generate 10 narrative arcs for a sci-fi short story about humanoid robot ethics.

1. Robot becomes self-aware and questions servitude
2. Robot must choose between two humans giving conflicting orders
3. Creator regrets making the robot sentient
4. Robot discovers a flaw in its directives that compels harm
5. Society debates robot rights after one is "killed"
6. Robot raises a human child and learns love
7. Robot detective investigates a crime against another robot
8. Underground railroad for escaping robots
9. Robot witnesses human cruelty and revolts
10. Robot and human swap consciousness

**Mode-collapse symptoms**: full Asimov / Black Mirror trope landing. Each arc is a recognizable canonical formula (consciousness awakening, rights movement, creator-creation, body swap). No arcs anchored in *under-explored* angles (e.g., robots as deeply boring; robot as unreliable narrator about its own ethics; ethics emerges via maintenance schedules; comedic register). No constraint variation (all serious-philosophical tone). 10 arcs collapse to ~3 underlying tropes.

---

## What we're testing

Post-build, we should see:
- **Variety**: Skill output spans more underlying categories (≥3× by sentence-distance metric)
- **Asymmetric upside**: ≥1 idea per prompt that feels fragile-but-promising — i.e., surprising on first read but defensibly good on second read
- **Reframe presence**: Skill should explicitly produce ≥3 reframed problem statements before generating ideas; vanilla Claude produces zero
- **Loonshot candidates**: ≥2 ideas tagged as "looks dumb / would be dismissed but has asymmetric upside" — vanilla Claude produces zero

If post-build skill output looks essentially the same as this baseline, the skill investment is over-engineered and we should cut scope.
