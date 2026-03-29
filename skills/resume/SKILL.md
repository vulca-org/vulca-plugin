# Resume Session (HITL Decision)

Resume a paused Human-in-the-Loop (HITL) artwork session by making an accept, refine, or reject decision.

TRIGGER when: user says "resume session", "continue artwork", "accept artwork", "reject artwork", "refine artwork", "HITL decision", "make a decision on my session", "approve this artwork", "I want to refine", "reject this round".

## Instructions

When the user wants to resume a paused HITL session:

1. Identify the session to resume:
   - Ask for the `session_id` if not provided (it appears in the output of a previous `create_artwork` call with `hitl=True`)
2. Identify the action:
   - **accept** — finalize the current result as-is; triggers digestion
   - **refine** — continue the pipeline with additional guidance; ask for feedback text
   - **reject** — discard this round and restart from scratch; ask for feedback text
3. Optionally identify locked dimensions:
   - Ask if the user wants to lock any L1-L5 dimensions (prevents the pipeline from changing them in the next round)
   - Example: "lock L1 and L3" → `locked_dimensions: ["L1", "L3"]`
4. Call the `resume_artwork` MCP tool with `session_id`, `action`, and optionally `feedback` + `locked_dimensions`
5. Present the result:
   - Updated session status (completed / running / waiting)
   - L1-L5 scores after the decision (if available)
   - Next pipeline step (if refining)
   - Digestion confirmation (if accepting)

## Decision Guide

| Action | When to use | Effect |
|--------|-------------|--------|
| `accept` | Happy with the current result | Finalizes artwork, triggers digestion loop |
| `refine` | Good direction, needs adjustment | Continues pipeline with your feedback as an instruction |
| `reject` | Wrong direction entirely | Resets this round; feedback is recorded for learning |

## Example

User: "Accept the artwork from session abc-123"

Response flow:
1. Call `resume_artwork(session_id="abc-123", action="accept")`
2. Show final L1-L5 scores
3. Confirm the session is complete and digestion has been triggered

User: "Refine session abc-456 — make the composition more asymmetric, lock L2"

Response flow:
1. Call `resume_artwork(session_id="abc-456", action="refine", feedback="Make the composition more asymmetric", locked_dimensions=["L2"])`
2. Show the pipeline resuming with L2 locked
3. Display updated scores once the next round completes
