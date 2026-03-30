# VULCA Claude Code Plugin

AI-native cultural art creation organism for Claude Code. Selective Pipeline, Brief-driven Studio, Layered Generation + Inpainting, L1-L5 evaluation with actionable suggestions, Digestion V2 learning system, and 13 cultural traditions.

## Install

```bash
pip install vulca[mcp]
claude plugin install vulca-org/vulca-plugin
```

**For real VLM scoring + image generation** (optional):
```bash
export GOOGLE_API_KEY=your-key-here
```

Mock mode works without any API key.

### MCP Tools (18 tools)

| Tool | Description |
|------|-------------|
| `evaluate_artwork` | L1-L5 cultural evaluation |
| `create_artwork` | Generate culturally-guided artwork |
| `list_traditions` | List 13 cultural traditions |
| `get_tradition_guide` | Detailed tradition reference |
| `resume_artwork` | Resume HITL paused sessions |
| `get_evolution_status` | Check weight evolution |
| `sync_data` | Push sessions to cloud, pull evolved context |
| **`studio_create_brief`** | Create Brief from creative intent |
| **`studio_update_brief`** | NL update Brief |
| **`studio_generate_concepts`** | Generate concept designs |
| **`studio_select_concept`** | Select + refine concept |
| **`studio_accept`** | Finalize session + digest |
| **`inpaint_artwork`** | Inpaint / repaint a region of an artwork |
| **`analyze_layers`** | Decompose artwork into semantic layers |
| **`layers_composite`** | Composite layers back into artwork |
| **`layers_export`** | Export layers to PSD/PNG with manifest |
| **`layers_evaluate`** | Evaluate layer quality |
| **`layers_regenerate`** | Regenerate a specific layer |

### Skills (9 skills)

| Skill | Trigger | Description |
|-------|---------|-------------|
| evaluate | "evaluate this painting" | Quick L1-L5 evaluation |
| create | "create artwork" | Cultural artwork generation |
| tradition | "show me xieyi guide" | Tradition reference lookup |
| **studio** | "start a studio session" | Brief-driven creative collaboration |
| **inpaint** | "inpaint this", "fix this region" | Region-based inpainting |
| **layers** | "analyze layers", "show layer structure" | Semantic layer decomposition |
| **evolution** | "evolution status", "how have weights changed" | View evolved L1-L5 weights + digestion insights |
| **sync** | "sync data", "push sessions", "pull weights" | Push sessions to cloud, pull evolved context |
| **resume** | "resume session", "accept/refine/reject artwork" | HITL decision — accept, refine, or reject a paused session |

### Agents (1 agent)

| Agent | Description |
|-------|-------------|
| cultural-critic | Deep cross-cultural analysis |

### ComfyUI Nodes (11 nodes)

The VULCA ComfyUI integration provides 11 custom nodes for use in ComfyUI workflows:

| Node | Description |
|------|-------------|
| `VulcaBrief` | Create creative Brief from intent |
| `VulcaConcept` | Generate concept variations |
| `VulcaGenerate` | Full artwork generation |
| `VulcaEvaluate` | L1-L5 cultural evaluation |
| `VulcaUpdate` | NL Brief updates |
| `VulcaInpaint` | Region inpainting with cultural guidance |
| `VulcaLayersAnalyze` | Semantic layer decomposition |
| `VulcaLayersComposite` | Composite layers back into artwork |
| `VulcaLayersExport` | Export layers to PSD/PNG |
| `VulcaEvolution` | Weight evolution status reader |
| `VulcaTraditions` | List available traditions |

## Studio Pipeline (v0.9.0)

```
Intent → Concept → Generate → Evaluate → Refine
  ↑                                        ↓
  └──── Brief (living creative document) ←─┘
```

- **LLM intent parsing**: Gemini extracts implicit elements, palette, composition
- **Dynamic questions**: Domain-adaptive clarifying questions
- **Natural language updates**: "Put the teapot in the lower center"
- **Digestion V2**: Learns from your preferences across sessions

### Evaluation Modes

- **strict** (default): Judge mode — scores reflect conformance
- **reference**: Advisor mode — shows alignment without judgment
- **fusion**: Compare against multiple traditions at once

## Requirements

- Python 3.10+
- `pip install vulca` (v0.9.0+)
- Gemini API key (for real VLM evaluation)

## License

Apache-2.0

## Links

- SDK: [PyPI](https://pypi.org/project/vulca/) (v0.9.0, 813 tests)
- Paper: [VULCA Framework](https://aclanthology.org/2025.findings-emnlp/) (EMNLP 2025)
