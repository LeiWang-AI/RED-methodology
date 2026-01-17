# Primitive Audit Template

Use this table to audit each leaf primitive in your RED decomposition.

## Instructions

For each primitive action, verify three conditions:
1. **Tool exists** — the capability/library/API is available
2. **Knowledge exists** — you know how to use it
3. **Access exists** — you have permissions/credentials

---

## Audit Table

| Primitive ID | Action | Tool Exists? | Knowledge Exists? | Access Exists? | Overall Status | Evidence / Notes |
|--------------|--------|--------------|-------------------|----------------|----------------|------------------|
| P1 | | ☐ Y ☐ N | ☐ Y ☐ N | ☐ Y ☐ N | | |
| P2 | | ☐ Y ☐ N | ☐ Y ☐ N | ☐ Y ☐ N | | |
| P3 | | ☐ Y ☐ N | ☐ Y ☐ N | ☐ Y ☐ N | | |
| P4 | | ☐ Y ☐ N | ☐ Y ☐ N | ☐ Y ☐ N | | |
| P5 | | ☐ Y ☐ N | ☐ Y ☐ N | ☐ Y ☐ N | | |

---

## Evidence Examples

| Condition | Acceptable Evidence |
|-----------|---------------------|
| **Tool exists** | `pip show library` succeeds, import works, API responds |
| **Knowledge exists** | Documented procedure, team member can demonstrate, tutorial completed |
| **Access exists** | Auth succeeds, permission check passes, config file present |

---

## Status Rules

- All three = Y → **VERIFIED_HAVE**
- Any one = N → **MISSING** (specify which)
- "I think so" / "probably" → Treat as **MISSING** until verified

---

## Resolution Tasks

For each MISSING primitive, create a resolution task:

| Primitive | Missing | Resolution Task | Owner | Due |
|-----------|---------|-----------------|-------|-----|
| | Tool / Knowledge / Access | | | |
| | Tool / Knowledge / Access | | | |

