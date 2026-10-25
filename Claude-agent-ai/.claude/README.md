# Claude Autonomous Workspace System

> **Version**: 1.0.0  
> **Created**: 2026-10-25  
> **Purpose**: Token-efficient autonomous agent orchestration for Claude Code

---

## Directory Structure

```
.claude/
├── README.md                           # This file
├── state_manifest.json                 # Processing state & prompt cache metadata
├── token_optimization_strategy.md      # Context window management rules
├── graphify/                           # Dependency node mapping system
│   ├── project_graph.json             # Module dependency graph
│   ├── architecture_nodes.md          # Mermaid diagrams & node index
│   └── node_metadata.json             # Extended node properties
└── ponytail/                          # Sequential skill execution pipeline
    ├── skill_pipeline.yaml            # Execution order & token rules
    ├── skill_router.json              # Conditional skill activation
    └── execution_log_template.md      # Standardized execution logs
```

---

## Core Principles

### 1. **Separation from AntiGravity**
- Claude infrastructure lives in `.claude/` - AntiGravity uses `.antigravity/`
- Zero file overlap, independent state management
- Complementary systems, not competing ones

### 2. **Token Conservation (90% Savings via Prompt Caching)**
- State manifest prevents re-processing
- Graphify loads only 1-hop dependencies
- Ponytail executes minimal skill chains
- YAGNI: Standard library first, no speculative code

### 3. **Autonomous vs. Manual Delegation**
- **Claude Does**: File scaffolding, code generation, architecture design
- **Human Required**: API keys, credentials, OAuth, production deployment

---

## Integration with Claude Code

This workspace system enhances Claude Code's native capabilities:
- **Skills Directory**: Custom skills stored in `skills/claude-*`
- **Knowledge Vault**: Reference intelligence in `docs/knowledge_vault/`
- **Project Plot**: Master architecture at `docs/project_plot.md`
- **Manual Steps**: Human-required tasks in `docs/manual_setup_steps.md`

---

## Command Triggers

- `/plan` - Discovery & architecture phase (no coding)
- `/resolve` - Merge manual intelligence into vault
- `/build` - Execute approved architecture
- `/ask` - Read-only technical explainer

---

*Built for Claude Code. Optimized for 200k-1M context windows.*
