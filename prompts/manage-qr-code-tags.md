# Prompt: Manage QR Code tags

Use this to organize QR Codes for campaigns, reporting, and bulk updates.

## Add tags

```
Add the tags "summer-2026" and "in-store" to the QR Code named "Storefront Sign".
```

## Replace campaign tags

```
For every QR Code tagged "summer-2026", remove "summer-2026" and add "fall-2026".
```

## Clear tags

```
Remove all tags from the QR Code with code <code>.
```

## What happens

The agent uses `list_qr_codes` to find QR Codes by title or tag, checks existing tags with `get_qr_code_tags` when needed, applies changes with `update_qr_code_tags`, and clears all tags with `delete_qr_code_tags`.
