# Claude MCP Connector

> **Version**: 1.0.0  
> **Trigger**: External data query needed

---

## Purpose

Query MCP servers efficiently without loading full data into context.

---

## MCP Protocol

```yaml
strategy: "On-demand queries"
servers:
  - database (schema metadata only)
  - design-system (UI styles/palettes)
  - external APIs (Pinterest, etc.)
```

---

## Token Savings

- Database: 80-90% vs full schema load
- Design system: Query 50+ styles without bloating context
- APIs: Fetch on-demand, not preload

---

*Source: Knowledge Vault 02_ai_agents_mcp.md*
