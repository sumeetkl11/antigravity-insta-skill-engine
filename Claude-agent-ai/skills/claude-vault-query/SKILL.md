# Claude Vault Query

> **Version**: 1.0.0  
> **Category**: Knowledge Management  
> **Priority**: High

---

## Purpose

Efficiently query the knowledge vault (78 Instagram reels across 5 categories) using metadata-first approach to minimize token consumption.

---

## Trigger Conditions

- User asks about knowledge vault contents
- Lookup needed for specific topic/category
- Cross-reference intelligence during building

---

## Execution Instructions

### Step 1: Always Start with Metadata

```yaml
priority_order:
  1: Check state_manifest.json first
  2: If cached, return category summaries only
  3: If specific query, load single category file
  4: Never load all 5 files simultaneously
```

### Step 2: Category-Based Queries

```markdown
Query: "What do we know about MCP?"
→ Load: docs/knowledge_vault/02_ai_agents_mcp.md only

Query: "Show me UI/UX patterns"
→ Load: docs/knowledge_vault/04_ui_ux_design.md only

Query: "What's in the vault?"
→ Return: Metadata summary (no full file loads)
```

### Step 3: Skill Extraction Mapping

When user needs a capability, map to source vault:

```yaml
capability_mapping:
  "token_optimization": "01_antigravity_core.md"
  "mcp_integration": "02_ai_agents_mcp.md"
  "workflow_automation": "03_workflow_automation.md"
  "design_systems": "04_ui_ux_design.md"
  "security_audit": "05_dev_productivity.md"
```

---

## Query Response Templates

### Template 1: Full Vault Summary
```markdown
**Knowledge Vault Status**
Total: 78 Instagram reels across 5 categories

1. AntiGravity Core (10 reels)
   - Vibe coding methodology, token optimization, context management
   - Skills: token-optimizer, context-manager, vibe-coding-setup

2. AI Agents/MCP (10 reels)
   - MCP protocol, GitHub workflows, free AI tools
   - Skills: mcp-connector, github-security, design-system-loader

3. Workflow Automation (6 reels)
   - Agent pipelines, spec-driven dev, multi-step workflows
   - Skills: workflow-automator, spec-generator, approval-checkpoint

4. UI/UX Design (37 reels)
   - Design systems, anti-AI-slop, motion graphics, 10 UI styles
   - Skills: design-system, anti-slop-checker, apple-design

5. Dev Productivity (15 reels)
   - Security audits, token tracking, free coding agents
   - Skills: security-auditor, token-tracker, pre-coding-docs

Token cost: ~500 tokens (metadata only)
```

### Template 2: Specific Category Detail
```markdown
**Category: UI/UX Design (37 reels)**

Key Techniques Extracted:
- 10 UI Design Styles (Minimalism, Brutalism, Glassmorphism, etc.)
- Anti-AI-Slop Checklist (remove purple gradients, generic icons)
- Design System MCP (50+ UI styles, 97 color palettes)
- Premium Component Libraries (Colorhunt, Fontjoy, Framer)

Actionable Skills:
- claude-design-system: Access premium UI via MCP
- claude-anti-slop-checker: Validate against generic patterns
- claude-apple-design: Apple/premium brand style generation

External Resources:
- Design tool websites (colorhunt.co, fontjoy.com)
- Animation libraries
- Free hosting platforms

Token cost: ~14,000 tokens (single category load)
```

---

## Integration Points

- **State Manifest**: `.claude/state_manifest.json`
- **Knowledge Vault**: `docs/knowledge_vault/`
- **Graphify Metadata**: `.claude/graphify/node_metadata.json`

---

## Examples

### Example 1: Efficient Lookup
```
User: "Do we have anything on security?"

Claude (internal):
1. Check node_metadata.json
2. See "security_audits" in dev_productivity category
3. Load single file: 05_dev_productivity.md

Response: "Yes, 6 security techniques from Reel #33:
- Pre-deployment security audit checklist
- 6 common vulnerabilities (SQL injection, XSS, exposed keys, etc.)
- Automated security prompts
- React Doctor for code quality

Skill available: claude-security-auditor"

Token cost: ~13,000 tokens (single category)
vs. 71,000 tokens if all categories loaded
Savings: 81.7%
```

### Example 2: Cross-Category Query
```
User: "What free tools can reduce my costs?"

Claude (internal):
1. Query spans multiple categories
2. Load metadata from state_manifest
3. Identify relevant sections:
   - 01_antigravity_core.md (token optimization)
   - 02_ai_agents_mcp.md (free AI tools)
   - 05_dev_productivity.md (free coding agents)

Response: "Free tools across 3 categories:

Token Optimization:
- OmniRoute (237+ AI providers, auto-cheapest)
- Claude Counter (usage tracking)
- Caveman (output compression)

AI Tools:
- Google Stitch (design to code)
- Opal (free automation)
- Ollama (local models)

Alternative Agents:
- MiMo Code, ZCode, Qwen Code, Kimi Code (all free)

Estimated savings: 80-90% cost reduction"

Token cost: ~30,000 tokens (3 categories)
```

---

## Success Metrics

- ✅ Metadata queries cost <1,000 tokens
- ✅ Single category queries cost <15,000 tokens  
- ✅ Never load all 5 categories simultaneously
- ✅ User gets accurate, relevant results

---

*Extracted from: All 5 Knowledge Vault Categories*
