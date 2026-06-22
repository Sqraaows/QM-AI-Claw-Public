---
name: video-frames
description: Extract frames or short clips from videos using ffmpeg. Use when extracting thumbnails, analyzing video content, or creating preview images.
homepage: https://ffmpeg.org
metadata: {"clawdbot":{"emoji":"🎞️","requires":{"bins":["ffmpeg"]},"install":[{"id":"brew","kind":"brew","formula":"ffmpeg","bins":["ffmpeg"],"label":"Install ffmpeg (brew)"}]}}
---

# Video Frames (ffmpeg)

Extract a single frame from a video, or create quick thumbnails for inspection.

## Quick start

First frame:
```bash
ffmpeg -i /path/to/video.mp4 -vf "select=eq(n\,0)" -vframes 1 /tmp/frame.jpg
```

At a timestamp:
```bash
ffmpeg -i /path/to/video.mp4 -ss 00:00:10 -vframes 1 /tmp/frame-10s.jpg
```

## Notes

- Prefer timestamp for "what is happening around here?"
- Use `.jpg` for quick share; use `.png` for crisp UI frames
- Requires `ffmpeg` installed