# Prompt: Update App Store QR Code targets

Use this for App Store QR Codes that need platform-specific target URLs.

## Update app store targets

```
Update the App Store QR Code named "Mobile App Download" with Google Play,
Apple App Store, Huawei AppGallery, Amazon Appstore, and fallback URLs.
```

## Country-specific app target

```
For the App Store QR Code with code <code>, set the Austria-specific fallback
URL to https://example.com/at/app.
```

## What happens

The agent resolves names to QR Code codes with `list_qr_codes`, then calls `update_app_store_qr_code_targets` with platform URLs such as `target_url_google_playstore`, `target_url_apple_appstore`, `target_url_huawei_appgallery`, `target_url_amazon_appstore`, and `target_url_fallback`.
