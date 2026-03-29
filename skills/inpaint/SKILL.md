# Inpaint Artwork

Inpaint or repaint a specific region of an existing artwork using VULCA's culturally-guided inpainting pipeline.

TRIGGER when: user says "inpaint this", "fix this region", "repaint", "redraw part of", "fix the sky", "change the background", "touch up this area", "replace this section".

## Instructions

When the user wants to inpaint or modify a region of an artwork:

1. Identify the source image (file path or ask the user)
2. Identify the region to inpaint — accept natural language description (e.g., "the sky in the upper half") or bounding box coordinates [x, y, w, h]
3. Identify the instruction — what should replace or fill the region (e.g., "replace with stormy clouds in xieyi style")
4. Identify the tradition (optional — inferred from image or ask if style consistency matters)
5. Call the `inpaint_artwork` MCP tool with the parameters
6. Present results clearly:
   - Path to the blended output image
   - Bounding box that was modified (x, y, w, h)
   - Number of variants generated (if multiple)
   - Any cultural notes on the inpainted region

## Parameters

| Parameter | Required | Description |
|-----------|----------|-------------|
| `image_path` | Yes | Path to the source artwork to inpaint |
| `region` | Yes | NL description ("the sky") or coordinates [x, y, w, h] |
| `instruction` | Yes | What to paint in the region |
| `tradition` | No | Cultural tradition to guide style consistency |

## Example

User: "Fix the sky in this painting — it should look more stormy"

Response flow:
1. Call `inpaint_artwork(image_path="landscape.jpg", region="the sky in the upper portion", instruction="replace with dramatic stormy clouds, dark and heavy", tradition="chinese_xieyi")`
2. Show the blended output image path
3. Confirm the bounding box that was modified
4. Note any cultural considerations (e.g., "stormy atmosphere aligns with xieyi's 气韵 — emotional atmosphere principle")

## Tips

- Describe the region in plain language: "the face", "the lower right corner", "the background behind the figure"
- Be specific in the instruction: "replace with red flowers in full bloom" works better than "fix the flowers"
- If style consistency is important, always specify the tradition so inpainting matches the original cultural register
