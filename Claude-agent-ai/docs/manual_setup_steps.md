# Manual Setup Steps Guide

> **Purpose**: Human-required tasks for external dependencies, API keys, and credentials  
> **Last Updated**: 2026-10-25T09:32:57.879Z

---

## 🔴 Tasks Requiring Human Action

Claude **cannot** perform these tasks automatically. Follow the numbered steps below to complete your setup.

---

## 1. API Key Generation

### 1.1 Anthropic API Key (Claude)

**Required for**: Claude API access, production deployments

**Steps**:
1. Visit: https://console.anthropic.com/
2. Sign in or create account
3. Navigate to: **Settings** → **API Keys**
4. Click: **Create Key**
5. Copy the key (starts with `sk-ant-`)
6. Paste into `.env` file:
   ```bash
   ANTHROPIC_API_KEY=sk-ant-your-key-here
   ```

**Cost**: Pay-as-you-go ($3/M input tokens, $15/M output tokens for Sonnet 4)

---

### 1.2 OpenAI API Key (Optional)

**Required for**: GPT model access, alternative to Claude

**Steps**:
1. Visit: https://platform.openai.com/api-keys
2. Sign in or create account
3. Click: **Create new secret key**
4. Copy the key (starts with `sk-proj-` or `sk-`)
5. Paste into `.env` file:
   ```bash
   OPENAI_API_KEY=sk-your-key-here
   ```

**Free Alternative**: Use OpenRouter free tier (see Section 3.1)

---

### 1.3 GitHub Personal Access Token

**Required for**: Private repo access, GitHub API operations

**Steps**:
1. Visit: https://github.com/settings/tokens
2. Click: **Generate new token** → **Generate new token (classic)**
3. Set name: "Claude Code Workspace"
4. Select scopes:
   - ☑️ `repo` (Full repository access)
   - ☑️ `workflow` (Update GitHub Actions)
   - ☑️ `read:org` (Read org data)
5. Click: **Generate token**
6. Copy token (starts with `ghp_`)
7. Paste into `.env` file:
   ```bash
   GITHUB_TOKEN=ghp_your_token_here
   ```

---

## 2. MCP Server Configuration

### 2.1 Database MCP Server (If Using Databases)

**Required for**: On-demand database queries without loading full schema

**Steps**:
1. Open: `.claude/mcp_servers.json` (create if doesn't exist)
2. Add configuration:
   ```json
   {
     "mcpServers": {
       "database": {
         "command": "npx",
         "args": ["-y", "@anthropic-ai/mcp-server-postgres"],
         "env": {
           "DATABASE_URL": "postgresql://user:password@localhost:5432/dbname"
         }
       }
     }
   }
   ```
3. Replace `DATABASE_URL` with your actual connection string
4. Restart Claude Code

**Alternative Databases**:
- MySQL: Use `@anthropic-ai/mcp-server-mysql`
- SQLite: Use `@anthropic-ai/mcp-server-sqlite`

---

### 2.2 Design System MCP Server

**Required for**: Premium UI styles, color palettes, font combinations

**Steps**:
1. Clone the design system repo (when available):
   ```bash
   # URL to be provided by community/user
   git clone [design-system-mcp-repo-url]
   cd design-system-mcp
   npm install
   ```
2. Add to `.claude/mcp_servers.json`:
   ```json
   {
     "mcpServers": {
       "design-system": {
         "command": "node",
         "args": ["path/to/design-system-mcp/index.js"]
       }
     }
   }
   ```
3. Restart Claude Code

**Resources**: See Knowledge Vault - 04_ui_ux_design.md for MCP design system references

---

## 3. Free Tool Installation

### 3.1 OmniRoute (Token Optimization)

**Purpose**: Route queries to cheapest AI provider (237+ models)

**Steps**:
1. Visit: https://omniroute.ai/ (or search for latest URL)
2. Create free account
3. Copy API key from dashboard
4. Paste into `.env`:
   ```bash
   OMNIROUTE_API_KEY=your_key_here
   ```
5. Configure routing in your code:
   ```python
   from omniroute import Router
   router = Router(api_key=os.getenv("OMNIROUTE_API_KEY"))
   ```

**Savings**: 80% token cost reduction via automatic model selection

---

### 3.2 Claude Counter (Usage Tracking)

**Purpose**: Track daily/weekly Claude usage to avoid limit surprises

**Steps**:
1. Search: "Claude Counter extension" or check Chrome Web Store
2. Install browser extension
3. Sign in to Claude.ai with extension active
4. Dashboard shows: daily usage, weekly limits, token breakdown

**No API key required** - works via browser extension

---

### 3.3 Caveman (Output Compression)

**Purpose**: Compress Claude's output tokens (same quality, less context)

**Steps**:
1. Search: "Caveman Claude compression" for latest tool
2. Follow tool-specific installation instructions
3. Typical setup:
   ```bash
   npm install -g caveman-compressor
   caveman --config claude
   ```

**Savings**: ~20-30% output token reduction

---

### 3.4 Ollama (Local Models - Free Alternative)

**Purpose**: Run Claude Code with local models (zero API costs)

**Steps**:
1. Visit: https://ollama.ai/download
2. Download for your OS (Windows/Mac/Linux)
3. Install Ollama
4. Pull a model:
   ```bash
   ollama pull llama3.2
   # or
   ollama pull qwen2.5-coder
   ```
5. Configure Claude Code to use Ollama:
   ```bash
   claude code --model ollama/llama3.2
   ```

**Benefits**: Free, private, offline capability

---

## 4. External Repository Cloning

### 4.1 8-Hour Startup Repository (150+ AI Skills)

**Purpose**: Production-grade skill templates, specialized agents

**Steps**:
1. Search GitHub: "8 hour startup 150 skills AI" or request direct URL
2. Clone repository:
   ```bash
   cd ~/projects
   git clone [repo-url]
   ```
3. Explore `skills/` directory for templates
4. Adapt skills to Claude format (see `skills/` directory in this project)

**Value**: Battle-tested patterns, real-world workflows

---

### 4.2 GitHub Spec Kit (Spec-Driven Development)

**Purpose**: Specification templates for pre-coding architecture

**Steps**:
1. Visit: https://github.com/github/spec-kit (or search "GitHub Spec Kit")
2. Clone or download:
   ```bash
   git clone https://github.com/github/spec-kit.git
   ```
3. Review spec templates
4. Use before `/build` phase to clarify requirements

---

### 4.3 Three Must-Know Vibe Coding Repos

**Purpose**: Essential reference implementations

**Steps**:
1. Request specific URLs from original Instagram reel (#51)
2. Clone each repository:
   ```bash
   git clone [repo-1-url]
   git clone [repo-2-url]
   git clone [repo-3-url]
   ```
3. Study code patterns
4. Extract reusable skills

**Note**: Exact URLs need to be obtained from content creator

---

## 5. Alternative Coding Agent Setup

### 5.1 MiMo Code (Xiaomi - Free)

**Steps**:
1. Search: "Xiaomi MiMo Code" for official website
2. Download installer
3. Install and configure
4. Use when Claude quota exhausted

---

### 5.2 ZCode (GLM 5.2 - Free)

**Steps**:
1. Search: "ZCode GLM 5.2" for download
2. Install following platform instructions
3. Alternative to Claude for large codebases

---

### 5.3 Qwen Code & Kimi Code (Free)

**Steps**:
1. Visit Qwen/Kimi official websites
2. Download and install
3. Use as free alternatives to paid coding agents

---

## 6. Security & Environment Setup

### 6.1 Create `.env` File

**Critical**: Never commit `.env` to git

**Steps**:
1. Create `.env` in project root:
   ```bash
   touch .env
   ```
2. Add to `.gitignore`:
   ```bash
   echo ".env" >> .gitignore
   ```
3. Add all API keys:
   ```bash
   # API Keys
   ANTHROPIC_API_KEY=sk-ant-your-key
   OPENAI_API_KEY=sk-your-key
   GITHUB_TOKEN=ghp_your-token
   
   # Database
   DATABASE_URL=postgresql://localhost:5432/mydb
   
   # Optional Tools
   OMNIROUTE_API_KEY=your-key
   ```

---

### 6.2 Verify `.gitignore` Configuration

**Steps**:
1. Open `.gitignore`
2. Ensure these entries exist:
   ```
   # Environment
   .env
   .env.local
   .env.*.local
   
   # Secrets
   *.key
   *.pem
   secrets/
   
   # API Keys
   api_keys/
   credentials.json
   ```
3. Check git status:
   ```bash
   git status
   # Verify .env is NOT listed
   ```

---

## 7. GitHub Security Settings (6 Free Configurations)

**Purpose**: Harden repository security

**Steps**:
1. Go to: `https://github.com/[username]/[repo]/settings/security_analysis`
2. Enable each setting:

   **1. Dependabot Security Alerts**
   - ☑️ Enable
   - Auto-notify of vulnerable dependencies

   **2. Dependabot Security Updates**
   - ☑️ Enable
   - Auto-create PRs to fix vulnerabilities

   **3. Secret Scanning**
   - ☑️ Enable
   - Detect committed API keys/tokens

   **4. Code Scanning (CodeQL)**
   - ☑️ Enable
   - Automated security code review

3. Go to: `https://github.com/[username]/[repo]/settings/branches`
4. Configure branch protection:

   **5. Branch Protection Rules**
   - Rule name: `main`
   - ☑️ Require pull request reviews (1 approval)
   - ☑️ Require status checks to pass

   **6. Signed Commits**
   - ☑️ Require signed commits
   - Setup GPG key: https://docs.github.com/en/authentication/managing-commit-signature-verification

---

## 8. Verification Checklist

Before proceeding to `/build` phase:

```markdown
□ API Keys configured in .env
□ .env added to .gitignore
□ GitHub PAT generated and stored
□ MCP servers configured (if using databases)
□ Free tools installed (OmniRoute, Claude Counter, Caveman)
□ External repos cloned for reference
□ GitHub security settings enabled
□ Verified no secrets committed to git
```

---

## 🆘 Troubleshooting

### Issue: "API key not found"
**Solution**: Verify `.env` file exists and key names match exactly (case-sensitive)

### Issue: "MCP server not connecting"
**Solution**: Check `.claude/mcp_servers.json` syntax, restart Claude Code

### Issue: ".env committed to git"
**Solution**:
```bash
git rm --cached .env
git commit -m "Remove .env from tracking"
```

### Issue: "GitHub token insufficient permissions"
**Solution**: Regenerate token with correct scopes (repo, workflow, read:org)

---

## 📞 Support Resources

- **Claude Documentation**: https://docs.anthropic.com/
- **MCP Protocol Docs**: https://modelcontextprotocol.io/
- **GitHub Security Guide**: https://docs.github.com/en/code-security

---

*Generated by Claude Autonomous Workspace System v1.0.0*  
*Manual steps identified from 78 Instagram reels + security best practices*
