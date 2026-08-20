# Connect Mistral Vibe to the QR Planet MCP Server

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it.

## 2. Edit your Vibe config

**File path:** `~/.vibe/config.toml`

By default Vibe ships with an empty `mcp_servers = []` line. Comment that out, then add a `[[mcp_servers]]` block. Replace `YOUR_DOMAIN`, `YOUR_KEY_ID`, and `YOUR_SECRET` with your real QR Planet API key from step 1.

```toml
# mcp_servers = []

[[mcp_servers]]
name = "qrplanet-mcp"
transport = "http"
url = "https://api.qrplanet.com/mcp"
headers = { "Authorization" = "Bearer secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET", "X-Client-Id" = "mistral-vibe" }
```

## 3. Verify the connection

Restart Vibe and confirm `qrplanet-mcp` is listed as a connected MCP server. Ask it to list available tools and check for QR Planet tools like `create_qr_code` or `list_bcards`.

## 4. Try it

```
Create a business card QR Code for Jane Doe, Sales Director, jane@example.com.
```

See [prompts/](../prompts/) for more examples.

## Notes

- If you forget to comment out `mcp_servers = []`, the `[[mcp_servers]]` block will be ignored or cause a config error — this is the most common setup mistake.
- `transport = "http"` is required for QR Planet's remote server; don't use a `command`/stdio transport for it.
- Config syntax can change between Vibe releases — verify against Mistral's own docs if this stops working.
