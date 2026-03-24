# VULCA Claude Code Plugin

Cultural AI art evaluation + creation tools for Claude Code.

## Install

```bash
pip install vulca[mcp]
claude plugin install vulca-org/vulca-plugin
```

## Features

### MCP Tools (10 tools)

| Tool | Description |
|------|-------------|
| `evaluate_artwork` | L1-L5 cultural evaluation |
| `create_artwork` | Generate culturally-guided artwork |
| `list_traditions` | List 15+ cultural traditions |
| `get_tradition_guide` | Detailed tradition reference |
| `resume_artwork` | Resume HITL paused sessions |
| `get_evolution_status` | Check weight evolution |
| **`studio_create_brief`** | Create Brief from creative intent |
| **`studio_update_brief`** | NL update Brief |
| **`studio_generate_concepts`** | Generate concept designs |
| **`studio_select_concept`** | Select + refine concept |
| **`studio_accept`** | Finalize session + digest |

### Skills (4 skills)

| Skill | Trigger | Description |
|-------|---------|-------------|
| evaluate | "evaluate this painting" | Quick L1-L5 evaluation |
| create | "create artwork" | Cultural artwork generation |
| tradition | "show me xieyi guide" | Tradition reference lookup |
| **studio** | "start a studio session" | Brief-driven creative collaboration |

### Agents (1 agent)

| Agent | Description |
|-------|-------------|
| cultural-critic | Deep cross-cultural analysis |

## Requirements

- Python 3.10+
- `pip install vulca` (v0.5.0+)
- Gemini API key (for real VLM evaluation)

## License

Apache-2.0
