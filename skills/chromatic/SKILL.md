---
name: chromatic
description: Make images and video in Chromatic from chat. Use when the person wants a picture, an edit, or a clip on their Chromatic account.
---

# Chromatic

One chat, one canvas. If a call returns a canvas id, pass that id on every later call in this chat. A new chat omits it.

Do not ask for the canvas document. The tools return a file URL, a job id, and a canvas id.

Call `get_model_schema` before using a model you have not used. Paid accounts usually use Nano Banana 2 for images and MiniMax H3 for video.

`create` spends credits and starts the job. `review` only places the shot.

At most five MCP jobs run at once. MCP spend stops at 2000 cents per UTC day.
