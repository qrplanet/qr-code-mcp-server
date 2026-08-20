# Connect Claude Desktop, Cowork, and claude.ai to the QR Planet MCP Server

Claude Desktop, Cowork, and claude.ai all use the same **remote connector** mechanism for a hosted MCP server like QR Planet's — there's no config file to edit, and setting the connector up once makes it available across all three surfaces (Cowork is a mode inside the Desktop app, alongside Chat and Code).

This is a different product and setup flow from **Claude Code** — see [claude-code.md](claude-code.md) if you're looking for the CLI/IDE tool instead.

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it.

## 2. Add the connector

In Claude Desktop (or claude.ai):

1. Go to **Customize → Connectors**.
2. Click the **+** button next to Connectors.
3. Enter a name (e.g. `QR Planet MCP`) and the server URL:
   ```
   https://api.qrplanet.com/mcp
   ```
4. Open **Advanced settings** and enter the OAuth Client ID `claude-apps`, or use this field to pass the Secret API key from step 1 as a Bearer token instead — the exact fields shown here can vary by Claude Desktop version, so use whichever the dialog offers.
5. Click **Add**, then complete the authorization prompt.

## 3. Verify the connection

Open a new chat, switch to Cowork if you want to test task-delegation rather than chat, and ask Claude to list its available tools. Confirm QR Planet tools like `create_qr_code` or `list_qr_codes` show up.

## 4. Try it

```
Create a dynamic QR Code pointing to https://example.com and name it "Storefront Sign".
```

See [prompts/](../prompts/) for more examples.

## Notes

- Remote connectors added this way run from Anthropic's cloud infrastructure, not your local machine, and work across Claude Desktop, Cowork, claude.ai, and the mobile apps once added.
- Free plan accounts are limited to one custom connector — if QR Planet doesn't show up, check you haven't hit that limit.
- This guide uses the combined Claude Desktop, Cowork, and claude.ai connector flow. If a working Claude UI shows a different field or client ID, follow the working UI flow.
- If you're instead running a local/stdio MCP server, that uses a separate mechanism (`claude_desktop_config.json`, under `mcpServers`) — QR Planet's server is remote, so the connector flow above is what you want.
