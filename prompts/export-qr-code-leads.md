# Prompt: Export QR Code leads

Use this when QR Code landing pages collect leads and you want to review or export them.

## Summarize leads

```
Show the leads captured by the QR Code named "Trade Show Booth" this month and
summarize them by company.
```

## Export leads

```
Export the leads for the QR Code with code <code> as CSV.
```

## Filter by referrer

```
Get leads for the QR Code named "Partner Landing Page" where the referrer is
https://partner.example.com.
```

## What happens

The agent resolves names to QR Code codes with `list_qr_codes`, then calls `get_qr_code_leads`. The leads endpoint supports JSON by default and can export CSV or XLSX when the requested format is supported.
