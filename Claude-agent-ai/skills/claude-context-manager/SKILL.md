# Claude Context Manager

> **Version**: 1.0.0  
> **Trigger**: Automatic (monitors context usage)

---

## Purpose

Monitor context window usage and trigger compaction when thresholds exceeded.

---

## Thresholds

- **Green**: 0-100k tokens (normal)
- **Yellow**: 100k-160k tokens (start pruning)
- **Red**: 160k+ tokens (aggressive compaction)

---

## Actions

### Yellow Zone
- Unload inactive skills
- Clear completed task chains
- Query vault metadata only

### Red Zone
- Emergency compaction
- Load only critical nodes
- Defer non-essential ops

---

*Auto-runs during session*
