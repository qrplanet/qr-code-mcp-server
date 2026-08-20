# Connect Mistral Work / Studio to the QR Planet MCP Server

This guide covers Mistral Work / Studio custom MCP connectors. If you are configuring the Vibe Code CLI with `~/.vibe/config.toml`, use [mistral-vibe.md](mistral-vibe.md) instead.

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it.

## 2. Add a custom MCP connector

Log into Mistral, switch to **Studio**, open **Connectors**, and add a new connector.

Choose the **Custom MCP Connector** tab and fill out:

- **Title / Connector name:** `QR Planet MCP` or another name you prefer
- **Server / Server URL:** `https://api.qrplanet.com/mcp`
- **Authentication Method:** `API Token Authentication`
- **Authorization header value:** choose `Bearer` and paste your QR Planet API key

Create the connector.

## 3. Verify the connection

Confirm the new connector is listed as connected. Ask Mistral to list available tools and check for QR Planet tools like `create_qr_code` or `list_bcards`.

## 4. Try it

```
Create a business card QR Code for Jane Doe, Sales Director, jane@example.com.
```

See [prompts/](../prompts/) for more examples.

## Notes

- QR Planet's MCP server is remote; use the custom MCP connector flow with the HTTP server URL above.
- Mistral Work / Studio connectors are separate from Vibe Code CLI MCP server config.
- This guide uses API token authentication. Mistral Work / Studio connectors are separate from the Vibe Code CLI setup.
