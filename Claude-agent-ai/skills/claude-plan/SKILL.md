# /plan - Discovery & Architecture Phase

> **Version**: 1.0.0  
> **Command**: `/plan`  
> **Phase**: Discovery (No Application Coding)

---

## Purpose

Execute the complete discovery and architecture phase. Processes intelligence, maps dependencies, generates Master Project Plot, and produces Senior Developer Pre-Flight Report.

---

## Trigger

User types: `/plan` or `/plan [context/links]`

---

## Execution Workflow

### Step 1: Check State Manifest
```yaml
action: "Read .claude/state_manifest.json"
purpose: "Skip already processed intelligence"
decision:
  - if status="processed": use_cached_metadata
  - if status="pending": proceed_to_step_2
```

### Step 2: Process Intelligence
```yaml
action: "Categorize external intelligence sources"
sources:
  - Instagram reels
  - GitHub repositories
  - Documentation links
  - User-provided context
output: "docs/knowledge_vault/*.md"
```

### Step 3: Extract Skills & Techniques
```yaml
action: "Identify actionable capabilities from intelligence"
extract:
  - Methodology patterns
  - Tool integrations
  - Code techniques
  - Design systems
  - Security patterns
map_to: "Claude skills"
```

### Step 4: Generate Graphify Node Map
```yaml
action: "Map dependencies between components"
generate:
  - .claude/graphify/project_graph.json
  - .claude/graphify/architecture_nodes.md
  - .claude/graphify/node_metadata.json
output: "Mermaid diagram + dependency edges"
```

### Step 5: Configure Ponytail Pipeline
```yaml
action: "Define skill execution sequence"
generate:
  - .claude/ponytail/skill_pipeline.yaml
  - .claude/ponytail/skill_router.json
phases:
  - discovery
  - architecture
  - execution
```

### Step 6: Generate Master Project Plot
```yaml
action: "Create pure engineering architecture document"
file: "docs/project_plot.md"
constraints:
  - NO raw URLs
  - NO social media links
  - Pure engineering architecture only
includes:
  - Executive objective
  - Tech stack
  - Skill execution order
  - Graphify nodes
  - Phase-by-phase milestones
```

### Step 7: Identify Manual Steps
```yaml
action: "Delegate external dependencies to human"
file: "docs/manual_setup_steps.md"
includes:
  - API key generation (exact URLs)
  - MCP server setup (numbered steps)
  - External tool installation
  - GitHub repo cloning
```

### Step 8: Generate Status Report
```yaml
action: "Create Senior Developer Pre-Flight Report"
file: "docs/SENIOR_DEVELOPER_REPORT.md"
includes:
  - Token & context economy
  - Intelligence audit
  - Autonomous actions completed
  - Manual steps required
  - Next steps & recommendations
```

---

## Constraints

### ❌ What NOT to Do in /plan Phase
- Write application code
- Implement features
- Generate UI components
- Deploy anything
- Commit to git (without approval)

### ✅ What to Do in /plan Phase
- Process & categorize intelligence
- Map dependencies
- Generate architecture documents
- Identify required skills
- Delegate manual steps
- Report status

---

## Output Format

```markdown
### 🎯 /plan Phase Complete

**Intelligence Processed**:
- [X] reels/repos/docs categorized into knowledge vault
- Extracted [Y] actionable skills

**Architecture Generated**:
- ✅ Graphify node map ([Z] nodes, [N] edges)
- ✅ Ponytail pipeline configured
- ✅ Master Project Plot: docs/project_plot.md

**Manual Steps Required**:
- [List any API keys, external tools, credentials needed]
- See: docs/manual_setup_steps.md

**Token Optimization**:
- Session: [X]k tokens used
- Future savings: [Y]% via caching

**Status**: ✅ READY FOR /build

**Next Command**: `/build` (after reviewing architecture)
```

---

## Examples

### Example 1: Process Instagram Reels
```
User: /plan
(Attached: 78 Instagram reel links)

Claude executes:
1. ✅ Categorized 78 reels into 5 semantic categories
2. ✅ Extracted 20 skills (token-optimizer, mcp-connector, etc.)
3. ✅ Generated Graphify map (7 nodes, 6 edges)
4. ✅ Created Master Project Plot
5. ✅ Identified manual steps (API keys, MCP servers)

Output: "Architecture complete. Review docs/project_plot.md. Ready for /build."
```

### Example 2: Plan New Feature
```
User: /plan
"Build authentication system with GitHub OAuth + JWT"

Claude executes:
1. ✅ Mapped dependencies (auth → session → database)
2. ✅ Identified required skills (security-auditor, oauth-connector)
3. ✅ Generated architecture plot
4. ✅ Flagged manual steps (GitHub OAuth app registration)

Output: "Architecture ready. Manual step: Register GitHub OAuth app. Then /build."
```

---

## Integration Points

- **State Manifest**: `.claude/state_manifest.json` (check first)
- **Knowledge Vault**: `docs/knowledge_vault/` (output)
- **Graphify**: `.claude/graphify/` (dependency maps)
- **Ponytail**: `.claude/ponytail/` (skill routing)
- **Project Plot**: `docs/project_plot.md` (master architecture)

---

## Success Criteria

- ✅ All intelligence categorized in knowledge vault
- ✅ Graphify nodes mapped with dependencies
- ✅ Ponytail pipeline configured
- ✅ Master Project Plot generated (no raw URLs)
- ✅ Manual steps documented with exact instructions
- ✅ Senior Developer Report produced
- ✅ Token optimization metrics reported
- ✅ User has clear next steps

---

*Command Skill: /plan*  
*Phase: Discovery & Architecture*  
*Next Phase: /build (after approval)*
