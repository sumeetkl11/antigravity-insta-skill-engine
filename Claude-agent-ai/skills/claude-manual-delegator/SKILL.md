# Claude Manual Delegator

> **Version**: 1.0.0  
> **Trigger**: External dependencies identified

---

## Purpose

Create step-by-step guide for tasks requiring human action.

---

## Delegates

- API key generation (exact URLs)
- MCP server setup (numbered steps)
- External tool installation
- GitHub repo cloning
- OAuth registrations

---

## Format

```markdown
### Task: [Name]
1. Visit: [exact URL]
2. Click: [specific button]
3. Copy: [what to copy]
4. Paste into: [exact file/variable]
```

---

*Output: docs/manual_setup_steps.md*
