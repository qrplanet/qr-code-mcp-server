# Prompt: Create a digital business card

Use this to create or update QR Planet digital business cards.

## New business card

```
Create a digital business card for Jane Doe, Sales Director at Example Inc,
with email jane@example.com and company website https://example.com.
```

## Update a business card

```
Update Jane Doe's digital business card so her job title is VP Sales and her
company URL is https://example.com/team.
```

## Add images

```
Upload a profile image to the digital business card with code <code>.
```

## What happens

The agent calls `create_digital_business_card`, `list_digital_business_cards`, `get_digital_business_card`, or `update_digital_business_card` depending on the request. For profile, logo, or background images, it calls `upload_digital_business_card_image`.
