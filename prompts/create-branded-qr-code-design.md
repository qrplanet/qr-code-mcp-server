# Prompt: Create a branded QR Code design

Use this when you already have a dynamic QR Code and want to render it with brand styling.

## Brand colors

```
Design the QR Code named "Storefront Sign" with foreground color #111827,
background color #FFFFFF, rounded modules, and a simple bottom frame that says "Scan me".
```

## With a logo

```
Design the QR Code with code <code> using our stored logo, make the logo 20%
of the QR Code size, and use our brand color #1A73E8 for the finder patterns.
```

## Download-ready

```
Create a print-ready designer image for the QR Code named "Summer Flyer" and
return the image URL I can download.
```

## What happens

The agent resolves names to QR Code codes with `list_qr_codes`, applies styling with `design_qr_code`, and can download the rendered image with `download_image_designer_qr_code`. Use `download_image_basic_qr_code` if you need the default, non-designer image.
