---
name: generate-video
description: Make a clip in Chromatic. Use when the person wants a video, a clip from one frame, or several pictures in one clip.
---

# Generate video

One chat, one canvas. If a call returns a canvas id, pass that id on every later call in this chat. A new chat omits it.

Do not ask for the canvas document. The tools return a file URL, a job id, and a canvas id.

`create` spends credits and starts the job. `review` only places the shot.

At most five MCP jobs run at once. MCP spend stops at 2000 cents per UTC day.

Call `get_model_schema` before using a model you have not used. Paid accounts usually use MiniMax H3.

A file already on this chat's canvas is a node id from `generate_image`, `generate_video`, `upload_asset`, or `list_generations`. Do not upload that file again.

- A new clip: `generate_video`.
- One still becomes a clip: `generate_video` with `parentNodeId`. That is the first frame.
- Several stills in one clip: `generate_video` with `referenceNodeIds`, in order. Call `get_model_schema` first. The modes list must include `reference-to-video`. MiniMax H3 can. Do not also pass `parentNodeId`.
- A photo that only exists in the chat: `upload_asset` with a public https URL, then use the returned node id.

Video and audio references are not part of this plug yet. Several pictures in one clip means pictures only.
