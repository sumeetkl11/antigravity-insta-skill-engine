# Claude Anti-Slop Checker

> **Version**: 1.0.0  
> **Category**: Quality Assurance  
> **Priority**: High

---

## Purpose

Validates AI-generated UI/UX against generic AI patterns. Prevents shipping websites/apps that look like "every other AI-generated site."

---

## Trigger Conditions

- **Automatic**: Before presenting any UI/web design to user
- **Manual**: `/check-slop` command
- **Integration**: Part of verification phase in Ponytail pipeline

---

## The Anti-AI-Slop Checklist

Run this validation before shipping ANY UI:

### ❌ Visual Anti-Patterns (Remove These)

```yaml
forbidden_elements:
  gradients:
    - Purple/blue gradients
    - Glassmorphism effects
    - Excessive backdrop-blur
  
  icons:
    - Generic placeholder icons
    - Stock illustration sets
    - Default icon libraries without customization
  
  navigation:
    - Scroll-down arrows
    - Animated scroll indicators
    - "Scroll to explore" text
  
  layout:
    - Generic "three feature cards" layout
    - Hero section with gradient background
    - Fake dashboard screenshots
    - Placeholder "John Smith" data
```

### ✅ Approved Replacements

```yaml
use_instead:
  colors:
    - Flat color + single accent
    - Brand-specific palette (no purple/blue combos)
    - Solid backgrounds over gradients
  
  icons:
    - Actual product screenshots
    - Real user interface captures
    - Custom brand iconography
  
  navigation:
    - Clean navigation without scroll hints
    - Trust users know how to scroll
  
  content:
    - Real data (even if demo data)
    - Actual product names/values
    - Authentic user scenarios
```

### 📝 Copy Anti-Patterns (Rewrite These)

```yaml
forbidden_words:
  - "revolutionize"
  - "empower"
  - "seamlessly"
  - "cutting-edge"
  - "next-generation"
  - "unlock the potential"
  - "transform your workflow"

approved_style:
  - Plain English
  - Direct statements
  - Concrete benefits
  - Specific features
```

---

## Execution Instructions

### Step 1: Visual Audit

```markdown
Scan generated UI for:
□ Purple or blue gradients → Replace with flat color
□ Glassmorphism effects → Remove or simplify
□ Generic icons → Replace with screenshots
□ Scroll arrows → Remove completely
□ Three-card feature layout → Redesign layout
□ Fake dashboard images → Use real or remove
```

### Step 2: Content Audit

```markdown
Scan copy for:
□ "Revolutionize" or similar → Rewrite in plain English
□ "Empower users" → Specify actual capability
□ Generic examples → Replace with real data
□ Placeholder names → Use realistic examples
```

### Step 3: Layout Audit

```markdown
Check for distinctive design:
□ Not using default Tailwind gradients
□ Not using standard "SaaS template" structure
□ Has unique visual identity
□ Looks different from AI-generated competitors
```

---

## Validation Response Format

### Example 1: Failed Validation

```markdown
⚠️ **Anti-Slop Check: FAILED**

Issues found:
1. Hero section uses purple-to-blue gradient
2. Three generic feature cards detected
3. Copy contains "revolutionize" (line 23)
4. Using placeholder "John Smith" data (3 instances)
5. Scroll-down arrow in hero section

Recommendations:
- Replace gradient with solid color + accent
- Redesign feature section (avoid three-card layout)
- Rewrite: "revolutionize" → "streamline" or specific verb
- Add realistic demo data
- Remove scroll arrow

Status: ❌ DO NOT SHIP until fixed
```

### Example 2: Passed Validation

```markdown
✅ **Anti-Slop Check: PASSED**

Validation results:
✓ No purple/blue gradients detected
✓ Flat color palette with single accent (#2E5CFF)
✓ Copy uses plain English (no "revolutionize")
✓ Real product screenshots instead of icons
✓ Realistic demo data (no placeholders)
✓ Unique layout (not generic three-card)
✓ No scroll arrows or indicators

Distinctive elements:
- Bento Grid layout with asymmetric cards
- Custom brand color (#2E5CFF)
- Real product screenshots
- Direct, benefit-focused copy

Status: ✅ APPROVED for shipping
```

---

## Integration with Design System

If MCP design system is available, validate against approved styles:

```yaml
mcp_query: "design-system-server/validate"
payload:
  - check_palette_against_approved_colors
  - check_layout_against_generic_templates
  - check_copy_against_forbidden_words
  
response:
  approved: true/false
  issues: [list]
  suggestions: [list]
```

---

## Examples

### Example 1: Landing Page Check

```
User: "Built landing page for SaaS product"

Claude (runs anti-slop checker):
⚠️ Issues detected:
1. Purple gradient (hero section) → Use flat color
2. "Revolutionize your workflow" → Rewrite as "Automate repetitive tasks"
3. Three feature cards → Redesign as Bento Grid
4. Generic rocket icon → Use product screenshot

Prompt to fix:
"Remove purple gradient, use solid #1A1A1A background with #00E5A0 accent.
Rewrite hero copy: 'Automate repetitive tasks and save 10 hours per week.'
Replace three-card layout with asymmetric Bento Grid.
Replace rocket icon with actual product screenshot."
```

### Example 2: Dashboard Check

```
User: "Generated analytics dashboard"

Claude (runs anti-slop checker):
✅ Passed all checks:
- No gradients (using flat dark theme)
- Real data visualization (not fake numbers)
- Custom chart colors (brand palette)
- No placeholder names
- Unique dashboard layout

Status: Ready to ship
```

---

## Success Metrics

- ✅ Zero generic AI patterns in shipped UI
- ✅ Distinctive visual identity for every project
- ✅ Plain English copy (no "revolutionize")
- ✅ Real data instead of placeholders

---

*Extracted from: Knowledge Vault - 04_ui_ux_design.md (Reels #68, #69)*  
*Based on: Open-source anti-slop skill + AI design pattern research*
