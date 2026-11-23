# Emote Craft Skill

An open-source [Agent Skill](https://agentskills.io/specification) for **Claude Code, Cursor, Windsurf, and Codex** containing exact platform upload specs, 128px prompt engineering rules, and GIF delay-compensation guidelines for Discord, Twitch, Slack, Telegram, 7TV, BTTV, iMessage, and Reddit.

## Install via `skills.sh`

```bash
npx skills add gaoshan111/emote-craft-skill
```

## Optional: Pair with the Free EmoteGen MCP Server

Add the zero-auth Streamable HTTP MCP endpoint to Claude Desktop, Cursor, or Windsurf:

```json
{
  "mcpServers": {
    "emotegen": {
      "url": "https://emotegen.com/api/mcp"
    }
  }
}
```

Available free MCP tools:
- `get_platform_specs` — Exact dimensions, binary byte limits, frame caps, and formats across 10 platforms.
- `validate_emote_asset` — Validate asset dimensions, byte weight, frame count, and format before uploading.

## License

MIT — maintained by [EmoteGen](https://emotegen.com).
