# Troubleshooting

## Server doesn't show up / client says "not connected"

- Confirm the config file is in the right location and right format for your client (JSON vs TOML — see [client-setup/](client-setup/)).
- Restart the client fully after editing config. Most MCP clients only read server config on startup.
- Check for JSON/TOML syntax errors (trailing commas, unmatched braces/brackets). A malformed config often fails silently or drops just the broken server.

## Authentication errors (401 / 403)

- Verify the API key format: `secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET` or `public:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET`. A missing segment or stray whitespace will fail auth.
- `public:` keys are read-only. If you're calling a tool that creates, updates, or deletes something (e.g. `create_qr_code`, `delete_qr_code`), you need a `secret:` key.
- If your client uses OAuth (Antigravity/Gemini, OpenCode), make sure you completed the OAuth flow — a header-only key won't satisfy an OAuth-configured server, and vice versa.
- Confirm the key hasn't been rotated or revoked in your QR Planet account.

## Tools don't appear in the client's tool list

- Some clients cache the tool list per session — start a fresh session after connecting.
- Confirm the server is actually enabled (`"enabled": true` in OpenCode, no commented-out block in Vibe's `config.toml`).
- Ask the client explicitly: "List your available MCP tools" — some UIs hide the full list until asked.

## Requests succeed but return unexpected data

- Double check you're pointing at the right QR Code / folder ID — most QR Planet write tools operate on an ID returned from a prior `create_*` or `list_*` call, not a human-readable name.
- Rate limits or account plan limits can cause partial failures; check your QR Planet account dashboard for plan limits if a create/update call is rejected.

## Still stuck

- Re-check the exact config syntax against the client's own MCP documentation — client-side config formats change over time and may have moved since these docs were written.
- Check the official QR Planet MCP page for updates: [qrplanet.com/qr-code-mcp](https://qrplanet.com/qr-code-mcp).
- Open an issue on this repo if the docs themselves are wrong or out of date.
