# Connect ChatGPT Codex to the QR Planet MCP Server

Applies to the Codex CLI and the Codex IDE extension (they share the same config file).

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it. Use the `secret:` key if you want Codex to be able to create/update/delete QR Codes, or a `public:` key for read-only access.

## 2. Edit your Codex config

**File path:**

- Global: `~/.codex/config.toml`
- Project-scoped (trusted projects only): `.codex/config.toml`

Open the file (create it if it doesn't exist yet) and add a `[mcp_servers.qrplanet-mcp]` table anywhere in the file. Replace `YOUR_DOMAIN`, `YOUR_KEY_ID`, and `YOUR_SECRET` with your real QR Planet API key from step 1.

```toml
[mcp_servers.qrplanet-mcp]
url = "https://api.qrplanet.com/mcp"
http_headers = { "Authorization" = "Bearer secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET", "X-Client-Id" = "chatgpt-codex" }
```

## 3. Verify the connection

Restart Codex (or the current session) and confirm the server is listed as connected. In the Codex CLI you can inspect configured servers with:

```
codex mcp
```

Ask Codex to list its available tools and confirm QR Planet's tools (e.g. `create_qr_code`, `list_qr_codes`) show up.

## 4. Try it

```
Create a dynamic QR Code pointing to https://example.com and name it "Storefront Sign".
```

See [prompts/](../prompts/) for more examples.

## Notes

- Codex reads MCP config from `config.toml`, not JSON — don't copy JSON snippets from other clients verbatim.
- If your organization enforces trusted-project rules, project-scoped `.codex/config.toml` may require the project to be marked trusted before Codex will load it.
- Command names and config keys can change between Codex releases — if `mcp_servers` stops working, check the current syntax in Codex's own docs.
