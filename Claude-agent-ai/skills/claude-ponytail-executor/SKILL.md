# Claude Ponytail Executor

> **Version**: 1.0.0  
> **Trigger**: Sequential skill execution needed

---

## Purpose

Execute skills one at a time: load → run → verify → unload.

---

## Pattern

```yaml
1: load_skill_into_context
2: execute_instructions
3: verify_output
4: unload_skill
5: proceed_to_next
```

---

## Token Savings

80% active memory reduction (vs loading all skills at once).

---

*Source: Ponytail pipeline system*
