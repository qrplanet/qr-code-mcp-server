# Connect ChatGPT Web to the QR Planet MCP Server

This guide covers ChatGPT's web connector/app setup. If you are configuring Codex CLI or the Codex IDE extension, use [chatgpt-codex.md](chatgpt-codex.md) instead.

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it.

## 2. Enable Developer Mode

In ChatGPT, open **Settings**, go to **Apps**, open **Advanced settings**, and enable **Developer Mode**.

Depending on your workspace plan and role, Developer Mode may need to be enabled by a workspace admin first.

## 3. Create the app

Create a new custom app/connector and configure it with:

- **Name:** `QR Planet MCP` or another name you prefer
- **Connection:** `Server URL`
- **Server URL:** `https://api.qrplanet.com/mcp`
- **Authentication:** `Access token / API key`
- **Header scheme:** `Bearer`

Read and accept the app/connector confirmation, then create the app.

## 4. Connect with your API key

When ChatGPT asks for the token, paste the Secret API key from step 1. ChatGPT should scan the server tools after the connection is authorized.

## 5. Verify the connection

Start a new chat, select or reference the QR Planet app, and ask ChatGPT to list available tools. Confirm QR Planet tools like `create_qr_code` or `list_qr_codes` show up.

## 6. Try it

```
Create a dynamic QR Code pointing to https://example.com and name it "Storefront Sign".
```

See [prompts/](../prompts/) for more examples.

## Notes

- ChatGPT web custom MCP apps are different from Codex CLI / IDE MCP config.
- This guide documents the token-header custom app flow because ChatGPT connector UI support can differ by workspace and release.
- ChatGPT custom connector availability and Developer Mode controls depend on your ChatGPT workspace plan and role.
