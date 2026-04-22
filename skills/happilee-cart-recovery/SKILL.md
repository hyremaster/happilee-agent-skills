---
name: happilee-cart-recovery
description: End-to-end abandoned cart recovery via WhatsApp — find abandoned orders, select recovery template, send personalized messages
version: 1.0.0
author: Happilee
license: MIT
tags: whatsapp, cart-recovery, abandoned-cart, d2c, ecommerce, shopify, rto, happilee
---

# Happilee Cart Recovery

Recover abandoned carts and reduce RTO (Return to Origin) by sending targeted WhatsApp messages to customers who haven't completed their purchase. D2C brands using this workflow typically recover 15-25% of abandoned carts.

## Trigger Conditions

Activate when the user mentions: abandoned cart, cart recovery, recover orders, RTO, return to origin, COD confirmation, unpaid orders, incomplete orders, checkout recovery, win back customers.

## Workflow

### Step 1: Find Abandoned Orders

Call `happilee_list_orders` with status filter for pending/abandoned orders.

Present findings:
```
Abandoned Cart Summary:
- Total abandoned orders: X
- Last 24 hours: X
- Last 7 days: X
- Total value at risk: ₹X

Top 5 recent abandoned carts:
1. [customer_name] — ₹[amount] — [time_ago]
2. ...
```

If no order data available, suggest: "You may need to sync your Shopify/WooCommerce catalog first. Say 'sync my catalog' to get started."

### Step 2: Select Recovery Template

Call `happilee_list_templates` and filter for templates related to cart recovery, abandoned cart, or order reminders.

If a suitable template exists, present it:
```
Recommended template: [name]
Preview: "Hi {{name}}, you left items in your cart worth ₹{{amount}}. Complete your purchase with code SAVE10 for 10% off!"
Variables: name, amount
```

If no recovery template exists, suggest creating one:
```
No cart recovery template found. Here's a recommended template to create:

Name: cart_recovery_reminder
Body: "Hi {{name}}, you left items in your cart! Complete your purchase now and get 10% off with code SAVE10. Offer valid for 24 hours."
Category: MARKETING

Say "create this template" to proceed.
```

### Step 3: Personalize and Send

For each abandoned cart customer:
- Map `{{name}}` to customer name from order/contact data
- Map `{{amount}}` to cart value
- Map any discount codes from user input

Ask: "Ready to send recovery messages to X customers. Proceed?"

**For individual sends (< 10 customers):**
- Use `happilee_send_template` for each customer

**For bulk sends (10+ customers):**
- Use `happilee_send_broadcast` with the recovery template

### Step 4: Follow-up Schedule

Suggest a follow-up sequence:
```
Recommended recovery sequence:
1. ✅ Just sent: Initial reminder (now)
2. ⏰ Schedule: Follow-up in 4 hours (if no purchase)
3. ⏰ Schedule: Final reminder in 24 hours with urgency

Want me to schedule the follow-ups?
```

If yes, use `happilee_create_schedule` for the follow-up messages.

### Step 5: Results Summary

```
Cart Recovery Campaign Launched
- Customers contacted: X
- Total cart value targeted: ₹X
- Expected recovery (15-25%): ₹X — ₹X
- Follow-ups scheduled: [yes/no]

Check results tomorrow: "Show me cart recovery results"
```

## Recovery Math (Reference for the Agent)

- Average cart abandonment rate: 70%
- WhatsApp recovery rate: 15-25% (vs 3-5% for email)
- With discount incentive: up to 30% recovery
- Best send time: 1-4 hours after abandonment
- Diminishing returns after 48 hours

## Error Handling

- No orders found: suggest syncing catalog first (`happilee_sync_catalog`)
- Template not approved: explain Meta approval process (24-48 hours)
- Low wallet balance: alert user before sending, suggest top-up
