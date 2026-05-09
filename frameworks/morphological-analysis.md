---
name: morphological-analysis
domain-fit: engineering, product, research
constraint-type: structural
secondary-constraint-type: semantic
favorites-bias: false
---

## When to use
The solution space has multiple INDEPENDENT parameters, each with several possible values. Morphological Analysis enumerates the parameter space as a matrix and forces consideration of cells that conventional thinking skips. Best for problems with 3-5 well-defined design dimensions (architecture choices, product configurations, research methodology variants).

## The technique
1. Identify the 3-5 independent PARAMETERS of the solution space.
   - Good parameters are orthogonal — varying one doesn't determine another.
   - Bad parameters co-vary — splitting them is fake variety.
2. For each parameter, list 3-5 possible VALUES — including non-obvious ones.
3. Build the matrix: rows = parameters, columns = values. Total cells = product of value counts (e.g., 4 params × 4 values = 256 combinations).
4. The full enumeration is too large; sample strategically:
   - Mark the "default" cell (what conventional thinking would pick) in each row.
   - Generate ideas by INTENTIONALLY picking non-default cells in each row.
   - Force at least 3 ideas where ALL rows pick non-default values simultaneously.
5. The all-non-default ideas are the high-value cells morphologically — combinations no one explores because each individual non-default seems "wrong."

## Anti-mode-collapse prompts
- Parameters MUST be orthogonal. If varying parameter A predicts the value of parameter B, they're a single parameter in disguise. Re-decompose.
- Values per parameter must include at least one NON-OBVIOUS value. The default values represent the convergent attractor; non-obvious values open the space.
- The all-non-default ideas FEEL wrong when generated. That's the signal — keep them. Mode collapse rejects them; that's why morphological analysis exists.

## Example application (synthetic)
Problem: "Design a new evaluation methodology for LLMs in enterprise contexts."

Parameters:
- **Evaluator** (default: human): {human, automated, peer-LLM, synthetic-customer}
- **Task generation** (default: pre-defined benchmark): {pre-defined, real-customer-traces, generated-on-demand, adversarially-co-designed}
- **Outcome metric** (default: accuracy): {accuracy, customer-satisfaction-proxy, time-to-resolution, downstream-business-impact}
- **Cadence** (default: pre-release one-time): {pre-release, weekly, continuous-shadow, on-customer-trigger}

Default cell: human + pre-defined + accuracy + pre-release. Standard benchmark eval.

All-non-default ideas:
- **Synthetic-customer + adversarially-co-designed + downstream-business-impact + on-customer-trigger**: an evaluation methodology where synthetic customers (themselves AI-generated) propose adversarial trial scenarios, evaluation runs only when triggered by an actual customer issue, and the metric is whether the resolution prevented downstream churn 30 days later.
- **Peer-LLM + generated-on-demand + time-to-resolution + continuous-shadow**: a peer LLM watches every interaction, generates on-demand harder variants, scores time-to-resolution, runs continuously in shadow.

Both ideas are non-obvious AND non-trivial. Neither would emerge from "improve LLM evaluation."

## Output format
- 3-5 orthogonal parameters with default + 2-4 non-default values each
- 5-8 ideas, including ≥3 with all-non-default cell choices
