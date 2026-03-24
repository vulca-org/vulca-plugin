---
name: studio
description: Create artwork through Brief-driven creative collaboration — intent analysis, concept generation, and cultural evaluation
user_invocable: true
arguments: intent (text), mood (optional), tradition (optional)
triggers:
  - studio
  - create brief
  - concept design
  - creative session
  - brief
---

# VULCA Studio — Brief-driven Creative Collaboration

Launch an interactive creative session using VULCA Studio.

## Usage

"Start a studio session for 赛博朋克水墨山水"
"Create a brief for Japanese ukiyo-e ocean waves"
"Generate concepts from my brief"

## What this does

1. **Intent Analysis** — Parses your creative vision, detects traditions and style
2. **Concept Generation** — Creates 4 concept designs for you to choose from
3. **Artwork Generation** — Produces final artwork based on your Brief
4. **Cultural Evaluation** — L1-L5 scoring against YOUR Brief criteria (not preset YAML)
5. **Natural Language Updates** — Refine any aspect by describing changes

## MCP Tools Used

- `studio_create_brief` — Create initial Brief from intent
- `studio_update_brief` — Update Brief with natural language
- `studio_generate_concepts` — Generate concept designs
- `studio_select_concept` — Choose a concept direction
- `studio_accept` — Finalize and trigger digestion

## Example

```
User: Start a studio session for 赛博朋克水墨山水
→ Creates Brief with style_mix: chinese_xieyi (60%) + cyberpunk (40%)
→ Generates 4 concept images
→ User selects concept 3, adds "more negative space"
→ Generates final artwork
→ Evaluates: L1=95% L2=90% L3=98% L4=100% L5=97%
→ Accepted + digested
```
