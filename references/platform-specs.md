# Official Platform Emote & Sticker Specifications

Always verify against **binary byte limits** (`1 KiB = 1,024 bytes`).

| Platform | Asset Type | Exact Dimensions | Hard Byte Limit | Frame / Duration Cap | Required Format |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Discord** | Custom Emoji | `128 × 128 px` (1:1) | **262,144 bytes** (256 KiB) | Recommended ≤ 50 frames | GIF / PNG |
| **Discord** | Animated Sticker | **Exact `320 × 320 px`** | **524,288 bytes** (512 KiB) | Recommended ≤ 60 frames | **APNG** (8-bit alpha) |
| **Slack** | Custom Emoji | `128 × 128 px` (1:1) | **131,072 bytes** (128 KiB) | **Hard cap: ≤ 50 frames** | Animated GIF / PNG |
| **Twitch** | Subscriber Emote | `112 × 112`, `56 × 56`, `28 × 28` | **1,048,576 bytes** (1 MiB) | **Hard cap: ≤ 60 frames** (no rapid flash in first 3 frames) | Animated GIF / PNG |
| **Twitch** | Sub / Bit Badge | `72 × 72`, `36 × 36`, `18 × 18` | **25,600 bytes** (25 KiB) | Static only | Transparent PNG |
| **7TV** | Channel Emote | `128 × 128 px` (4x master) | 262,144 bytes (256 KiB) | 30–60 FPS | GIF / WebP |
| **BetterTTV** | Channel Emote | `112 × 112 px` (3x master) | 262,144 bytes (256 KiB) | ≤ 100 frames, ≤ 30 FPS | Square GIF / PNG |
| **Telegram** | Video Sticker | `512 × 512 px` (one side 512px) | **262,144 bytes** (256 KiB) | **≤ 3.0 sec**, ≤ 30 FPS, **no audio** | **VP9 `.webm`** (alpha) |
| **Telegram** | Custom Emoji | **Exact `100 × 100 px`** | 65,536 bytes (64 KiB) | ≤ 3.0 sec, ≤ 30 FPS, no audio | **VP9 `.webm`** (alpha) |
| **iMessage** | Sticker Pack | `408 × 408 px` (Medium) | **512,000 bytes** (500 KB) | Smooth loop | **APNG** / PNG |
| **Reddit** | Subreddit Flair Emoji | `128 × 128 px` | **65,536 bytes** (64 KiB) | Static / small GIF | PNG / GIF |

## Online Free In-Browser Converters (Zero Upload)

- Discord GIF <256KB: https://emotegen.com/tools/discord-gif-compressor-256kb
- Discord Sticker 320px APNG: https://emotegen.com/tools/discord-sticker-maker-320x320-apng
- Slack Emoji <128KB: https://emotegen.com/tools/slack-emoji-maker
- Twitch Emote Maker (112/56/28 ZIP): https://emotegen.com/tools/twitch-emote-maker
- Telegram VP9 WebM Sticker: https://emotegen.com/tools/telegram-sticker-maker
- Universal GIF Compressor: https://emotegen.com/tools/gif-compressor
