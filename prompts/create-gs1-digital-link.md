# Prompt: Create a GS1 Digital Link QR Code

Use this for product QR Codes based on GS1 Digital Link identifiers and routing rules.

## Product QR Code

```
Create a GS1 Digital Link QR Code for GTIN 5449000297280 that redirects by
default to https://example.com/products/cola-500ml and title it "Cola 500 ml".
```

## Add product data

```
Create a GS1 Digital Link QR Code for GTIN 09506000134352 with expiry date
December 31, 2029 and batch number batch-2026-37.
```

## Add a language rule

```
For the GS1 Digital Link QR Code named "Cola 500 ml", add a German product
information rule that sends German users to https://example.com/de/produkte/cola-500ml.
```

## What happens

The agent calls `create_gs1_digital_link` for the QR Code and `create_gs1_digital_link_rule` for language or linktype-specific routing. It can inspect rules with `list_gs1_digital_link_rules` and remove all rules with `delete_gs1_digital_link_rules`.
