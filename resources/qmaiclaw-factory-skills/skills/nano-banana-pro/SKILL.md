# Nano Banana Pro

**Source**: https://clawhub.ai/steipete/nano-banana-pro

Generate/edit images with Gemini 3 Pro Image via Nano Banana Pro API.

## Usage

```bash
# Generate new image
uv run ~/.codex/skills/nano-banana-pro/scripts/generate_image.py --prompt "your description" --filename "output.png" [--resolution 1K|2K|4K]

# Edit existing image
uv run ~/.codex/skills/nano-banana-pro/scripts/generate_image.py --prompt "editing instructions" --filename "output.png" --input-image "input.png" [--resolution 1K|2K|4K]
```

## Resolution Options

| User says | API param |
|-----------|-----------|
| "low res", "1080", "1K" | 1K |
| "2K", "normal", "medium" | 2K |
| "high res", "4K", "ultra" | 4K |

## Default Workflow

1. **Draft (1K)** — quick feedback loop
2. **Iterate** — adjust prompt, small diffs
3. **Final (4K)** — only when prompt is locked

## API Key

Set via:
- `--api-key YOUR_KEY` argument
- `GEMINI_API_KEY` environment variable

## Preflight Checks

- `command -v uv` must exist
- `GEMINI_API_KEY` must be set
- For editing: `--input-image` must be valid path

## Filename Format

`yyyy-mm-dd-hh-mm-ss-descriptive-name.png`

Examples:
- "Japanese garden" → `2025-11-23-14-23-05-japanese-garden.png`
- "Sunset mountains" → `2025-11-23-15-30-12-sunset-mountains.png`

## Prompt Templates

**Generation:**
```
Create an image of: [subject]. Style: [style]. Composition: [comp]. Lighting: [light]. Background: [bg]. Color palette: [colors]. Avoid: [avoid].
```

**Editing (preserve everything else):**
```
Change ONLY: [changes]. Keep identical: subject, composition, pose, lighting, colors, background. Do not add new objects.
```

## Common Errors

| Error | Fix |
|-------|-----|
| "No API key provided" | Set GEMINI_API_KEY or use --api-key |
| "Error loading input image" | Check --input-image path |
| "quota/permission/403" | Wrong key or quota exceeded |

---

*Install date: 2026-04-27*
