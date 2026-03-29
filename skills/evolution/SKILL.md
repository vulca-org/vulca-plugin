# Evolution Status

Check how VULCA has learned and adapted — view evolved L1-L5 weights per tradition, session counts, and digestion insights.

TRIGGER when: user says "evolution status", "weight evolution", "how have weights changed", "show evolution", "tradition evolution", "what has VULCA learned", "check digestion", "evolved weights".

## Instructions

When the user wants to inspect the evolution state:

1. Identify the tradition of interest (optional — if not specified, show overview for all traditions)
2. Call the `get_evolution_status` MCP tool with the tradition name (or omit for global view)
3. Present results clearly:
   - Session count (total sessions processed by the digestion system)
   - For each tradition: original YAML weights vs. evolved weights, highlighting changes ≥ 0.02
   - Insights extracted by the ContextEvolver (e.g., "xieyi users emphasise 留白 over line quality")
   - FewShot examples count (calibration references selected at ≥ 0.75 score)
4. If weights have drifted significantly, explain what user feedback drove the change
5. If no evolution has occurred yet (< 5 sessions), explain that more feedback is needed

## Weight Change Formatting

Show weight deltas clearly:

```
Tradition: chinese_xieyi  (23 sessions)
  L1 Brushwork:     0.25 → 0.35  (+0.10) ↑ strengthened
  L2 Composition:   0.20 → 0.18  (-0.02) ↓ slightly reduced
  L3 Color/Ink:     0.20 → 0.20   (0.00) — unchanged
  L4 Cultural Ref:  0.20 → 0.15  (-0.05) ↓ reduced
  L5 Innovation:    0.15 → 0.12  (-0.03) ↓ reduced
Insight: "Users consistently reward strong 气韵生动 and penalise mechanical brushwork."
FewShot examples: 12 (threshold ≥ 0.75)
```

## Example

User: "How have the weights changed for xieyi?"

Response flow:
1. Call `get_evolution_status(tradition="chinese_xieyi")`
2. Display original vs. evolved weights with delta arrows
3. Summarise the key insight from the ContextEvolver
4. Note how many calibration examples are now available
