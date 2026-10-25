# Claude Verification Runner

> **Version**: 1.0.0  
> **Trigger**: After code generation in /build

---

## Purpose

Verify implementation quality before presenting to user.

---

## Checks

- ✅ Syntax validation
- ✅ Security audit (if applicable)
- ✅ Anti-slop check (if UI)
- ✅ Token optimization review

---

## Actions

- **Pass**: Present to user
- **Fail**: Fix issues before presenting

---

*Runs automatically in /build phase*
