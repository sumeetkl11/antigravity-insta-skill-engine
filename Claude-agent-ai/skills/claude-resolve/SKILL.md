# /resolve - Manual Intelligence Synchronization

> **Version**: 1.0.0  
> **Command**: `/resolve`  
> **Purpose**: Merge user-provided context for blocked/unresolved links

---

## Purpose

Fast metadata merge for intelligence that couldn't be accessed automatically (Instagram login walls, 403 errors, missing context). User provides captions/notes, Claude integrates into knowledge vault.

---

## Trigger

User types: `/resolve` when `unresolved_links.md` exists or when adding manual context

---

## Workflow

### Step 1: Load Unresolved Items
```yaml
file: "docs/knowledge_vault/unresolved_links.md"
if_not_exists: "No unresolved items, exit gracefully"
```

### Step 2: Request User Context
```yaml
prompt: "Please provide context for these blocked items:
[List items from unresolved_links.md]

For each, provide:
- Brief description or caption
- Category (Core/MCP/Workflow/UI/Tools)
- Any actionable techniques"
```

### Step 3: Categorize & Merge
```yaml
action: "Integrate user-provided context into appropriate vault file"
update:
  - docs/knowledge_vault/01_antigravity_core.md (if applicable)
  - docs/knowledge_vault/02_ai_agents_mcp.md (if applicable)
  - docs/knowledge_vault/03_workflow_automation.md (if applicable)
  - docs/knowledge_vault/04_ui_ux_design.md (if applicable)
  - docs/knowledge_vault/05_dev_productivity.md (if applicable)
```

### Step 4: Update State Manifest
```yaml
action: "Mark resolved items as processed"
update: ".claude/state_manifest.json"
remove_from: "unresolved_links.md"
```

### Step 5: Update Project Plot (if needed)
```yaml
if_new_intelligence_affects_architecture:
  update: "docs/project_plot.md"
else:
  skip: "Architecture unchanged"
```

---

## Examples

### Example 1: Instagram Login Wall
```
unresolved_links.md contains:
"Instagram Reel #42 - Blocked by login wall"

User provides:
"It's about MCP server setup for Notion integration"

Claude executes:
1. ✅ Categorized to: 02_ai_agents_mcp.md
2. ✅ Added entry with user-provided context
3. ✅ Updated state manifest
4. ✅ Removed from unresolved_links.md

Output: "Resolved 1 item. Knowledge vault updated."
```

---

## Output Format

```markdown
### 🔄 /resolve Complete

**Items Resolved**: [X]
**Categories Updated**:
- [Category 1]: [Y] items added
- [Category 2]: [Z] items added

**State Manifest**: Updated
**Unresolved Remaining**: [N]

**Status**: ✅ RESOLVED
```

---

*Command Skill: /resolve*  
*Purpose: Merge manual intelligence*
