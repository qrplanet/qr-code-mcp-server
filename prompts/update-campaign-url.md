# Prompt: Update a campaign's destination URL

Dynamic QR Codes let you change the destination without reprinting the code. Use this to redirect an existing QR Code to a new URL.

## Basic

```
Update the QR Code named "Storefront Sign" to point to https://example.com/new-promo instead.
```

## By code

```
Update QR Code <code> so it redirects to https://example.com/black-friday.
```

## Bulk-style (agent will loop over list + update)

```
List all QR Codes tagged "summer-2026" and change their destination URL to
https://example.com/fall-sale.
```

## What happens

If you refer to a QR Code by name, the agent first calls `list_qr_codes` to resolve the name to a code, then calls `update_qr_code` with the new `target_url`. Referring to the QR Code by its code directly skips the lookup step and is faster/more reliable for scripted workflows.
