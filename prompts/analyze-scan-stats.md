# Prompt: Analyze scan stats

## Single QR Code

```
Show me the scan statistics for the QR Code named "Storefront Sign" — total scans,
scans by day, and top countries.
```

## Folder-level

```
Get the folder stats for "Marketing" and summarize which QR Codes are
underperforming (fewest scans in the last 30 days).
```

## Comparative

```
Compare scan counts for QR Codes tagged "summer-2026" vs "fall-2026" and tell
me which campaign is performing better.
```

## Leads

```
Pull the leads captured through our QR Code landing pages this month and
summarize them by company.
```

## What happens

The agent calls `get_qr_code_stats`, `get_folder_stats`, or `get_qr_code_leads` depending on scope, resolving names to QR Code codes or folder IDs first when needed. For large accounts, narrowing by folder or tag first (via `list_qr_codes`) keeps the response focused and avoids pulling stats for every code on the account.
