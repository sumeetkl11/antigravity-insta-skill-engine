# Category 2: AI Coding Agents, MCP Servers & GitHub Repositories

> **Reels Count**: 10  
> **Focus**: Model Context Protocol, agent integrations, GitHub workflows, free AI tools

---

## Skills & Techniques Extracted

### 1. **Google Free AI Tools Suite** (Reel #3)
- **Source**: https://www.instagram.com/nick_saraev/reel/DbOUP9OPDAQ/
- **Tools Identified**:
  - **Google Stitch**: Design prompt → HTML/React code conversion
  - **Opal**: Free AI pipeline automation (n8n alternative)
  - **Pomelli**: (Context suggests AI workflow tool)
- **Application**: Design-to-code automation, no-code AI pipelines
- **Cost**: Free alternatives to paid services

### 2. **Model Context Protocol (MCP) Integration** (Reels #4, #10, #13, #18, #38, #45, #47)
- **7 Reels on MCP**: Deep integration pattern
- **Core Concept**: Context window + token conservation protocol
- **How It Works**:
  - Agent queries MCP server on-demand (not holding full repo in memory)
  - Connects to databases, external tools, APIs via standardized interface
  - Reduces token consumption by 80-90%
- **Claude Desktop Implementation**: Already supports MCP servers natively
- **Applications**:
  - Database queries without loading full schema
  - File system access without reading all files
  - External API calls (Pinterest, design systems, motion graphics)
  - Context preservation across AI tools (CapsuleHub example)

### 3. **GitHub Developer Workflows** (Reels #5, #70)
- **Source**: https://www.instagram.com/chowdhury_duo/reel/DcKv7gNgh4x/
- **Key Techniques**:
  - Security settings (6 free GitHub configurations)
  - Repository best practices
  - CI/CD integration patterns
- **Application**: Automated workflows, security hardening

### 4. **Claude Code Local + MCP** (Reel #10, #13)
- **Source**: https://www.instagram.com/onlytech.peter/reel/DWJiyeGE45c/
- **Setup**: Claude Code + Ollama (local models) + MCP servers
- **Benefits**:
  - No API costs
  - Offline capability
  - Full privacy
  - Still get slash commands, sub-agents, plan mode
- **Technical**: Terminal commands for MCP server setup

### 5. **CapsuleHub Context Persistence** (Reel #18)
- **Source**: https://www.instagram.com/wdf_ai/reel/DXy6Dn_TWSR/
- **Problem Solved**: Context resets when switching AI tools
- **Solution**: Capture conversation → Drop into any AI → Continue exactly where left off
- **Supported**: Claude, ChatGPT, Gemini, Perplexity, DeepSeek, Gmail, coding agents via MCP
- **Claude Application**: MCP connector for cross-session context

### 6. **Design System MCP Integration** (Reel #38)
- **Source**: https://www.instagram.com/10xoperator/reel/DayIBJ1M430/
- **Problem**: AI-generated sites look generic
- **Solution**: MCP server with:
  - 50+ premium UI styles
  - 97 curated color palettes
  - Premium font combinations
  - Modern UI component library
- **Result**: Claude generates distinctive, non-generic designs

### 7. **Motion Design via MCP** (Reel #47)
- **Source**: https://www.instagram.com/worldof.aix/reel/DbF9lUOMtU3/
- **Workflow**: Claude Code + Pinterest API (via MCP) + Higgsfield MCP
- **Capability**: Motion design generation inside AI workflow
- **Application**: Video generation, animation, motion graphics

---

## Actionable Intelligence

### MCP Server Architecture Pattern
```yaml
mcp_integration:
  purpose: "On-demand data access without context bloat"
  implementation:
    - configure: ".claude/mcp_servers.json"
    - query: "mcp://database/schema" (metadata only)
    - fetch: "mcp://api/endpoint" (on-demand)
  token_savings: "80-90%"
```

### Free AI Infrastructure Stack
```markdown
1. **Models**: Ollama (local) + OpenRouter (free tier)
2. **Automation**: Opal (free n8n alternative)
3. **Design-to-Code**: Google Stitch
4. **Context Persistence**: CapsuleHub
5. **MCP Servers**: Pinterest, Higgsfield, Design Systems
```

### GitHub Security Hardening (6 Free Settings)
```markdown
□ Enable Dependabot security alerts
□ Enable secret scanning
□ Configure branch protection rules
□ Enable required reviews for PRs
□ Enable signed commits requirement
□ Configure code scanning (CodeQL)
```

---

## Integration with Claude Skills

These concepts map to:
- **claude-mcp-connector** (skill) - Query MCP servers efficiently
- **claude-github-security** (skill) - Automated security configuration
- **claude-design-system-loader** (skill) - Access premium UI via MCP
- **claude-context-capsule** (skill) - Cross-session context preservation

---

## External Dependencies (Human Setup Required)

See `docs/manual_setup_steps.md` for:
- MCP server configuration (database, API connections)
- GitHub PAT (Personal Access Token) generation
- Ollama installation (for local models)
- CapsuleHub account setup

---

*Processed: 2026-10-25*  
*Status: Ready for Graphify node mapping*
