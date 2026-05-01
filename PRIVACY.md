# Privacy Notes

Vulca is local-first by default. The plugin reads local project files and image paths only when the user asks Claude Code to inspect, decompose, evaluate, or otherwise work with those artifacts.

Provider-backed actions are explicit opt-in. If the user configures an external provider such as OpenAI, Gemini, or a remote evaluation provider, prompts, images, masks, and provider metadata may be sent to that provider according to that provider's terms and the user's configuration.

The first public plugin release emphasizes no-cost or local workflows:

- visual discovery and direction cards;
- brainstorm/spec/plan artifacts;
- semantic decomposition of local images;
- rubric-based evaluation.

Generation, redraw, inpaint, provider-backed VLM evaluation, and other cost-incurring or upload-capable workflows should remain clearly user-approved actions.

Vulca does not sell user data and does not host a foundation image model.
