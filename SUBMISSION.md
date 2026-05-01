# Claude Plugin Submission Packet

**Plugin name:** Vulca
**Version:** 0.19.0
**Repository:** https://github.com/vulca-org/vulca-plugin
**License:** Apache-2.0

## One-Liner

Vulca is an agent-native visual control layer for discovery, structured prompts, semantic layers, and cultural evaluation.

## Short Description

Add visual discovery, decomposition, planning, and L1-L5 cultural evaluation workflows to Claude Code.

## Long Description

Vulca helps Claude Code users work with images through reviewable creative artifacts instead of one-shot prompting. It can explore fuzzy visual intent, produce direction cards, compose provider-aware prompts, decompose images into semantic layers, and evaluate visual results against cultural and quality criteria.

Vulca works with local files and configured image providers. Provider-backed generation, editing, and evaluation are explicit opt-in workflows.

## First-Release Emphasis

- `/vulca:visual-discovery` for taste, culture, and direction exploration.
- `/vulca:visual-brainstorm`, `/vulca:visual-spec`, and `/vulca:visual-plan` for proposal/design/plan artifacts.
- `/vulca:decompose` for semantic layer extraction.
- `/vulca:evaluate` for structured L1-L5 review.

## Safety And Boundaries

- Vulca does not host a foundation image model.
- Provider output quality is not guaranteed.
- Cultural terminology does not guarantee better image generation.
- Redraw and inpaint are advanced SDK/MCP workflows, not polished first-release skills for every image.
- Real-provider generation, editing, and VLM-backed evaluation should remain explicit opt-in.

## Validation

Run from this repository:

```bash
claude plugin validate .
claude plugin validate .claude-plugin/plugin.json
gemini extensions validate .
codex marketplace add .
python3 -m json.tool .claude-plugin/plugin.json
python3 -m json.tool .codex-plugin/plugin.json
python3 -m json.tool .agents/plugins/marketplace.json
python3 -m json.tool .claude-plugin/marketplace.json
python3 -m json.tool .mcp.json
python3 -m json.tool gemini-extension.json
```

Observed on 2026-05-01: Claude marketplace and plugin manifest validation passed; Gemini CLI extension validation passed; Codex marketplace add validation passed.

## Gemini CLI Extension

This repository is also packaged as a Gemini CLI extension. Users can install the public repository directly:

```bash
pip install "vulca[mcp]==0.19.0"
gemini extensions install vulca-org/vulca-plugin
```

The Gemini extension loads `GEMINI.md` as persistent context and starts the `vulca-mcp` server from `PATH`.

## Codex Desktop / CLI Marketplace

This repository is also packaged as a Codex-compatible plugin marketplace. Users can install the public repository directly:

```bash
pip install "vulca[mcp]==0.19.0"
codex marketplace add https://github.com/vulca-org/vulca-plugin
```

The Codex plugin manifest is `.codex-plugin/plugin.json`, and the marketplace entry is `.agents/plugins/marketplace.json`.

## Screenshot Checklist

- Plugin visible in Claude Code plugin UI.
- `/help` or skill list showing `vulca:*` skills.
- A no-cost `/vulca:visual-discovery` run producing direction cards.
- A no-cost `/vulca:evaluate` or rubric-only evaluation artifact.
- Terminal capture of `claude plugin validate .`.

Do not include private user images, provider API keys, or hidden local paths in screenshots.
