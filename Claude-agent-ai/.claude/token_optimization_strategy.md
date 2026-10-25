# Token Conservation & Context Optimization Strategy

> **Goal**: Minimize token consumption while maximizing Claude Code effectiveness  
> **Target Savings**: 90% via Anthropic Prompt Caching

---

## 1. Anthropic Prompt Caching Architecture

### How It Works
- Static architectural instructions stay at prompt prefix
- Repeated reads trigger 90% token discount
- Cache persists for 5 minutes of inactivity

### What to Cache
✅ Category schemas (AntiGravity Core, MCP, UI/UX, etc.)  
✅ Graphify node definitions  
✅ Ponytail skill execution rules  
✅ Knowledge vault structure  
❌ Dynamic conversation context  
❌ User-specific requests  
❌ Real-time state changes

---

## 2. State Manifest First Pattern

**Rule**: Before reading ANY file, check `.claude/state_manifest.json`

```javascript
// Pseudo-logic
if (manifest.processing_status[file].status === "processed") {
  skip_read();
  use_cached_metadata();
} else {
  read_file();
  update_manifest();
}
```

**Savings**: Prevents re-reading 78 Instagram reels on every session

---

## 3. Graphify 1-Hop Dependency Loading

**Anti-Pattern**: Load entire codebase into context  
**Claude Pattern**: Query `project_graph.json` → Load target node + immediate dependencies only

```json
{
  "target": "auth_module",
  "load": ["auth_module", "database", "session_manager"],
  "skip": ["ui_components", "email_service", "analytics"]
}
```

**Savings**: 70-80% reduction in context window usage per build step

---

## 4. Ponytail Minimal Skill Activation

### Sequential Execution Pattern
1. Load active skill → Execute → Verify → **Unload from context**
2. Next skill loads only after previous completes
3. Never hold multiple skill definitions in memory simultaneously

### YAGNI Enforcement
- Standard library > External dependencies
- Concise functions > Sprawling abstractions
- Ship working code > Speculative features

---

## 5. Context Window Monitoring

### Thresholds (200k Context Window)
- **Green Zone**: 0-100k tokens (50%) - Normal operation
- **Yellow Zone**: 100k-160k tokens (80%) - Start pruning
- **Red Zone**: 160k-200k tokens (80%+) - Aggressive compaction

### Compaction Triggers
- Completed task chains unload from context
- Vault queries return metadata only (full content on-demand)
- Graphify nodes expire after 10 minutes of inactivity

---

## 6. Real-World Token Savings Examples

### Example 1: Instagram Reel Processing
- **Without optimization**: 78 reels × 500 tokens = 39,000 tokens per session
- **With state manifest**: First session 39k, subsequent sessions ~100 tokens (metadata only)
- **Savings**: 99.7% on repeat sessions

### Example 2: Graphify Node Loading
- **Full codebase load**: 150k tokens
- **1-hop dependency load**: 15k tokens
- **Savings**: 90%

### Example 3: Ponytail Skill Chain (5 skills)
- **All-at-once load**: 5 × 3k = 15k tokens
- **Sequential load-execute-unload**: 1 × 3k = 3k tokens active
- **Savings**: 80%

---

## 7. Monitoring & Alerts

Claude should self-report token usage at key milestones:
- After vault ingestion: "Processed 78 reels, cached 39k tokens"
- During Graphify load: "Loaded auth_module + 2 dependencies (4.2k tokens)"
- End of session: "Total session: 52k tokens (135k saved via caching)"

---

*Optimized for Anthropic Claude Sonnet 4/4.5 with 200k-1M context windows*
