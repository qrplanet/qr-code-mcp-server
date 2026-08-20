# Connect Claude Code to the QR Planet MCP Server

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it.

## 2. Add the server

**File path:** `.mcp.json` in your project root (project scope — shareable with your team via version control).

Use the CLI to add it:

```
claude mcp add --transport http qrplanet-mcp https://api.qrplanet.com/mcp \
  --scope project \
  -H "Authorization: Bearer secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET" \
  -H "X-Client-Id: claude-code"
```

This creates or updates `.mcp.json` with:

```json
{
  "mcpServers": {
    "qrplanet-mcp": {
      "type": "http",
      "url": "https://api.qrplanet.com/mcp",
      "headers": {
        "Authorization": "Bearer secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET",
        "X-Client-Id": "claude-code"
      }
    }
  }
}
```

If you'd rather keep the server private to yourself instead of sharing it via `.mcp.json`, use one of these scopes instead — both are stored in `~/.claude.json`, not `.mcp.json`:

- **Local** (default, current project only): drop `--scope project` entirely.
- **User** (all your projects, on this machine):
  ```
  claude mcp add --transport http qrplanet-mcp https://api.qrplanet.com/mcp \
    --scope user \
    -H "Authorization: Bearer secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET" \
    -H "X-Client-Id: claude-code"
  ```

## 3. Approve the server

Project-scoped servers from `.mcp.json` require one-time approval. Run `claude` interactively in the project and approve `qrplanet-mcp` when prompted. To review approvals later, run `claude mcp list` (pending servers show as `⏸ Pending approval`) or reset choices with `claude mcp reset-project-choices`.

## 4. Verify the connection

```
claude mcp get qrplanet-mcp
```

Confirms the server, its scope, and connection status. Ask Claude to list its available tools and check for QR Planet tools like `create_qr_code` or `list_qr_codes`.

## 5. Try it

```
Create a dynamic QR Code pointing to https://example.com and name it "Storefront Sign".
```

See [prompts/](../prompts/) for more examples.

## Notes

- Don't commit `.mcp.json` with a real API key in it — either keep the server at `local`/`user` scope (stored outside the project, in `~/.claude.json`), or use `${VAR}` environment variable expansion in `.mcp.json` so the committed file has no secret in it. See [API key and security](../README.md#api-key-and-security).
- `.mcp.json` is meant to be checked into version control for team-shared servers — if you go this route, use environment variable expansion, not a hardcoded key.
- Use the Bearer-token setup above if it works in your Claude Code version. MCP client OAuth support varies by release, so don't switch a working setup unless your client specifically requires it.
- Claude Code is a different product from Claude Desktop/Cowork/claude.ai — see [claude-apps.md](claude-apps.md) if you're looking for that setup instead.
