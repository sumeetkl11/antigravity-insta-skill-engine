# Graphify Visual Dependency Map

```mermaid
graph TD
    SM[.antigravity/state_manifest.json<br/>Token Conservation Root] --> VC[01_core_antigravity_links.md<br/>10 Prompts & IDE Setups]
    SM --> VS[02_skills_and_repos.md<br/>13 Repos & MCP Tools]
    SM --> VG[03_graphify_and_ponytail.md<br/>16 Workflows & Automations]
    SM --> VU[04_ui_and_feature_inspo.md<br/>39 Frontend & UI Patterns]
    VC --> PP[docs/project_plot.md<br/>Master Architecture Roadmap]
    VS --> PP
    VG --> PP
    VU --> PP
    VS --> MG[docs/manual_setup_steps.md<br/>Human Credentials & Auth]
    PP --> PT[.antigravity/ponytail/skill_pipeline.yaml<br/>Sequential Skill Execution]
```

## Graph Node Topology
1. **Token Root**: `state_manifest.json` acts as pre-flight gatekeeper.
2. **Intelligence Vaults**: 4 clustered files containing all 78 indexed links.
3. **Master Plot**: Consolidates intelligence into an actionable implementation blueprint.
4. **Execution Router**: Ponytail enforces sequential, token-minimized skill triggering.