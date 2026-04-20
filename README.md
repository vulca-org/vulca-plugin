# VULCA — Claude Code & Cursor Plugin

Agent-native image-editing MCP surface. **21 MCP tools + 1 skill (`/decompose`)** for Claude Code and Cursor. v0.17.2 (tracks vulca SDK v0.17.2; 1454 tests).

## Install

```bash
pip install vulca[mcp]==0.17.2
claude plugin install vulca-org/vulca-plugin
```

For real image generation: either run [ComfyUI](https://github.com/comfyanonymous/ComfyUI) locally (free) or set `GOOGLE_API_KEY` for Gemini. Mock mode works without either.

## What happens in Claude Code

**You:** `> /decompose /path/to/painting.jpg`

**Claude:** Reads the image with `view_image`, authors a decomposition plan, calls `layers_split(mode="orchestrated", plan=...)`, returns one transparent PNG per entity. Iterates per the skill's 10-branch decision tree if segmentation fails on a specific entity.

## MCP Tools (21)

| Tool | Description |
|------|-------------|
| `generate_image` | Pure image generation (no evaluation loop) |
| `create_artwork` | Single-pass cultural-guided creation + evaluate |
| `inpaint_artwork` | Region-based inpainting |
| `view_image` | Read image metadata + base64 for the agent |
| `evaluate_artwork` | L1–L5 cultural scoring against a tradition |
| `list_traditions` | List all 13 cultural traditions |
| `get_tradition_guide` | Detailed tradition reference |
| `search_traditions` | Keyword search across tradition knowledge |
| `layers_split` | Decompose an image into semantic layers (orchestrated mode for `/decompose`) |
| `layers_list` | List layers in a session directory |
| `layers_edit` | Structural edits (add/remove/reorder/toggle/lock/merge/duplicate) |
| `layers_redraw` | Redraw one layer with new instructions |
| `layers_transform` | Apply transform ops to a layer |
| `layers_composite` | Composite layers back into a flat image |
| `layers_export` | Export to PNG directory with manifest |
| `layers_evaluate` | Per-layer L1–L5 evaluation |
| `brief_parse` | Parse a creative brief into structured form |
| `generate_concepts` | Generate N concept variation images from a prompt |
| `archive_session` | Archive a completed session for tradition-learning feedback |
| `sync_data` | Sync sessions + evolved weights |
| `unload_models` | Admin: release model memory (MPS/CUDA) |

## Skills (1)

| Skill | Trigger | What it does |
|-------|---------|--------------|
| `/decompose` | "decompose /path/img.jpg" | Loads SKILL.md, reads image, orchestrates `layers_split`, iterates per decision tree |

## Requirements

- Python 3.10+
- `uv` installed for the default MCP runner (`uvx --from vulca[mcp] vulca-mcp`)
- `pip install vulca[mcp]==0.17.2`

## License

Apache 2.0
