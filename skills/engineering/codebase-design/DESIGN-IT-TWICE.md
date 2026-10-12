# Design It Twice

When the user wants to explore alternative interfaces for a chosen candidate, develop contrasting designs sequentially in the current agent. Based on "Design It Twice" (Ousterhout): your first idea is unlikely to be the best. Use delegated agents only when the user explicitly requests delegation, and parallel agents only when the user explicitly requests parallel work. Heavy validation still follows the workspace's resource limits.

Uses the vocabulary in [SKILL.md](SKILL.md): **module**, **interface**, **seam**, **adapter**, **leverage**.

## Process

### 1. Frame the problem space

Write a concise user-facing explanation of the problem space for the chosen candidate:

- The constraints any new interface would need to satisfy
- The dependencies it would rely on, and which category they fall into (see [DEEPENING.md](DEEPENING.md))
- A rough illustrative code sketch to ground the constraints, not a proposal, just a way to make the constraints concrete

Show this to the user, then proceed to Step 2 within the requested scope. Ask only if a material constraint or authorization is missing.

### 2. Develop contrasting designs

Develop two or three **radically different** interfaces sequentially. Reuse the known codebase context rather than surveying it again for every alternative.

Use the same technical facts (file paths, coupling details, dependency category from [DEEPENING.md](DEEPENING.md), what sits behind the seam), but give each alternative a different design constraint:

- Alternative 1: "Minimize the interface: aim for 1–3 entry points max. Maximise leverage per entry point."
- Alternative 2: "Optimise for the most common caller: make the default case trivial."
- Alternative 3 (if justified by actual variation): "Design around ports & adapters for cross-seam dependencies."

Use the definitions in [SKILL.md](SKILL.md) and the project's existing glossary so alternatives use consistent architecture and domain language.

For each alternative, describe:

1. Interface (types, methods, params, plus invariants, ordering, error modes)
2. Usage example showing how callers use it
3. What the implementation hides behind the seam
4. Dependency strategy and adapters (see [DEEPENING.md](DEEPENING.md))
5. Trade-offs: where leverage is high, where it's thin

### 3. Present and compare

Present designs sequentially so the user can absorb each one, then compare them in prose. Contrast by **depth** (leverage at the interface), **locality** (where change concentrates), and **seam placement**.

After comparing, give your own recommendation: which design you think is strongest and why. If elements from different designs would combine well, propose a hybrid. Be opinionated: the user wants a strong read, not a menu.
