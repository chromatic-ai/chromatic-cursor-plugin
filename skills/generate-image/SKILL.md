---
name: generate-image
description: Make or edit a picture in Chromatic. Use when the person wants a picture, a poster, a still, or a change to an existing image.
---

# Generate image

One chat, one canvas. If a call returns a canvas id, pass that id on every later call in this chat. A new chat omits it.

Do not ask for the canvas document. The tools return a file URL, a job id, and a canvas id.

`create` spends credits and starts the job. `review` only places the shot.

At most five MCP jobs run at once. MCP spend stops at 2000 cents per UTC day.

Call `get_model_schema` before using a model you have not used. Paid accounts usually use Nano Banana 2.

A file already on this chat's canvas is a node id from `generate_image`, `generate_video`, `upload_asset`, or `list_generations`. Do not upload that file again.

- A new still: `generate_image`.
- Change a still: `generate_image` with `referenceNodeIds`.
- A photo that only exists in the chat: `upload_asset` with a public https URL, then use the returned node id.
