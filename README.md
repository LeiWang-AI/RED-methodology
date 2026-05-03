# RED: Recursive Execution Decomposition

**A verification-gated protocol for surfacing hidden assumptions and missing fundamentals.**

RED audits plans, systems, and research methods by recursively decomposing them into executable actions until each leaf maps to a registered primitive. Any dependency that cannot be reproducibly verified is treated as **missing work**, not as an assumption.

## Paper

📄 **[paper.pdf](paper.pdf)** 

> *Recursive Execution Decomposition (RED): A Verification-Gated Protocol for Surfacing Hidden Assumptions and Missing Fundamentals*

## What RED Does

| Input | Output |
|-------|--------|
| A plan, system, or method | Hierarchical decomposition tables |
| Implicit assumptions | Explicit, auditable dependencies |
| "It should work" | VERIFIED_HAVE or MISSING status |
| Missing fundamentals | Actionable resolution tasks |

## Quick Start

1. **Define** your artifact (plan, system, method) and success criteria
2. **Decompose** recursively until actions map to primitives
3. **Audit** each primitive: Does the tool exist? Do you have the knowledge? Do you have access?
4. **Convert** every MISSING → resolution task

## Core Concepts

### Primitives
An action is **primitive** when it satisfies three conditions:
- **Tool exists** — the capability/library/API is available
- **Knowledge exists** — you know how to use it
- **Access exists** — you have permissions/credentials

### Verification Policy
- **VERIFIED_HAVE**: requires reproducible evidence (command output, code reference, config check)
- **MISSING**: anything that cannot be verified on demand

No "assumed okay" state exists.

## Templates

| Template | Purpose |
|----------|---------|
| [L1 Decomposition](templates/l1-decomposition.md) | Parent→child action mapping |
| [Primitive Audit](templates/primitive-audit.md) | Tool/knowledge/access verification |
| [Full RED Table](templates/full-red-table.md) | Complete analysis template |

## Example Primitive Registry

| Domain | Registry |
|--------|----------|
| [Software Engineering](registries/software-engineering.md) | Common dev primitives |

## AI-Assisted RED

RED works well with LLM assistance. See the [Prompting Guide](prompts/ai-assisted-red.md) for:
- Decomposition prompts
- Audit table generation
- Gap identification patterns

**Key principle:** LLM generates, human validates. RED's verification gates catch hallucinations.

## When to Use RED

- Engineering design reviews
- Research-to-deployment translation
- Post-failure debugging and root cause analysis
- Human–AI collaboration where plans drift into assumptions
- Auditing LLM-generated plans

## What RED is NOT

- **Not a planner** — RED audits plans; it doesn't generate them
- **Not an optimizer** — RED surfaces what's missing; it doesn't select the best path
- **Not a proof** — RED identifies gaps; it doesn't guarantee success
- **Not exhaustive** — RED is bounded by registry quality and decomposition depth

## License

MIT License — use freely, attribution appreciated.

## Citation

```bibtex
@article{red2026,
  title={Recursive Execution Decomposition (RED): A Verification-Gated Protocol for Surfacing Hidden Assumptions and Missing Fundamentals},
  author={[Your Name]},
  journal={arXiv preprint},
  year={2026}
}
```

## Contributing

Contributions welcome! Especially:
- New primitive registries for different domains
- Case studies applying RED
- Improvements to templates

---

*RED converts implicit assumptions into explicit, auditable objects.*

