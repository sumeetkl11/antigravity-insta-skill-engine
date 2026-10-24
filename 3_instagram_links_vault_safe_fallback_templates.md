# Templates: `AntiGravity Insta Links/` Vault & Safe Fallback

Ye file dikhati hai ke Agent aapke Instagram links ko kaise alag folder mein rakhega, kaise similar meaning wale links ko ek saath group karega, aur jo link open na ho usko kaise safe side par alag rakhega.

---

## File 1: `AntiGravity Insta Links/01_core_antigravity_links.md`
*(Yahan sirf AntiGravity ke core features, prompts, aur agent setups wale links aayenge)*

```markdown
# Core AntiGravity Links & Setups

### Cluster A: Agent Initialization & Token Saving
- **URL**: [https://www.instagram.com/reel/example1/]
- **Extracted Meaning**: Shows how to configure `.antigravity` rules to cache file trees and save 60% input tokens.
- **Target Action**: Auto-implemented in `.antigravity/state_manifest.json`.

### Cluster B: Custom Slash Commands
- **URL**: [https://www.instagram.com/reel/example2/]
- **Extracted Meaning**: Explains setting up `/plan` and `/build` workflows for multi-agent coding.
- **Target Action**: Mapped to Master Agent Prompt.
```

---

## File 2: `AntiGravity Insta Links/02_skills_and_repos.md`
*(Yahan saare GitHub repositories, MCP servers, aur coding skills wale links ikatthe honge)*

```markdown
# Extracted Skills & GitHub Repositories

### Cluster A: Coding & Scaffolding Skills
- **URL**: [https://www.instagram.com/reel/example3/]
- **Mentioned Repo/Skill**: `github.com/example/auto-skill-runner`
- **Context/Meaning**: Automates boilerplate creation and lint checking before commits.
- **Can Agent Do It Autonomous?**: YES (Agent will clone and configure in `skills/`).

### Cluster B: External API Integrations
- **URL**: [https://www.instagram.com/reel/example4/]
- **Mentioned Repo/Skill**: External Auth / Cloud DB Connector
- **Context/Meaning**: Connects local agent state with remote vector storage.
- **Can Agent Do It Autonomous?**: PARTIAL (Agent writes code; User must provide API Key via Manual Setup Guide).
```

---

## File 3: `AntiGravity Insta Links/03_graphify_and_ponytail.md`
*(Yahan Graphify aur Ponytail se related links aur workflows rahenge)*

```markdown
# Graphify & Ponytail Orchestration Links

### Cluster A: Graphify Node Mapping
- **URL**: [https://www.instagram.com/reel/example5/]
- **Extracted Meaning**: Converting codebase files into a JSON dependency graph so the LLM only reads connected files.
- **Target Action**: Agent autonomously builds `.antigravity/graphify/project_graph.json`.

### Cluster B: Ponytail Skill Sequencing
- **URL**: [https://www.instagram.com/reel/example6/]
- **Extracted Meaning**: Attaching a sequential execution tail to every prompt so skills trigger in strict order.
- **Target Action**: Agent autonomously builds `.antigravity/ponytail/skill_pipeline.yaml`.
```

---

## File 4: `AntiGravity Insta Links/unresolved_links.md` (SAFE FALLBACK)
*(Agar built-in browser kisi Instagram link ko login wall ki wajah se read na kar paye, toh agent usko yahan rakhega taake aap khud uska context likh sakein)*

```markdown
# Unresolved Instagram Links (Action Required)

> **Instructions for User**: Neeche diye gaye links Instagram Login Wall ya Bot Protection ki wajah se built-in browser mein open nahi ho sake. Bas `Manual Context / Caption` ke aage 1 line mein likh dein ke is reel mein kya bataya gaya hai, aur phir `/resolve` run karein.

---

### 1. Blocked Link #1
- **URL**: [https://www.instagram.com/reel/blocked_link_1/]
- **Failure Reason**: Redirected to Instagram Login Page
- **Manual Context / Caption (Paste Here)**: [ Yahan caption ya tool ka naam likhein ]

### 2. Blocked Link #2
- **URL**: [https://www.instagram.com/p/blocked_link_2/]
- **Failure Reason**: Empty metadata returned
- **Manual Context / Caption (Paste Here)**: [ Yahan caption ya tool ka naam likhein ]
```