# Separated Plot Blueprint, Autonomous Configs & Manual Setup Guide

Ye document cover karta hai ke:
1. **Separated Plot (`docs/project_plot.md`)** kaisa dikhega.
2. **Graphify & Ponytail** ko agent khud kaise configure karega.
3. Jo cheezein agent khud nahi kar sakta, unki **Step-by-Step Setup Guide** aapko kaise milegi.

---

## PART 1: The Separated Plot (`docs/project_plot.md`)
*(Ye file links se bilkul alag `docs/` folder mein banti hai)*

```markdown
# MASTER PROJECT PLOT & EXECUTION ROADMAP

## 1. Core Objective
Build a token-optimized, modular application where Graphify manages file context relationships and Ponytail routes coding skills step-by-step.

## 2. Step-by-Step Skill Execution Order (Ponytail Sequence)
1. **Step 1 (Pre-Flight)**: Load `.antigravity/state_manifest.json` -> Verify cached state.
2. **Step 2 (Context Graph)**: Query `.antigravity/graphify/project_graph.json` -> Select only active target files.
3. **Step 3 (Skill Execution)**: Trigger specific coding/repo skill from `skills/`.
4. **Step 4 (Validation & Tail Update)**: Run syntax check -> Update manifest -> Unload skill from memory.

## 3. Repository Integration Plan
- **Repo 1 (Graphify Local Engine)**: Auto-configured in `.antigravity/graphify/`.
- **Repo 2 (Ponytail Router)**: Auto-configured in `.antigravity/ponytail/`.
- **Extracted Feature Repos**: Cloned into `skills/` and linked to `src/`.
```

---

## PART 2: Autonomous Configurations (Agent Creates These Himself)

### A. `.antigravity/state_manifest.json` (Token Saver)
Agent har baar shuru hone se pehle ye choti si file padhta hai taake poore project ke tokens kharch na hon:
```json
{
  "project_status": "initialized",
  "last_command": "/plan",
  "links_stats": {
    "total_submitted": 12,
    "categorized": 10,
    "unresolved": 2
  },
  "active_tools": {
    "graphify_enabled": true,
    "ponytail_enabled": true
  },
  "processed_modules": ["folder_scaffolding", "link_categorization"]
}
```

### B. `.antigravity/ponytail/skill_pipeline.yaml` (Prompt Tail & Skill Manager)
Har prompt ke saath agent ye rule check karta hai ke kab kaunsa skill use karna hai:
```yaml
ponytail_router:
  version: "1.0"
  default_behavior: "token_minimal"
  prompt_tail_rules:
    - trigger: "architecture_or_file_change"
      require_graphify: true
      skill_sequence:
        - "load_graph_node"
        - "apply_modular_code_skill"
        - "update_graph_edges"
    - trigger: "new_link_or_repo"
      require_graphify: false
      skill_sequence:
        - "browser_extract_metadata"
        - "categorize_into_vault"
        - "sync_project_plot"
```

---

## PART 3: Step-by-Step Guide for Things Agent Cannot Do Himself (`docs/manual_setup_steps.md`)

Jab koi aisi cheez aayegi jo AI khud nahi kar sakta (jaise private API key, GitHub personal token, ya external CLI login), toh agent uske benefits par lamba bhashan dene ke bajaye (kyunki benefits aapko pehle se pata hain) seedha aisi **Step-by-Step Developer Guide** bana kar dega:

```markdown
# Manual Setup Guide (Human Action Required)

Maine saara local folder structure, Graphify nodes, aur Ponytail pipelines khud setup kar diye hain. Niche di gayi cheezon ke liye aapki manual permission ya keys chahiye:

---

### Setup 1: Instagram Authenticated Scraping / Cookie (Optional for Private Reels)
Agar aap chahte hain ke built-in browser login-blocked reels bhi read kar le:
1. Open your browser where Instagram is logged in.
2. Copy the public share URL or enable local browser session sharing in AntiGravity settings:
   - Go to **AntiGravity Settings > Tools > Built-in Browser**.
   - Toggle **"Use Local Session Profile"** to `ON`.
3. Alternatively, simply paste the reel caption inside `AntiGravity Insta Links/unresolved_links.md` and run `/resolve`.

---

### Setup 2: External GitHub / Skill API Keys
Kuch extracted skills ko external API key ki zaroorat hai:
1. Root folder mein `.env.example` file maine bana di hai.
2. Terminal mein ye command run karein:
   ```bash
   cp .env.example .env
   ```
3. Apni keys `.env` file mein in exact lines ke aage paste karein:
   ```env
   EXTERNAL_SKILL_API_KEY="paste_your_key_here"
   GITHUB_ACCESS_TOKEN="paste_your_token_here"
   ```
4. Save karein aur chat mein `/build` likh kar bhej dein—baaki kaam main khud complete kar loonga.
```