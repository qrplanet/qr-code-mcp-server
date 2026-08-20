# Connect OpenCode to the QR Planet MCP Server

## 1. Get an API key

Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key** to reveal and copy it. You'll paste this into the OAuth popup in step 3, not into the config file.

## 2. Edit your OpenCode config

**File path:**

- Global: `~/.config/opencode/opencode.json`
- Project-scoped: `opencode.json` in the project root (OpenCode walks up to the nearest Git root)

Open the file (create it if it doesn't exist yet) and add the `mcp.qrplanet-mcp` block below (merge it into the file if it already has other content):

```json
{
  "$schema": "https://opencode.ai/config.json",
  "mcp": {
    "qrplanet-mcp": {
      "type": "remote",
      "url": "https://api.qrplanet.com/mcp",
      "enabled": true,
      "oauth": {
        "clientId": "opencode"
      },
      "scope": "mcp:tools"
    }
  }
}
```

## 3. Authenticate

After saving the config, run:

```
opencode mcp auth qrplanet-mcp
```

An authorization popup opens — paste the Secret API key from step 1 into it. OpenCode stores the resulting credentials outside the config file.

## 4. Verify the connection

Start (or restart) OpenCode and confirm `qrplanet-mcp` shows up as an enabled, connected server. Ask it to list available tools and check for QR Planet tools like `create_qr_code` or `list_folders`.

## 5. Try it

```
List all QR Codes in the "Marketing" folder and show their scan counts.
```

See [prompts/](../prompts/) for more examples.

## Notes

- `type: "local"` is for servers you run yourself with a command; QR Planet's MCP server is remote, so use `type: "remote"` with a `url`.
- Set `"enabled": false` to temporarily disable the server without deleting the config block.
- If `opencode mcp auth` fails, double-check the server URL and that your QR Planet account has API access enabled.
