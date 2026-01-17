# AI-Assisted RED Prompting Guide

How to use LLMs effectively within the RED methodology.

---

## Core Principle

**LLM generates, human validates.**

RED's verification gates catch hallucinations. Use LLMs for breadth; use human judgment for verification.

---

## Prompting Patterns

### 1. Decomposition Prompt

Use when breaking down an action into sub-actions.

```
I'm applying RED (Recursive Execution Decomposition) to audit this artifact:

[Describe artifact/goal]

Please decompose this into sub-actions. For each action:
1. What is the action?
2. What resources does it touch?
3. What resources does it require?
4. What does it output?
5. Is this a primitive (atomic) or does it need further decomposition?

Format as a table.
```

---

### 2. Primitive Check Prompt

Use to determine if an action is truly primitive.

```
Is this action primitive (atomic and executable)?

Action: [action description]

A primitive must satisfy:
- Tool exists: Is there a specific tool/command/API to do this?
- Knowledge exists: Do we know exactly how to invoke it?
- Access exists: Do we have permissions/credentials?

If any condition is unclear, it's NOT primitive. What sub-actions are needed?
```

---

### 3. Audit Table Generation Prompt

Use to generate initial audit tables.

```
Generate a primitive audit table for these actions:

[List of primitives]

For each primitive, assess:
- Tool exists? (Y/N + what tool)
- Knowledge exists? (Y/N + what knowledge)
- Access exists? (Y/N + what access)

Flag any that are MISSING (cannot be verified).
```

---

### 4. Gap Identification Prompt

Use to find potential missing dependencies.

```
Review this RED decomposition:

[Paste decomposition table]

Identify potential gaps:
1. What implicit assumptions are being made?
2. What dependencies are not explicitly stated?
3. What could fail at execution time that isn't captured?

For each gap, explain why it matters.
```

---

### 5. Mitigation Planning Prompt

Use when a gap is identified.

```
This dependency is MISSING:

[Describe the gap]

Propose 2-3 resolution strategies:
1. What concrete steps would resolve this?
2. What's the fastest path to VERIFIED_HAVE?
3. What's the most robust long-term solution?
```

---

### 6. Plain-Language Explanation Prompt

Use to translate technical findings for non-experts.

```
Explain this RED finding in plain language:

[Technical constraint/assumption/gap]

Explain:
1. What does this mean in simple terms?
2. Why does it matter?
3. What happens if we ignore it?
```

---

## Workflow Example

### Step 1: Scope Lock
Human defines artifact, goal, success criteria.

### Step 2: Initial Decomposition
```
Prompt: "Decompose [goal] into sub-actions using RED methodology..."
LLM: [generates decomposition table]
Human: [reviews, corrects, validates]
```

### Step 3: Iterate Until Primitives
```
For each non-primitive:
  Prompt: "Is [action] primitive? If not, decompose further..."
  LLM: [proposes sub-actions]
  Human: [validates or rejects]
```

### Step 4: Audit Primitives
```
Prompt: "Generate audit table for these primitives..."
LLM: [generates initial audit]
Human: [actually verifies each claim - runs commands, checks access]
```

### Step 5: Identify Gaps
```
Prompt: "What gaps exist in this decomposition?"
LLM: [flags potential issues]
Human: [confirms which are real gaps]
```

### Step 6: Resolution Tasks
```
Prompt: "Propose mitigation for [gap]..."
LLM: [suggests strategies]
Human: [selects and assigns tasks]
```

---

## What LLMs Do Well

| Task | LLM Contribution |
|------|------------------|
| Decomposition | Generate comprehensive sub-action lists |
| Pattern recognition | Spot common failure modes |
| Knowledge recall | Suggest tools/libraries that might exist |
| Translation | Explain technical concepts simply |
| Drafting | Generate table structures quickly |

---

## What Humans Must Do

| Task | Why Human Required |
|------|-------------------|
| Verification | LLMs may hallucinate that tools/access exist |
| Judgment | Prioritization, scoping, "is this useful?" |
| Ground truth | Execute verification commands |
| Registry governance | Decide what counts as primitive |
| Final decision | Accept or reject each status |

---

## Anti-Patterns to Avoid

| Anti-Pattern | Problem | Fix |
|--------------|---------|-----|
| Trusting LLM verification | "It says we have access" isn't verification | Actually run the check |
| Accepting first decomposition | May be incomplete or wrong | Challenge and iterate |
| Skipping human review | Hallucinations slip through | Review every table |
| Over-decomposing | Analysis paralysis | Use primitive registry as stop condition |

---

## Tips

1. **Be specific in prompts** — vague prompts get vague decompositions
2. **Include context** — paste previous tables when iterating
3. **Challenge the LLM** — "What did you miss?" often reveals gaps
4. **Verify immediately** — don't batch verifications; do them as you go
5. **Document evidence** — record what command/check verified each dependency

