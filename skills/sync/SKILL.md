# Sync Data

Push local sessions to the cloud and pull the latest evolved context (weights + insights) back to the local environment.

TRIGGER when: user says "sync data", "push sessions", "pull weights", "upload data", "sync with cloud", "sync vulca", "send feedback to cloud", "refresh evolved weights".

## Instructions

When the user wants to sync local VULCA data with the cloud:

1. Ask for sync direction if ambiguous:
   - **push** — upload pending local sessions/feedback to the cloud storage
   - **pull** — download the latest evolved context (weights, insights, few-shot examples)
   - **both** (default) — push first, then pull
2. Call the `sync_data` MCP tool with the chosen direction
3. Present results:
   - Sessions pushed: count of JSONL records uploaded
   - Evolved context pulled: confirmation + timestamp of the context version
   - Any errors or conflicts (e.g., duplicate session IDs)
4. After a successful pull, inform the user that the next evaluation/creation call will use the refreshed evolved weights

## Sync Status Formatting

```
Sync complete
  ↑ Pushed:  14 sessions  (feedback.jsonl → cloud)
  ↓ Pulled:  evolved_context.json  (updated 2026-03-28T09:12:33Z)
             3 traditions updated: chinese_xieyi, watercolor, photography
```

## Example

User: "Sync my data with the cloud"

Response flow:
1. Call `sync_data(direction="both")`
2. Report how many sessions were pushed
3. Confirm which traditions had their evolved context refreshed
4. Remind the user that subsequent evaluations will use the new weights
