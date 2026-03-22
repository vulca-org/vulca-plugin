# VULCA — Claude Code Plugin

Cultural art evaluation and guided creation for Claude Code. Score artworks on L1-L5 dimensions across 13 cultural traditions.

## Install

```bash
# 1. Install the SDK (required)
pip install vulca[mcp]

# 2. Add the plugin marketplace
claude plugin marketplace add vulca-org/vulca-plugin

# 3. Install the plugin
claude plugin install vulca
```

**For real VLM scoring** (optional):
```bash
export GOOGLE_API_KEY=your-key-here
```

Mock mode works without any API key.

## What's Included

| Type | Name | Description |
|------|------|-------------|
| MCP Tool | `evaluate_artwork` | L1-L5 scoring with rationale |
| MCP Tool | `create_artwork` | Generate → Evaluate → Decide pipeline |
| MCP Tool | `list_traditions` | Browse 13 cultural traditions |
| MCP Tool | `get_tradition_guide` | Terminology, taboos, weights |
| MCP Tool | `resume_artwork` | HITL: accept / refine / reject |
| MCP Tool | `get_evolution_status` | Weight evolution history |
| Skill | `/evaluate` | "Evaluate this artwork for Chinese xieyi" |
| Skill | `/create` | "Create a Japanese ink wash landscape" |
| Skill | `/tradition` | "What traditions are available?" |
| Agent | cultural-critic | Deep cross-tradition analysis |

## Usage

Just ask Claude Code naturally:

> "Evaluate painting.jpg for Chinese xieyi tradition"

> "Create a misty mountain landscape in ink wash style"

> "Compare how this image scores in watercolor vs photography traditions"

## Providers

Image generation: `mock` (no key), `gemini` (Google), `openai` (DALL-E 3), `comfyui` (local SD)

VLM scoring: Gemini (default), or any LiteLLM-supported model via `--vlm-model`

## Links

- SDK: [vulca-org/vulca](https://github.com/vulca-org/vulca) | [PyPI](https://pypi.org/project/vulca/)
- Paper: [VULCA Framework](https://aclanthology.org/2025.findings-emnlp/) (EMNLP 2025)
