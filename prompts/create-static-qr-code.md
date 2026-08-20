# Prompt: Create a static QR Code

Use this when the QR Code should encode content directly instead of redirecting through a dynamic short URL.

## Static URL

```
Create a static QR Code for https://example.com/help with black foreground,
white background, and high error correction.
```

## Static text

```
Create a static QR Code that contains the text "WiFi instructions are at the front desk"
and return the generated image.
```

## Static contact detail

```
Create a static QR Code for the email address support@example.com and make it
ready to download as an image.
```

## What happens

The agent calls `design_static_qr_code` with either `target_url` or `content` plus optional styling fields. Static QR Codes do not use a QR Planet short URL, so they cannot be redirected later with `update_qr_code`.
