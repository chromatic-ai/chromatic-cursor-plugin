---
name: generate-video
description: Make a clip in Chromatic. Use when the person wants a video, a clip from one frame, or several pictures in one clip.
---

# Generate video

1. On the first call in a chat, omit `canvasId`. The tool creates one canvas and returns its id.
2. On every later call in that same chat, pass that same `canvasId`. Do not open a second canvas.
3. Call `get_model_schema` before a model you have not used. Paid accounts usually use MiniMax H3.
4. A file already on this canvas is a node id from `generate_image`, `generate_video`, `upload_asset`, or `list_generations`. Do not upload it again. A photo that only exists in the chat goes through `upload_asset` with a public https URL, then you use the returned node id.
5. Call `generate_video` in one of these ways:
   - A new clip: no `parentNodeId` and no `referenceNodeIds`.
   - One still becomes the clip: pass `parentNodeId` only. That image is the first frame.
   - Several stills in one clip: pass `referenceNodeIds` in order. The model schema must include `reference-to-video`. MiniMax H3 can. Do not also pass `parentNodeId`.
6. Call `get_job` with the job id until the file URL is there. If it is still running, wait about 20 seconds and call `get_job` again.

`create` spends credits and starts the job. `review` only places the shot.

Do not ask for the canvas document. The tools return a file URL, a job id, and a canvas id.

Do not pass both `parentNodeId` and `referenceNodeIds`. Video and audio references are not part of this plug yet. Several pictures in one clip means pictures only.

At most five MCP jobs run at once. MCP spend stops at 2000 cents per UTC day.
