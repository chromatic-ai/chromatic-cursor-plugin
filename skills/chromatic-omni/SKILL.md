---
name: chromatic-omni
description: Choose the right Chromatic input. Use when a shot should edit an existing image, start a video from one frame, or combine several pictures in one clip.
---

# Chromatic inputs

A file already on this chat's canvas is a node id from `generate_image`, `generate_video`, `upload_asset`, or `list_generations`. Do not upload that file again.

- Change a still: `generate_image` with `referenceNodeIds`.
- One still becomes a clip: `generate_video` with `parentNodeId`. That is the first frame.
- Several stills in one clip (Omni): `generate_video` with `referenceNodeIds`, in order. Call `get_model_schema` first. The modes list must include `reference-to-video`. MiniMax H3 can. Do not also pass `parentNodeId`.
- A photo that only exists in the chat: `upload_asset` with a public https URL, then use the returned node id.

Video and audio references are not part of this plug yet. Omni here is pictures only.
