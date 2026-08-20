# Prompt: Route QR Code targets by location or language

Use this when one dynamic QR Code should redirect to different URLs depending on country, language, geofence, or geo-region.

## Country targeting

```
For the QR Code named "Storefront Sign", send scans from Austria to
https://example.com/at and scans from Germany to https://example.com/de.
```

## Language targeting

```
For the QR Code with code <code>, send German-language devices to
https://example.com/de and English-language devices to https://example.com/en.
```

## Remove targeting

```
Remove the German language target from the QR Code named "Storefront Sign".
```

## What happens

The agent resolves names to QR Code codes with `list_qr_codes`, then calls `add_qr_code_country_target`, `add_qr_code_language_target`, `add_qr_code_geofence_target`, or `add_qr_code_georegion_target`. To remove routing rules, it calls the matching delete tool such as `delete_qr_code_country_target` or `delete_qr_code_language_target`.
