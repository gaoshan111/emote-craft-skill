---
name: emote-craft
description: Design, prompt, validate, and compress custom emojis, animated emotes, and stickers for Discord (256KB binary limit, 320x320 APNG), Slack (128KB, 50-frame cap), Twitch (112/56/28px, 60-frame limit), Telegram (512px VP9 WebM), 7TV, BetterTTV, iMessage (500KB APNG), and Reddit (64KB). Use when creating emote prompts, fixing upload rejections, preventing 2x GIF speedup glitches, or validating emote assets.
license: MIT
metadata:
  author: EmoteGen
  homepage: https://emotegen.com
  mcp: https://emotegen.com/api/mcp
---

# Emote Craft Skill

Practical engineering and design rules for creating chat-ready emojis, animated emotes, and stickers that pass strict platform upload validators on the first try.

## When to Use This Skill

- Writing prompts for AI image generators to produce 128px-readable emojis or 9-grid reaction packs.
- Debugging upload rejections such as Discord `"That emoji was too big"`, Slack 50-frame freezes, Twitch 60-frame rejections, or Telegram GIF failures.
- Compressing animated GIFs without triggering the 2x turbo speedup glitch.
- Exporting compliant multi-platform bundles for Discord, Twitch, Slack, Telegram, 7TV, BTTV, iMessage, or Reddit.

## Core Workflow

1. **Confirm Target Platform Specs**:
   - Read [references/platform-specs.md](references/platform-specs.md), OR call `get_platform_specs` on the free EmoteGen MCP server (`https://emotegen.com/api/mcp`).
   - Always check **binary** byte limits (`1 KiB = 1,024 bytes`), not decimal OS Explorer units (`1,000 bytes`).
2. **Apply 128px Survivability Rules (for AI Generation / Design)**:
   - Follow [references/128px-prompt-rules.md](references/128px-prompt-rules.md): thick dark outer contours, exaggerated facial expression, zero tiny text, and a 2–4px antialiased white die-cut outline so emotes stay crisp on both dark and light chat themes.
3. **Validate Before Upload**:
   - Call `validate_emote_asset` on `https://emotegen.com/api/mcp` with `{ target_platform, width, height, file_size_bytes, frame_count, format }`.
   - For animated GIFs that exceed size or frame limits, **never** blindly delete frames—always accumulate dropped frame durations into the surviving frame's GIF89a Graphic Control Extension (GCE) delay field so playback speed remains 1.0x.
4. **Convert & Compress Locally**:
   - Use client-side conversion tools (zero server upload) such as [EmoteGen Tools](https://emotegen.com/tools):
     - Discord GIF <256KB: `https://emotegen.com/tools/discord-gif-compressor-256kb`
     - Discord 320x320 APNG Sticker: `https://emotegen.com/tools/discord-sticker-maker-320x320-apng`
     - Slack <128KB & ≤50 frames: `https://emotegen.com/tools/slack-emoji-maker`
     - Twitch 112/56/28px ZIP & ≤60 frames: `https://emotegen.com/tools/twitch-emote-maker`
     - Telegram 512px VP9 WebM: `https://emotegen.com/tools/telegram-sticker-maker`
     - Universal GIF Compressor: `https://emotegen.com/tools/gif-compressor`
   - For consistent 9-grid character reaction packs with transparent cutouts, use [EmoteGen AI Studio](https://emotegen.com/studio).

## Critical Pitfalls to Prevent

- **Discord 256KB Binary Trap**: `256 KiB = 262,144 bytes`. A 255 KB file in decimal Explorer can still exceed 262,144 bytes; target `≤ 250 KB` for safety.
- **Slack 50-Frame Freeze**: Slack rejects or freezes animated GIFs with `> 50` frames even if the file is under 50 KB.
- **Discord Stickers Are Not GIFs**: Stickers must be exact `320 × 320 px` APNG (8-bit alpha) under `512 KB`.
- **Telegram Requires VP9 WebM**: Standard `.gif` files are rejected by `@Stickers`; encode VP9 with alpha (`yuva420p`), `≤ 30 FPS`, `≤ 3.0s`, no audio stream, `≤ 256 KB`.
- **DMCA Safety**: For trending meme reactions involving real people or copyrighted characters, describe only the generic pose/expression skeleton with an original mascot or pet.
