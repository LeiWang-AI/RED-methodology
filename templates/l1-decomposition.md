# L1 Decomposition Template

Use this table to map parent actions to child actions during RED analysis.

## Instructions

1. Start with your top-level action (the goal or artifact being analyzed)
2. Decompose into sub-actions
3. For each sub-action, identify resources touched and required
4. Mark whether each action is a primitive (atomic) or needs further decomposition
5. Assign status: VERIFIED_HAVE or MISSING

---

## Decomposition Table

| ID | Parent Action | Child Action | Resources Touched | Resources Required | Outputs | Primitive? | Status |
|----|---------------|--------------|-------------------|-------------------|---------|------------|--------|
| 1.1 | [Top-level goal] | [First sub-action] | | | | Y/N | |
| 1.2 | [Top-level goal] | [Second sub-action] | | | | Y/N | |
| 1.3 | [Top-level goal] | [Third sub-action] | | | | Y/N | |
| 2.1 | 1.1 | [Sub-sub-action] | | | | Y/N | |
| ... | ... | ... | | | | | |

---

## Status Legend

| Status | Meaning | Evidence Required |
|--------|---------|-------------------|
| **VERIFIED_HAVE** | Dependency exists and is verified | Command output, code reference, config check |
| **MISSING** | Dependency cannot be verified | → Becomes resolution task |
| **PARTIAL** | Some evidence, needs more verification | Specify what's missing |

---

## Tips

- Keep decomposing until actions are primitives (tool + knowledge + access all exist)
- If unsure whether something is primitive, it probably isn't — decompose further
- Every MISSING item becomes a task in your resolution backlog

