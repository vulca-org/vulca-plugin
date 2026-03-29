# Analyze Layers

Decompose an artwork into its constituent semantic layers — foreground subjects, mid-ground elements, background, and atmospheric effects — using VULCA's layered generation analysis.

TRIGGER when: user says "analyze layers", "split into layers", "show layers", "layer structure", "decompose", "export layers", "what layers does this have", "break down into layers", "show me the layer breakdown".

## Instructions

When the user wants to analyze or decompose an artwork into layers:

1. Identify the source image (file path or ask the user)
2. Call the `analyze_layers` MCP tool with the image path
3. Present the layer breakdown clearly:
   - Layer names and semantic descriptions
   - Bounding boxes for each layer (x, y, w, h)
   - Blend modes (normal, multiply, overlay, screen, etc.)
   - Layer order (back to front)
4. If the user wants to export or work with a specific layer, confirm which one and proceed

## What You'll See

Each layer in the result includes:
- **Name**: Semantic label (e.g., "sky", "mountain silhouette", "foreground foliage", "mist overlay")
- **Description**: What the layer contains and its visual role
- **Bounding box**: Where the layer sits in the canvas
- **Blend mode**: How it composites with layers below

## Example

User: "Show me the layer structure of this ink landscape"

Response flow:
1. Call `analyze_layers(image_path="ink_landscape.png")`
2. Present results like:
   ```
   Layer 1 (Background): Sky wash — soft gradated grey, full canvas, normal blend
   Layer 2 (Mid): Distant mountains — silhouetted peaks, upper 60%, multiply blend
   Layer 3 (Mid): Mid-ground trees — sparse pine, center, normal blend
   Layer 4 (Fore): Foreground rocks — ink splashes, lower third, normal blend
   Layer 5 (Atmosphere): Mist/cloud overlay — diffuse white, center band, screen blend
   ```
3. Note which layers are most culturally significant (e.g., "the mist layer is a key 留白 — negative space — device in xieyi painting")

## Use Cases

- **Understanding composition**: See how an artwork is structured before requesting edits
- **Targeted inpainting**: Use layer info to precisely describe regions for `inpaint_artwork`
- **Style analysis**: Identify atmospheric/overlay layers that define the cultural feel
- **Reference decomposition**: Analyze reference artworks before generating new ones
