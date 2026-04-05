# VULCA — Claude Code & Cursor Plugin

Create and evaluate cultural art directly in your AI coding environment. **21 MCP tools**, 10 skills, 13 traditions. v0.9.2 (1322 tests).

## Install

```bash
pip install vulca[mcp]
claude plugin install vulca-org/vulca-plugin
```

For real VLM scoring (optional): `export GOOGLE_API_KEY=your-key`. Mock mode works without any API key.

## What You Can Do

**You:** *"Evaluate this painting for Chinese xieyi style"*

**Claude:** Calls `evaluate_artwork` → returns L1-L5 scores, rationales, and actionable suggestions.

**You:** *"Create a tea packaging design with mountain landscape"*

**Claude:** Calls `create_artwork` → generates image, evaluates on L1-L5, returns scores + improvement suggestions.

**You:** *"Start a studio session for a Zen garden"*

**Claude:** Calls `studio_create_brief` → interactive Brief-driven workflow with concept generation, selection, and refinement.

## MCP Tools (21)

| Tool | Description |
|------|-------------|
| `evaluate_artwork` | L1-L5 cultural evaluation with suggestions |
| `create_artwork` | Generate culturally-guided artwork |
| `list_traditions` | List 13 cultural traditions |
| `get_tradition_guide` | Detailed tradition reference (weights, terminology, taboos) |
| `resume_artwork` | Resume HITL paused sessions |
| `get_evolution_status` | Check evolved weights + digestion insights |
| `sync_data` | Push sessions to cloud, pull evolved context |
| `studio_create_brief` | Create Brief from creative intent |
| `studio_update_brief` | Natural language Brief update |
| `studio_generate_concepts` | Generate concept designs |
| `studio_select_concept` | Select + refine concept |
| `studio_accept` | Finalize session + digest |
| `inpaint_artwork` | Region-based inpainting |
| `analyze_layers` | Decompose artwork into semantic layers |
| `layers_composite` | Composite layers back into artwork |
| `layers_export` | Export layers to PNG directory with manifest |
| `layers_evaluate` | Per-layer L1-L5 evaluation |
| `layers_regenerate` | Regenerate a specific layer |
| `tool_brushstroke_analyze` | Brushstroke texture energy + direction detection |
| `tool_composition_analyze` | Rule of thirds, center weight, balance |
| `tool_whitespace_analyze` | Negative space ratio + distribution |
| `tool_color_gamut_check` | Saturation profiling + gamut compliance |
| `tool_color_correct` | Color balance analysis + correction |

## Skills (10)

| Skill | Trigger | What it does |
|-------|---------|-------------|
| evaluate | "evaluate this painting" | Quick L1-L5 evaluation |
| create | "create artwork" | Cultural artwork generation |
| tradition | "show me xieyi guide" | Tradition reference lookup |
| studio | "start a studio session" | Brief-driven creative collaboration |
| inpaint | "inpaint this region" | Region-based repaint |
| layers | "analyze layers" | Semantic layer decomposition |
| evolution | "evolution status" | View evolved L1-L5 weights |
| sync | "sync data" | Push sessions, pull evolved context |
| resume | "resume session" | Accept/refine/reject paused session |
| release | "release new version" | Automated version release |

## Agent

| Agent | What it does |
|-------|-------------|
| cultural-critic | Deep cross-cultural analysis comparing multiple traditions |

## Requirements

- Python 3.10+
- `pip install vulca[mcp]` (v0.9.2)
- Gemini API key (optional, for real VLM evaluation)

## Links

- SDK: [PyPI](https://pypi.org/project/vulca/) (v0.9.2)
- ComfyUI: [comfyui-vulca](https://github.com/vulca-org/comfyui-vulca) (11 nodes)
- Paper: [VULCA Framework](https://aclanthology.org/2025.findings-emnlp/) (EMNLP 2025)

## License

Apache-2.0
