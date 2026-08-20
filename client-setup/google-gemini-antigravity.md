# Connect Google Antigravity / Gemini to the QR Planet MCP Server

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it.

## 2. Edit your MCP config

**File path:**

- Global: `~/.gemini/config/mcp_config.json`
- Project/repo-local: `.agents/mcp_config.json`

Open the file (create it if it doesn't exist yet) and add the `mcpServers.qrplanet-mcp` block below (merge it into the file if it already has other servers configured). Replace `YOUR_DOMAIN`, `YOUR_KEY_ID`, and `YOUR_SECRET` with your real QR Planet API key from step 1.

```json
{
  "mcpServers": {
    "qrplanet-mcp": {
      "serverUrl": "https://api.qrplanet.com/mcp",
      "oauth": {
        "clientId": "google-gemini"
      },
      "headers": {
        "Authorization": "Bearer secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET",
        "X-Client-Id": "google-gemini"
      }
    }
  }
}
```

## 3. Verify the connection

Restart the client and confirm `qrplanet-mcp` appears as a connected server. Ask it to list available tools and check for QR Planet tools like `create_qr_code` or `get_qr_code_stats`.

## 4. Try it

```
Design a QR Code with our brand colors that links to https://example.com/promo.
```

See [prompts/](../prompts/) for more examples.

## Notes

- Prefer the project-local `.agents/mcp_config.json` when you only want QR Planet tools available inside a specific repo.
- The `oauth.clientId` field identifies the connecting client to QR Planet; you can also authenticate purely via the `Authorization` header if your setup doesn't use OAuth.
- Include `X-Client-Id: google-gemini` so QR Planet can identify the connecting client.
- Config paths and field names can shift between Gemini/Antigravity releases — verify against the client's own MCP docs if this stops working.
