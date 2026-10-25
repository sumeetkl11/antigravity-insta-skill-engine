# Claude Code Skills & Knowledge Vault Usage Guide

This directory preserves the complete, unaltered skill definitions and anti-slop documentation from both:
1. **`Anti_AI_Slop_Complete_Docs-v2`** (`docs/knowledge_vault/anti_ai_slop_v2/`)
2. **`Claude Code Skills Suite`** (`docs/knowledge_vault/claude_code_skills/`)

You can directly load and execute these skills inside **Claude Code**, **Anthropic API agents**, or **Antigravity**.

---

## 1. How to Use with Claude Code

### Method A: Project-Level Skills Directory (Recommended)
Claude Code automatically discovers skills located in `.claude/skills/` or `skills/` within your project root:
```bash
# To expose any skill to your current Claude Code project:
cp -r docs/knowledge_vault/claude_code_skills/source_skills/<skill-name> ~/.claude/skills/
```

### Method B: Referencing via `CLAUDE.md`
Add the following instruction to your project's `CLAUDE.md` or system prompt:
```markdown
## Anti-AI Slop Architecture & Design Rules
Follow the complete anti-slop guidelines defined in `docs/knowledge_vault/anti_ai_slop_v2/01_anti_ai_slop_fundamentals.md` through `09_copywriting_and_anti_cliche_rules.md`.

When designing interfaces:
- Never use generic centered 3-card templates.
- Enforce dynamic asymmetric bento grids with 2x whitespace.
- Use Geist Sans / Mono fonts with non-standard dark (#09090b) and light (#fafafa) tones.
- Reject marketing buzzwords like "supercharge" or "revolutionize".
- Use physics-based spring animations (stiffness 260, damping 20).
```

### Method C: Claude Code Plugin Format
If using Claude plugins:
- Point `.claude-plugin/plugin.json` to the target skills inside `docs/knowledge_vault/claude_code_skills/source_skills/`.

---

## 2. Directory Map

- **`anti_ai_slop_v2/`**:
  - `01_anti_ai_slop_fundamentals.md`: Bento grids, 2x whitespace, typography.
  - `02_framer_motion_animations.md`: Spring physics, magnetic hover.
  - `03_premium_ui_libraries.md`: Aceternity & Magic UI setup.
  - `04_shadcn_customization.md`: Gradient buttons, soft border radii.
  - `05_vp0_mcp_integration.md`: Free 21st.dev alternative.
  - `06_audio_and_haptics_microinteractions.md`: Tactile `use-sound` cues.
  - `07_noise_glassmorphism_shaders.md`: SVG grain overlay & glass borders.
  - `08_responsive_visual_qa_mcp.md`: Viewport QA (375px, 768px, 1440px).
  - `09_copywriting_and_anti_cliche_rules.md`: Banned buzzword replacement dictionary.
  - `10_chrome_devtools_and_playwright_mcp.md`: Playwright MCP browser automation.
  - `11_design_systems_and_stitch_mcp.md`: Stitch MCP & token systems.
  - `12_context7_docs_mcp.md`: Context7 live docs search.
  - `Ready-to-Use Master Prompt.txt`: The full copy-pasteable anti-slop prompt.

- **`claude_code_skills/`**:
  - `skills-guide.txt`: Quick 1-line reference for slash commands.
  - `core_design_skill.md`: Anthropic's flagship frontend design manifesto.
  - `source_skills/`: 33 independent agent skills (Tastemaker, Emil Kowalski motion system, Jakub Krehel UI polish, Humanizer, etc.).
