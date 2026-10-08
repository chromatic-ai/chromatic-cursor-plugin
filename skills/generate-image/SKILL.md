---
name: generate-image
description: Make or edit a picture in Chromatic. Use when the person wants a picture, a poster, a still, or a change to an existing image.
---

# Generate image

1. On the first call in a chat, omit `canvasId`. The tool creates one canvas and returns its id.
2. On every later call in that same chat, pass that same `canvasId`. Do not open a second canvas.
3. Call `get_model_schema` before a model you have not used. Paid accounts usually use Nano Banana 2.
4. A file already on this canvas is a node id from `generate_image`, `generate_video`, `upload_asset`, or `list_generations`. Do not upload it again. A photo that only exists in the chat goes through `upload_asset` with a public https URL, then you use the returned node id.
5. Call `generate_image`. A new still passes no `referenceNodeIds`. A change to a still passes `referenceNodeIds`.
6. Call `get_job` with the job id until the file URL is there. If it is still running, wait about 20 seconds and call `get_job` again.

`create` spends credits and starts the job. `review` only places the shot.

Do not ask for the canvas document. The tools return a file URL, a job id, and a canvas id.

At most five MCP jobs run at once. MCP spend stops at 2000 cents per UTC day.
