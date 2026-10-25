# Claude Token Optimizer

> **Version**: 1.0.0  
> **Category**: Core Infrastructure  
> **Priority**: Critical

---

## Purpose

Implements state manifest checking and prompt caching strategies to achieve 90% token savings via Anthropic's prompt caching system.

---

## Trigger Conditions

- **Automatic**: Before every file read operation
- **Manual**: `/optimize` command
- **Threshold**: When context usage exceeds 80% (160k tokens in 200k window)

---

## Execution Instructions

### Step 1: Check State Manifest First

Before reading ANY file, always check `.claude/state_manifest.json`:

```javascript
// Pseudo-logic
const manifest = read('.claude/state_manifest.json');
const fileStatus = manifest.processing_status[targetFile];

if (fileStatus.status === "processed") {
  // Use cached metadata only
  return fileStatus.metadata;
} else {
  // Full read required
  const content = read(targetFile);
  updateManifest(targetFile, content);
  return content;
}
```

### Step 2: Implement Selective Loading

Never load entire directories. Use metadata queries:

```yaml
# ❌ WRONG
knowledge_vault_content = read_all('docs/knowledge_vault/*')

# ✅ RIGHT
vault_metadata = read('.claude/state_manifest.json').knowledge_vault
if user_needs_specific_category:
  category_content = read('docs/knowledge_vault/01_antigravity_core.md')
```

### Step 3: Context Window Monitoring

Track token usage throughout session:

```yaml
thresholds:
  green_zone: "0-100k tokens (50%) - Normal operation"
  yellow_zone: "100k-160k tokens (80%) - Start pruning"
  red_zone: "160k+ tokens (80%+) - Aggressive compaction"

actions:
  yellow_trigger:
    - Unload inactive skills
    - Clear completed task chains
    - Query vault metadata only
  red_trigger:
    - Emergency compaction
    - Load only critical nodes
    - Defer non-essential operations
```

### Step 4: Report Token Savings

At key milestones, report optimization metrics:

```markdown
**Token Optimization Report**
- Vault read skipped (cached): 39,000 tokens saved
- Graphify 1-hop load: 135,000 tokens saved vs. full codebase
- Session total: 52,000 tokens used (182,000 saved via optimization)
- Caching effectiveness: 92.3%
```

---

## Integration Points

- **State Manifest**: `.claude/state_manifest.json`
- **Token Strategy**: `.claude/token_optimization_strategy.md`
- **Graphify**: Query for 1-hop dependencies only
- **Ponytail**: Sequential skill loading (unload after execution)

---

## Examples

### Example 1: Cached Vault Read

```
User: "What's in the knowledge vault?"

Claude (internal):
1. Check state_manifest.json
2. See knowledge_vault status="processed"
3. Return metadata (500 tokens) instead of full content (39,000 tokens)

Claude (to user):
"Knowledge vault contains 5 categories, 78 Instagram reels processed:
- AntiGravity Core: 10 reels (vibe coding, token optimization)
- AI Agents/MCP: 10 reels (MCP protocol, GitHub workflows)
- Workflow Automation: 6 reels (agent pipelines, spec-driven dev)
- UI/UX Design: 37 reels (design systems, anti-AI-slop patterns)
- Dev Productivity: 15 reels (security audits, free tools)"

Token savings: 38,500 tokens
```

### Example 2: Context Window Alert

```
Claude (internal monitoring):
Current usage: 165,000 tokens (82.5%)
Status: RED ZONE

Actions taken:
- Unloaded completed skills from context
- Switched to metadata-only vault queries
- Deferred non-critical Graphify node loads

Result: Reduced to 95,000 tokens (47.5%)
```

---

## Success Metrics

- ✅ 90%+ token savings on repeat vault access
- ✅ State manifest checked before every file read
- ✅ Context never exceeds 200k limit
- ✅ User sees no degradation in response quality

---

*Extracted from: Knowledge Vault - 01_antigravity_core.md (Reels #6, #12, #15, #19, #27, #57, #60, #74)*
