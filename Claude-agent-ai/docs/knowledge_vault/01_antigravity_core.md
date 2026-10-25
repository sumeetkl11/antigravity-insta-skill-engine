# Category 1: AntiGravity Core, System Prompts & Vibe Coding

> **Reels Count**: 10  
> **Focus**: Vibe coding methodology, system prompts, context window management, LLM optimization

---

## Skills & Techniques Extracted

### 1. **Vibe Coding Methodology** (Reel #1)
- **Source**: https://www.instagram.com/avani.codes/reel/DemISY8uSlU/
- **Core Technique**: Pre-code structural file creation
- **Files Required Before Coding**:
  1. `PRD.md` - Product Requirements Document
  2. `DESIGN.md` - Visual/UX specifications
  3. `ARCHITECTURE.md` - System design
  4. `DATABASE.md` - Schema & data models
  5. `API.md` - Endpoint specifications
  6. `AGENTS.md` - AI agent behavior rules
  7. `README.md` - Project overview
- **Why It Works**: Prevents AI hallucination by providing concrete constraints
- **Application**: Create these 7 files BEFORE any coding begins

### 2. **GSD (Get Sh*t Done) Loop** (Reel #2)
- **Source**: https://www.instagram.com/code.banger/reel/De3XTLeRycA/
- **Plugin**: AntiGravity "Get Sh*t Done"
- **Workflow**: Plan → Build → Test → Launch
- **Purpose**: Breaks large tasks into atomic, verifiable steps
- **Integration Point**: Can be adapted as Claude skill for task decomposition

### 3. **Ralph Loop** (Reel #2)
- **Source**: Same as #2
- **Plugin**: AntiGravity "Ralph Loop"
- **Capability**: Autonomous decision-making without repeated prompts
- **Technique**: AI self-determines next steps based on context
- **Claude Equivalent**: Agent tool with subagent delegation

### 4. **CodeRabbit Integration** (Reel #2)
- **Source**: Same as #2
- **Plugin**: CodeRabbit
- **Purpose**: Automated bug detection & code review
- **Application**: Pre-commit hooks, CI/CD integration

### 5. **Context Window Conservation** (Reels #6, #12, #15, #19, #27, #57, #60, #74)
- **Multiple Sources**: 8 reels on token optimization
- **Key Techniques**:
  - **State Caching**: Store processed content, reference metadata only
  - **Prompt Modularization**: Break large contexts into focused segments
  - **Rate Limit Bypass**: Distribute requests across model instances
  - **Free Token Access**: OpenRouter, Gemini Flash (1B tokens), HTML-based multi-model interfaces
- **Claude Application**: 
  - State manifest pattern (already implemented in `.claude/state_manifest.json`)
  - Graphify 1-hop loading
  - Ponytail sequential skill execution

---

## Actionable Intelligence

### Token Optimization Pattern
```yaml
strategy: "90% token savings via prompt caching"
techniques:
  - Check state manifest before every file read
  - Cache static architectural definitions
  - Load dependencies on-demand (1-hop only)
  - Unload inactive skills from context
```

### Vibe Coding Checklist
```markdown
Before starting ANY AI coding project:
□ Create PRD.md (what we're building)
□ Create DESIGN.md (how it looks/feels)
□ Create ARCHITECTURE.md (system structure)
□ Create DATABASE.md (data models)
□ Create API.md (endpoints/contracts)
□ Create AGENTS.md (AI behavior rules)
□ Create README.md (project overview)
```

### Free Token Resources
- **OpenRouter**: Free tier aggregation across 50+ models
- **Gemini Flash**: 1 billion tokens free
- **OpenAI Test Tokens**: 250k/day for latest models (data used for training)
- **HTML Multi-Model Interface**: Single file, no login, runs locally

---

## Integration with Claude Skills

These concepts map to:
- **claude-token-optimizer** (skill) - Implements state manifest + caching
- **claude-context-manager** (skill) - Monitors usage, triggers compaction
- **claude-vibe-coding-setup** (skill) - Generates 7 pre-code files
- **claude-autonomous-loop** (skill) - Ralph Loop equivalent

---

*Processed: 2026-10-25*  
*Status: Ready for Graphify node mapping*
