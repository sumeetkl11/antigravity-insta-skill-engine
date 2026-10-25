# /ask - Technical Explainer (Read-Only Mode)

> **Version**: 1.0.0  
> **Command**: `/ask [question]`  
> **Mode**: Read-Only (No State Changes)

---

## Purpose

Answer technical questions, explain architectural decisions, review code logic, or clarify implementation details **without** editing files or altering project state.

---

## Trigger

User types: `/ask [question]`

Examples:
- `/ask How does Graphify 1-hop loading work?`
- `/ask Why use Ponytail sequential execution?`
- `/ask What's the difference between /plan and /build?`

---

## Constraints

### ✅ Allowed Actions
- Read files
- Query knowledge vault
- Explain architecture
- Review code logic
- Clarify methodologies
- Provide examples
- Compare approaches

### ❌ Forbidden Actions
- Write or edit files
- Modify state manifest
- Generate new code
- Execute builds
- Update configurations
- Commit to git

---

## Execution Workflow

### Step 1: Parse Question
```yaml
action: "Understand user's technical question"
categories:
  - architecture_explanation
  - methodology_clarification
  - code_review
  - comparison_request
  - troubleshooting_advice
```

### Step 2: Query Relevant Sources
```yaml
sources:
  - docs/project_plot.md (architecture)
  - docs/knowledge_vault/*.md (intelligence)
  - .claude/graphify/ (dependencies)
  - .claude/ponytail/ (execution)
  - skills/*.md (capability docs)
strategy: "Metadata first, full content only if needed"
```

### Step 3: Provide Clear Explanation
```yaml
format:
  - Direct answer first
  - Supporting details
  - Examples if helpful
  - References to docs
tone: "Technical but accessible"
```

### Step 4: Suggest Next Steps (if applicable)
```yaml
if question_leads_to_action:
  suggest: "Use /plan or /build for implementation"
else:
  close: "Question answered, no action needed"
```

---

## Question Types & Responses

### Type 1: Architecture Questions
```
User: /ask How does token optimization work?

Claude response:
"Token optimization uses 3 strategies:

1. **Prompt Caching** (90% savings)
   - Static definitions stay at prompt prefix
   - Anthropic caches repeated context
   - See: .claude/token_optimization_strategy.md

2. **Graphify 1-Hop Loading** (90% vs full codebase)
   - Load target node + immediate dependencies only
   - Skip distant modules
   - See: .claude/graphify/architecture_nodes.md

3. **Ponytail Sequential Execution** (80% active memory)
   - Load one skill at a time
   - Execute → Verify → Unload
   - See: .claude/ponytail/skill_pipeline.yaml

Combined result: 96.3% token savings per session after initial setup.

Reference: docs/SENIOR_DEVELOPER_REPORT.md Section 1"
```

### Type 2: Methodology Questions
```
User: /ask What's YAGNI in Ponytail?

Claude response:
"YAGNI = 'You Aren't Gonna Need It'

Ponytail enforces YAGNI during /build:
- Standard library FIRST (no external deps without reason)
- Concise functions (no sprawling abstractions)
- Concrete solutions (no speculative features)
- Working code (ship functionality, not frameworks)

Example:
❌ Install library for single function
✅ Use Python's built-in datetime

Prevents token bloat + reduces dependencies.

Reference: .claude/ponytail/skill_pipeline.yaml → optimization_rules"
```

### Type 3: Comparison Questions
```
User: /ask Difference between /plan and /build?

Claude response:
"/plan (Discovery Phase):
- Process intelligence
- Map dependencies
- Generate architecture docs
- ❌ NO code generation

/build (Execution Phase):
- Generate implementation
- Execute approved architecture
- Create code/configs
- ✅ Code generation

Flow: /plan → [user reviews] → /build

See: skills/claude-plan/SKILL.md and skills/claude-build/SKILL.md"
```

### Type 4: Code Review Questions
```
User: /ask Review this authentication code
[code snippet]

Claude response:
"Code review:

✅ Strengths:
- Uses bcrypt for password hashing
- Parameterized SQL queries (no injection risk)
- Session expiration configured

⚠️ Improvements:
1. Add rate limiting (prevent brute force)
2. Consider 2FA for admin accounts
3. HTTPS enforcement check missing

Security: MEDIUM RISK (not blocking but improve before prod)

Recommendation: Run claude-security-auditor skill for full audit."
```

---

## Response Format

```markdown
[Direct answer to question]

[Supporting details with examples]

[References to relevant docs/skills]

[Next steps if action needed, otherwise "Question answered"]
```

---

## Examples

### Example 1: Architecture Question
```
User: /ask Why separate .claude/ from .antigravity/?

Claude: "Separation prevents conflicts:
- .claude/ = Claude workspace system
- .antigravity/ = AntiGravity system
- Both can coexist independently

Design principle: Complementary, not competing systems.

Reference: .claude/README.md Section 1"
```

### Example 2: Troubleshooting Question
```
User: /ask Why is context window at 85%?

Claude: "High context usage detected.

Likely causes:
1. Full vault loaded (should be metadata only)
2. Multiple skills active (Ponytail should unload)
3. Large files in context

Solutions:
- Run claude-token-optimizer skill
- Check state manifest for cached items
- Trigger Ponytail unload sequence

Status: YELLOW ZONE (action recommended)

Reference: .claude/token_optimization_strategy.md Section 5"
```

### Example 3: Methodology Question
```
User: /ask What's vibe coding?

Claude: "Vibe coding methodology (from knowledge vault):

Pre-code structure: Create 7 files BEFORE coding
1. PRD.md (requirements)
2. DESIGN.md (visual specs)
3. ARCHITECTURE.md (system design)
4. DATABASE.md (schema)
5. API.md (endpoints)
6. AGENTS.md (AI behavior)
7. README.md (overview)

Why: Prevents AI hallucination by providing concrete constraints.

Source: docs/knowledge_vault/01_antigravity_core.md Reel #1

Available skill: claude-vibe-coding-setup (generates these files)"
```

---

## Integration Points

- **Knowledge Vault**: `docs/knowledge_vault/` (query intelligence)
- **Project Plot**: `docs/project_plot.md` (architecture reference)
- **Skills**: `skills/*/SKILL.md` (capability docs)
- **Graphify**: `.claude/graphify/` (dependency info)
- **Token Strategy**: `.claude/token_optimization_strategy.md`

---

## Success Criteria

- ✅ Question answered clearly and accurately
- ✅ References provided to relevant docs
- ✅ Examples given when helpful
- ✅ No files modified (read-only mode)
- ✅ Next steps suggested if action needed

---

*Command Skill: /ask*  
*Mode: Read-Only Technical Explainer*  
*Use for: Questions, clarifications, reviews (no state changes)*
