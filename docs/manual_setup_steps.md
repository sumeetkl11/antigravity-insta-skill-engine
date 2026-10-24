# Manual Setup Guide (Human Action Required)

> **Notice**: All folder structures, link vaults, Graphify maps, and Ponytail pipelines have been created autonomously by the agent.
> Niche di gayi steps sirf un cheezon ke liye hain jo external security, API keys ya user permissions demand karti hain.

---

### Step 1: External API Keys & Credentials (.env)
Agar aap external AI models ya GitHub API tools connect karna chahte hain:
1. Root directory mein `.env.example` template mojood hai.
2. Terminal mein ye command run karein:
   ```bash
   cp .env.example .env
   ```
3. `.env` file ko open karein aur apni respective keys paste karein:
   ```env
   GITHUB_TOKEN="your_github_personal_access_token"
   CLAUDE_API_KEY="your_anthropic_api_key"
   OPENAI_API_KEY="your_openai_api_key"
   ```

---

### Step 2: Unresolved Links Review (Currently Complete)
- Current status: **0 Unresolved Links**. All 78 links have been resolved and categorized.
- Agar aap future mein naye links add karein aur wo login wall ki wajah se block hon:
  1. `AntiGravity Insta Links/unresolved_links.md` open karein.
  2. Reel ka caption ya tool ka naam 1 line mein paste karein.
  3. Chat mein `/resolve` likhein.

---

### Step 3: Proceeding to Full Build
Aap kisi bhi waqt `/build` command dekar execution phase ko trigger kar sakte hain.