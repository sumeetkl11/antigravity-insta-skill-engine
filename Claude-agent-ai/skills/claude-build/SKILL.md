# /build - Execution Phase

> **Version**: 1.0.0  
> **Command**: `/build`  
> **Phase**: Execution (Systematic Implementation)

---

## Purpose

Execute approved architecture systematically. Generate code, skills, and implementations based on the Master Project Plot. Uses Graphify for 1-hop loading and Ponytail for sequential skill execution.

---

## Trigger

User types: `/build` (after `/plan` phase completion)

---

## Prerequisites

✅ **Must exist before /build**:
- `docs/project_plot.md` (Master Architecture)
- `.claude/graphify/project_graph.json` (Dependency map)
- `.claude/ponytail/skill_pipeline.yaml` (Execution order)

❌ **Cannot proceed without**:
- Approved architecture from user
- Clear target/scope definition

---

## Execution Workflow

### Step 1: Load Project Plot
```yaml
action: "Read docs/project_plot.md"
purpose: "Understand approved architecture"
verify:
  - Executive objective clear
  - Tech stack defined
  - Skill execution order specified
```

### Step 2: Query Graphify for Target Node
```yaml
action: "Load target module + 1-hop dependencies only"
query: ".claude/graphify/project_graph.json"
strategy: "1-hop-dependencies"
example:
  target: "authentication_module"
  load: ["auth", "database", "session"]
  skip: ["ui", "email", "analytics"]
token_savings: "90% vs full codebase load"
```

### Step 3: Activate Ponytail Skill Sequence
```yaml
action: "Execute skills sequentially (load → run → verify → unload)"
source: ".claude/ponytail/skill_pipeline.yaml"
pattern:
  1: load_skill_into_context
  2: execute_skill_instructions
  3: verify_output
  4: unload_skill_from_context
  5: proceed_to_next_skill
```

### Step 4: Generate Implementation
```yaml
action: "Write code/configs based on architecture"
principles:
  - YAGNI: "Standard library first, no speculation"
  - Minimal: "Concise, modular functions"
  - Concrete: "No abstractions without use cases"
  - Working: "Ship functional code, not frameworks"
```

### Step 5: Run Verification
```yaml
action: "Verify implementation quality"
checks:
  - Syntax validation
  - Security audit (if applicable)
  - Anti-slop check (if UI)
  - Token optimization review
skill: "claude-verification-runner"
```

### Step 6: Update State Manifest
```yaml
action: "Mark completed items as processed"
update: ".claude/state_manifest.json"
enable: "Prompt caching for future sessions"
```

### Step 7: Report Completion
```yaml
action: "Generate build completion report"
includes:
  - Files created/modified
  - Token usage
  - Verification results
  - Next steps (if any)
```

---

## Build Modes

### Mode 1: Generate Skills
```
User: /build
"Generate remaining Claude skills"

Claude executes:
- Load skill templates from knowledge vault
- Generate SKILL.md for each capability
- Create directory structure
- Verify skill format
```

### Mode 2: Implement Feature
```
User: /build
"Implement authentication system"

Claude executes:
- Load architecture from project_plot.md
- Query Graphify for auth dependencies
- Generate auth module + tests
- Run security audit
- Report completion
```

### Mode 3: Generate Configs
```
User: /build
"Setup MCP server configs"

Claude executes:
- Load MCP requirements from manual_setup_steps.md
- Generate .claude/mcp_servers.json template
- Document connection strings needed
- Flag for manual credential entry
```

---

## YAGNI Enforcement

### ❌ What NOT to Build
- Speculative features ("might need later")
- Abstract frameworks without concrete use
- External dependencies when stdlib works
- Over-engineered solutions
- Placeholder code

### ✅ What to Build
- Exact requirements from project_plot.md
- Minimal working implementation
- Standard library solutions first
- Concrete, tested code
- Clear, simple functions

---

## Token Optimization During Build

```yaml
before_each_step:
  - check_context_window_usage
  - if usage > 80%: trigger_compaction
  - unload_inactive_skills

graphify_loading:
  - load_target_node_only
  - load_1_hop_dependencies
  - skip_distant_modules

ponytail_execution:
  - one_skill_active_at_time
  - unload_after_completion
  - clear_inactive_context
```

---

## Output Format

```markdown
### 🔨 /build Phase Complete

**Implementation Summary**:
- Files created: [list with paths]
- Files modified: [list with paths]
- Skills generated: [count]

**Verification Results**:
- ✅ Syntax: Pass
- ✅ Security audit: [Pass/Issues found]
- ✅ Anti-slop check: [Pass/Failed] (if UI)
- ✅ Token optimization: [X]% savings enabled

**Token Usage**:
- Build phase: [X]k tokens
- Savings via Graphify: [Y]k tokens (vs full load)
- Caching enabled: [Z] files

**Status**: ✅ BUILD COMPLETE

**Next Steps**: [Deploy/Test/Review/Manual setup]
```

---

## Examples

### Example 1: Generate Skills
```
User: /build
"Generate remaining 16 Claude skills"

Claude executes:
1. ✅ Loaded skill requirements from knowledge vault
2. ✅ Generated 16 SKILL.md files
3. ✅ Created directory structure
4. ✅ Verified format and completeness

Output:
"Generated 16 skills in skills/ directory:
- claude-context-manager
- claude-vibe-coding-setup
- claude-mcp-connector
(... 13 more)

Total: 20 skills now available.
Token cost: 18k (with caching active)
Status: ✅ COMPLETE"
```

### Example 2: Build Authentication
```
User: /build
"Implement GitHub OAuth authentication"

Claude executes:
1. ✅ Loaded auth architecture from project_plot.md
2. ✅ Graphify 1-hop load: auth + session + database
3. ✅ Generated auth module with bcrypt + JWT
4. ✅ Security audit: Pass (no vulnerabilities)
5. ✅ Flagged manual step: Register GitHub OAuth app

Output:
"Authentication system implemented:
- src/auth/github_oauth.py
- src/auth/jwt_manager.py
- src/auth/session.py

Security audit: ✅ PASS
Manual step: Register OAuth app at github.com/settings/developers

Status: ✅ READY FOR TESTING"
```

---

## Integration Points

- **Project Plot**: `docs/project_plot.md` (source of truth)
- **Graphify**: `.claude/graphify/` (1-hop loading)
- **Ponytail**: `.claude/ponytail/` (skill sequence)
- **State Manifest**: `.claude/state_manifest.json` (update status)
- **Verification**: `claude-verification-runner` skill

---

## Safety Gates

### Before Proceeding
- ⚠️ Project Plot must exist and be approved
- ⚠️ User must confirm scope if ambiguous
- ⚠️ Manual steps must be acknowledged

### During Execution
- 🔴 Block on critical security issues
- 🟡 Warn on missing dependencies
- ⚠️ Alert on external credential needs

### After Completion
- ✅ Run verification suite
- ✅ Report any blockers
- ✅ Update state manifest

---

## Success Criteria

- ✅ Implementation matches project_plot.md
- ✅ All verification checks pass
- ✅ Token optimization maintained (<80% context)
- ✅ YAGNI principles followed
- ✅ Manual steps documented (if any)
- ✅ State manifest updated
- ✅ Clear next steps provided

---

*Command Skill: /build*  
*Phase: Execution*  
*Prerequisite: /plan completion & approval*
