# Vulca Claude Code Plugin

Vulca is an agent-native visual control layer for Claude Code. It turns fuzzy creative intent into reviewable direction cards, structured prompts, semantic layers, provider-routed image work, and L1-L5 cultural evaluation.

This plugin tracks the Vulca SDK v0.19.0 package shape.

## Install

```bash
pip install "vulca[mcp]==0.19.0"
claude plugin install vulca-org/vulca-plugin
```

For local development, you can validate this repository directly:

```bash
claude plugin validate .
claude --plugin-dir .
```

The bundled MCP configuration starts `vulca-mcp` from your `PATH`. Configure provider API keys only when you explicitly want real-provider generation, editing, or evaluation. Mock/no-cost workflows work without external provider keys.

## Skills

| Skill | Purpose |
| --- | --- |
| `/decompose` | Decompose an image into semantic transparent layers. |
| `/visual-discovery` | Turn fuzzy visual intent into taste profile, direction cards, and prompt artifacts. |
| `/visual-brainstorm` | Convert a selected direction into a reviewable proposal. |
| `/visual-spec` | Resolve provider, prompt, threshold, and cost decisions into `design.md`. |
| `/visual-plan` | Execute planned generation/evaluation iterations from `design.md`. |
| `/evaluate` | Evaluate an existing image against Vulca's cultural and visual rubric. |
| `/using-vulca-skills` | Meta-skill that guides when Claude should invoke the Vulca workflow skills. |

## Positioning

Vulca does not host a foundation image model and does not promise one-click image quality. It coordinates provider-backed workflows through auditable artifacts:

```text
discovery.md
taste_profile.json
direction_cards.json
proposal.md
design.md
plan.md
manifest.json
evaluation.json
```

Redraw and inpaint tools are available as advanced MCP workflows in the SDK. They should not be marketed as polished top-level user skills until target-aware redraw evidence has been reviewed on real images.

## Privacy

Vulca works with local image files and optional external image providers. When you opt into a real provider, prompts, images, and provider metadata may leave your machine depending on that provider's configuration and terms. Keep generation, editing, and VLM-backed evaluation explicit.

See [PRIVACY.md](PRIVACY.md) for submission-ready privacy notes and [SUBMISSION.md](SUBMISSION.md) for marketplace copy and validation commands.

## License

Apache-2.0
