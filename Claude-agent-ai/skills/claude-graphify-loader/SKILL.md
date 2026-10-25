# Claude Graphify Loader

> **Version**: 1.0.0  
> **Trigger**: Dependency mapping or 1-hop node loading

---

## Purpose

Load target module + immediate dependencies only (1-hop), skip distant modules.

---

## Strategy

```yaml
query: "project_graph.json"
load:
  target: "auth_module"
  dependencies: ["database", "session"]
  skip: ["ui", "email", "analytics"]
savings: "90% vs full codebase"
```

---

## Integration

Used automatically during `/build` phase via Ponytail.

---

*Source: Graphify architecture system*
