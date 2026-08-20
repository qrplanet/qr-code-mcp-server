# Prompt: Create a dynamic QR Code

Use this once your MCP client is connected (see [setup guides](../README.md#setup-guides)).

## Basic

```
Create a dynamic QR Code that points to https://example.com and name it "Storefront Sign".
```

## With a folder and tags

```
Create a dynamic QR Code for https://example.com/summer-sale, put it in the
"Marketing" folder, and tag it "summer-2026" and "in-store".
```

## With custom design

```
Create a dynamic QR Code linking to https://example.com, then design it with
our brand color #1A73E8, rounded corners, and our logo centered in the code.
```

## What happens

The agent calls `create_qr_code`, resolving or creating the folder first if needed. If you asked for tags, it applies them with `update_qr_code_tags`; if you asked for styling, it calls `design_qr_code`. The agent then returns the QR Code's code, short URL, and image URL. Save the returned code if you plan to update or check stats on this QR Code later — most follow-up tools operate on that code, not the destination URL.
