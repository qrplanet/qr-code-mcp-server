# Prompt: Issue a coupon voucher

Use this to issue vouchers and inspect coupon performance.

## Issue one voucher

```
Issue a voucher for the coupon named "Summer Discount" with a 14-day expiry.
```

## Issue by group

```
Issue a voucher for coupon code <coupon_code> in the group "retail-kiosk".
```

## Coupon reporting

```
Show issue and redemption statistics for the coupon named "Summer Discount".
```

## What happens

The agent calls `list_coupons` to resolve coupon names to coupon codes, `issue_coupon_voucher` to issue vouchers, `get_coupon_issue_stats` for issue statistics, and `get_coupon_redemptions` for redemption statistics.
