# 128px Survivability & Prompt Engineering Rules

Chat emojis render at **28×28px to 48×48px** in real conversation feeds. Detailed illustrations that look great at 1024px turn into unreadable mud at 28px.

## 5 Design Rules for Small-Canvas Legibility

1. **Head-and-Shoulders Crop (80% Frame Fill)**: Keep the face and hands filling 75–85% of the square canvas. Avoid full-body scenes or complex backgrounds.
2. **Bold Silhouette & Thick Lineart**: Specify `thick bold dark lineart` and `clean cel-shaded vector colors`. Fine hair strands and photorealistic noise break GIF quantization palettes.
3. **White Die-Cut Sticker Outline**: Add a `2–4px crisp white die-cut sticker border` so dark character edges never vanish into Discord or Twitch dark mode.
4. **Single Unmistakable Emotion**: Exaggerate eyes, brows, mouth, and a single comic cue (waterfall tears, sparkle aura, sweat drop, red steam, oversized thumbs up).
5. **No Small Text**: Unless it is a 2–3 letter bold meme word (`GG`, `NO`, `LUL`, `OK`), omit text entirely—anything smaller than 18px at 128×128 becomes illegible at 28×28.

## Reusable Prompt Formula

```text
Cute chibi Twitch/Discord emote of [CHARACTER DESCRIPTION], [EXAGGERATED EMOTION + SINGLE PROP], head and shoulders close-up filling 80% of square frame, bold dark lineart, crisp flat cel-shaded colors, clean white die-cut sticker outline, isolated on pure transparent background, ultra-legible at 28px and 128px, no tiny text
```

## Preventing the 2x GIF Speedup Glitch (GCE Delay Compensation)

When reducing an animated GIF from 80 frames down to 40 frames to meet Slack's 50-frame or Twitch's 60-frame limit:
- Every dropped frame `i` has a Graphic Control Extension delay `d_i` (in centiseconds).
- Add `d_i` onto the immediately preceding surviving frame `k`: `new_delay[k] += d_i`.
- Never drop frames without recalculating cumulative delays, or the animation will loop at 2x–3x turbo speed.
