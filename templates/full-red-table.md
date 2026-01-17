# Full RED Analysis Template

A complete template for conducting a RED analysis on any artifact.

---

## Step A: Scope Lock

| Field | Your Input |
|-------|------------|
| **Artifact** | [What are you analyzing?] |
| **Goal/Claim** | [What should this artifact achieve?] |
| **Success Criteria** | [How do you know it worked?] |
| **Out of Scope** | [What are you NOT analyzing?] |

---

## Step B: Decomposition Table

| ID | Parent | Action | Resources Touched | Resources Required | Outputs | Primitive? | Status |
|----|--------|--------|-------------------|-------------------|---------|------------|--------|
| 1 | — | [Top-level goal] | | | | N | |
| 1.1 | 1 | | | | | | |
| 1.2 | 1 | | | | | | |
| 1.3 | 1 | | | | | | |
| 2 | 1.1 | | | | | | |
| ... | ... | | | | | | |

---

## Step C: Primitive Audit

For each primitive (Primitive? = Y), complete this audit:

| Primitive ID | Action | Tool Exists? | Evidence | Knowledge Exists? | Evidence | Access Exists? | Evidence | Overall |
|--------------|--------|--------------|----------|-------------------|----------|----------------|----------|---------|
| | | Y/N | | Y/N | | Y/N | | |
| | | Y/N | | Y/N | | Y/N | | |
| | | Y/N | | Y/N | | Y/N | | |

---

## Step D: Design vs Current-State

| Dependency | Design Requires | Current State | Status | Resolution |
|------------|-----------------|---------------|--------|------------|
| | | | VERIFIED_HAVE / MISSING | |
| | | | VERIFIED_HAVE / MISSING | |
| | | | VERIFIED_HAVE / MISSING | |

---

## Step E: Missing Fundamentals Backlog

| ID | Missing Dependency | Type | Resolution Task | Owner | Priority | Due |
|----|-------------------|------|-----------------|-------|----------|-----|
| M1 | | Tool / Knowledge / Access | | | | |
| M2 | | Tool / Knowledge / Access | | | | |
| M3 | | Tool / Knowledge / Access | | | | |

---

## Summary

| Metric | Count |
|--------|-------|
| Total actions | |
| Primitives | |
| VERIFIED_HAVE | |
| MISSING | |
| Resolution tasks generated | |

---

## Notes

[Any observations, patterns, or insights from the analysis]

