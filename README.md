
# QR Planet QR Code MCP Server

Connect Claude Code, ChatGPT Codex, OpenCode, Google Antigravity/Gemini, Mistral Vibe, and other MCP-compatible clients to QR Planet so AI agents can create, update, design, route, and analyze dynamic QR Codes.

This repository is **documentation, configuration examples, and prompt examples** for the QR Planet QR Code MCP Server. It does not contain the MCP server's source code. The server itself is hosted and operated by QR Planet at:

```text
https://api.qrplanet.com/mcp
```

## What is this?

The QR Planet QR Code MCP Server exposes QR Planet's platform to AI coding agents and assistants over the [Model Context Protocol](https://modelcontextprotocol.io) (MCP).

Once connected, an MCP-compatible client can call QR Planet tools directly from a chat or agent session, without manually clicking through the dashboard.

## What you can do with the QR Planet MCP Server

Through the connected tools, an AI agent can:

- Create, update, list, and delete dynamic QR Codes
- Design custom QR Codes with colors, logos, shapes, frames, and templates
- Route QR Codes by country, geofence, geo-region, or language
- Manage folders, tags, and digital business cards
- Create and manage GS1 Digital Links and routing rules
- Issue vouchers and inspect coupon statistics
- Retrieve scan statistics, leads, and folder-level analytics
- and much more...

See [Available MCP tools](#available-mcp-tools) below for the current tool overview.

## Quick start

1. **Get an API key.** Log into your QR Planet account at [qrplanet.com/premium/login](https://qrplanet.com/premium/login), go to **API settings**, open the **API v2** section, and click **Show Secret API Key**.

2. **Copy your API key.** QR Planet keys look like this:

   ```text
   secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET
   ```

   Some read-only use cases may use a `public:` key instead.

3. **Add the MCP server to your client.** All clients connect to the same remote MCP endpoint:

   ```text
   https://api.qrplanet.com/mcp
   ```

4. **Authenticate with your API key.** Most clients use an HTTP header:

   ```text
   Authorization: Bearer YOUR_QR_PLANET_API_KEY
   ```

5. **Try a prompt.**

   ```text
   Create a dynamic QR Code that points to https://example.com and put it in a folder called Marketing.
   ```

Exact commands and flags can change as MCP clients update their support. If something in these docs looks stale, verify against your client's own documentation and the official QR Planet MCP page: [qrplanet.com/qr-code-mcp](https://qrplanet.com/qr-code-mcp).

## Setup guides

Each guide covers how to get an API key, how to add the MCP server for that client, and how to verify the connection.

| Client | Guide |
|---|---|
| Claude Code | `client-setup/claude-code.md` |
| Claude Desktop / Cowork / claude.ai | `client-setup/claude-apps.md` |
| ChatGPT web connector | `client-setup/chatgpt-web.md` |
| ChatGPT Codex CLI / IDE extension | `client-setup/chatgpt-codex.md` |
| OpenCode | `client-setup/opencode.md` |
| Google Antigravity / Gemini | `client-setup/google-gemini-antigravity.md` |
| Mistral Vibe Code CLI | `client-setup/mistral-vibe.md` |
| Mistral Work / Studio connector | `client-setup/mistral-work-studio.md` |

More client guides will be added as setup steps are confirmed.

## Example prompts

Ready-to-use prompts for common tasks live in `prompts/`:

- [Create a dynamic QR Code](prompts/create-dynamic-qr-code.md)
- [Create a branded QR Code design](prompts/create-branded-qr-code-design.md)
- [Create a static QR Code](prompts/create-static-qr-code.md)
- [Update a campaign's destination URL](prompts/update-campaign-url.md)
- [Route QR Code targets by location or language](prompts/route-qr-code-targets.md)
- [Manage QR Code tags](prompts/manage-qr-code-tags.md)
- [Manage QR Code folders](prompts/manage-folders.md)
- [Analyze scan statistics](prompts/analyze-scan-stats.md)
- [Export QR Code leads](prompts/export-qr-code-leads.md)
- [Create a digital business card](prompts/create-digital-business-card.md)
- [Create a GS1 Digital Link QR Code](prompts/create-gs1-digital-link.md)
- [Issue a coupon voucher](prompts/issue-coupon-voucher.md)
- [Update App Store QR Code targets](prompts/update-app-store-qr-code.md)

## Available MCP tools

The QR Planet MCP Server currently exposes the following tools. Tool availability may depend on your QR Planet API key permissions. This also may change over time. The single source of truth is of course the live MCP `tools/list` response from your client is authoritative. 


### QR Codes

- `create_qr_code` — Create a dynamic QR Code
- `list_qr_codes` — List QR Codes
- `get_qr_code` — Get a QR Code by code
- `update_qr_code` — Update QR Code fields such as target URL, title, metadata, folder, or settings
- `delete_qr_code` — Delete a QR Code
- `get_qr_code_stats` — Get scan statistics for a QR Code
- `reset_qr_code_stats` — Reset scan statistics for a QR Code
- `get_qr_code_leads` — Retrieve leads collected through a QR Code landing page

### QR Code Tags

- `get_qr_code_tags` — Get tags assigned to a QR Code
- `update_qr_code_tags` — Replace or update tags on a QR Code
- `delete_qr_code_tags` — Remove all tags from a QR Code

### QR Code Targeting

- `add_qr_code_country_target` — Add a country-specific target URL
- `delete_qr_code_country_target` — Remove a country-specific target
- `add_qr_code_language_target` — Add a language-specific target URL
- `delete_qr_code_language_target` — Remove a language-specific target
- `add_qr_code_geofence_target` — Add a geofence-specific target URL
- `delete_qr_code_geofence_target` — Remove a geofence-specific target
- `add_qr_code_georegion_target` — Add a geo-region-specific target URL
- `delete_qr_code_georegion_target` — Remove a geo-region-specific target

### QR Code Design

- `design_qr_code` — Apply a custom design to an existing dynamic QR Code
- `design_static_qr_code` — Create a designed static QR Code from static content
- `create_designer_template` — Create a reusable QR Code designer template
- `get_designer_template` — Get a designer template by ID
- `list_designer_templates` — List designer templates

### App Store QR Codes

- `update_app_store_qr_code_targets` — Update target URLs for an app store QR Code

### Digital Business Cards

- `create_digital_business_card` — Create a digital business card
- `list_digital_business_cards` — List digital business cards
- `get_digital_business_card` — Get a digital business card by code
- `update_digital_business_card` — Update digital business card fields
- `delete_digital_business_card` — Delete a digital business card
- `upload_digital_business_card_image` — Upload a profile, logo, or background image for a digital business card

### Folders

- `create_folder` — Create a folder
- `list_folders` — List folders
- `get_folder` — Get a folder by ID
- `delete_folder` — Delete a folder
- `get_folder_stats` — Get folder-level scan statistics
- `reset_folder_stats` — Reset folder-level scan statistics

### GS1 Digital Link

- `create_gs1_digital_link` — Create a GS1 Digital Link QR Code
- `create_gs1_digital_link_rule` — Create a routing rule for a GS1 Digital Link QR Code
- `list_gs1_digital_link_rules` — List rules for a GS1 Digital Link QR Code
- `delete_gs1_digital_link_rules` — Delete all rules for a GS1 Digital Link QR Code

### Coupons & Vouchers

- `list_coupons` — List coupons
- `issue_coupon_voucher` — Issue a voucher for a coupon
- `get_coupon_issue_stats` — Get coupon issue statistics
- `get_coupon_redemptions` — Get coupon redemption statistics



## API key and security

Treat your QR Planet API key like a password.

- Never commit it to a repository
- Never paste it into a shared chat
- Never hardcode it in public configuration examples
- Prefer environment variables or your client's secret storage
- Use a `public:` key only when read access is enough
- Use a `secret:` key for flows that create, update, or delete resources
- Rotate keys immediately if one is exposed

Example environment variable:

```bash
export QR_PLANET_API_KEY="secret:YOUR_DOMAIN:YOUR_KEY_ID:YOUR_SECRET"
```

## Troubleshooting

If your MCP client cannot connect:

- Check that the server URL is exactly `https://api.qrplanet.com/mcp`
- Check that the `Authorization` header starts with `Bearer ` if thats the correct mode for your client (see [Setup guides](#setup-guides) )
- Confirm that your API key is valid in QR Planet API settings
- Confirm that your client supports remote MCP servers
- Run your client's MCP tool discovery command and verify that `tools/list` returns QR Planet tools

If authentication fails, generate a fresh API key and update your client configuration.

## Official documentation

This repository supplements the official QR Planet MCP documentation:

[qrplanet.com/qr-code-mcp](https://qrplanet.com/qr-code-mcp)

## License

This repository is licensed under the MIT License. You are free to use, copy, modify, and share the documentation, configuration examples, and prompt examples, subject to the terms of the license.
