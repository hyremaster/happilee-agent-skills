---
name: happilee-whatsapp-best-practices
description: WhatsApp Business marketing rules — avoid bans, get templates approved, optimize delivery, comply with Meta policies
version: 1.0.0
author: Happilee
license: MIT
tags: whatsapp, best-practices, compliance, marketing, ban-prevention, template-approval, meta-policies
---

# WhatsApp Business Best Practices

Comprehensive rules for WhatsApp Business marketing. Avoid account bans, get templates approved faster, optimize message delivery, and comply with Meta's Business policies. Based on experience managing 1,600+ businesses and 30,000+ broadcasts on the Happilee platform.

## Trigger Conditions

Activate when the user mentions: WhatsApp tips, avoid ban, template approval, WhatsApp compliance, message not delivered, template rejected, account suspended, WhatsApp marketing tips, best practices, how to broadcast safely.

## Rules

### BAN PREVENTION (Critical)

**Rule 1: Never broadcast from a personal WhatsApp number**
Personal WhatsApp accounts are NOT designed for bulk messaging. You WILL get banned.
- Use WhatsApp Business API (via platforms like Happilee)
- Business API has no per-message ban risk — messages go through Meta's approved channels
- Personal account ban threshold: ~50-100 unsolicited messages

**Rule 2: Only message opted-in contacts**
- Meta requires explicit opt-in before sending marketing messages
- Opt-in methods: website form, WhatsApp QR code, in-store sign-up, reply to a business-initiated conversation
- Never buy contact lists — this is the #1 cause of account flags

**Rule 3: Respect the 24-hour messaging window**
- You can send free-form messages only within 24 hours of the customer's last message
- Outside 24 hours: only approved template messages allowed
- Template messages cost money (per Meta's conversation pricing)

**Rule 4: Monitor your quality rating**
- Meta assigns a quality rating: Green (high), Yellow (medium), Red (low)
- Red quality = messaging limits reduced, potential account restriction
- Check at: Meta Business Suite → WhatsApp Manager → Phone Numbers
- Quality drops when users report/block your messages

**Rule 5: Handle "STOP" requests immediately**
- If a customer says "stop", "unsubscribe", or "opt out" — remove them immediately
- Not handling opt-outs is a Meta policy violation
- Set up keyword-triggered auto-unsubscribe in Happilee flows

### TEMPLATE APPROVAL

**Rule 6: Template naming conventions**
- Use lowercase with underscores: `order_confirmation`, `cart_recovery`
- Include the purpose in the name — reviewers check this
- Avoid generic names: `test`, `message1`, `promo`

**Rule 7: Template body best practices**
- Keep under 1024 characters
- Use variables for personalization: `{{name}}`, `{{order_id}}`
- Don't include URLs directly — use URL buttons instead
- Avoid ALL CAPS — triggers spam filters
- Don't use misleading urgency: "ACT NOW OR LOSE YOUR ACCOUNT"

**Rule 8: Template category selection**
- **UTILITY**: Order confirmations, shipping updates, account alerts → higher approval rate
- **MARKETING**: Promotions, offers, newsletters → stricter review
- **AUTHENTICATION**: OTP, verification codes → fast approval, special format
- Wrong category = rejection. Don't put promotions under UTILITY.

**Rule 9: Common rejection reasons**
- Missing opt-out option in marketing templates
- URL in body text (use URL button instead)
- Requesting sensitive info (passwords, financial details)
- Content that violates Meta commerce policies (weapons, drugs, etc.)
- Template too similar to a recently rejected one

**Rule 10: Resubmission strategy**
- Wait 24 hours before resubmitting a rejected template
- Change the template name (Meta flags resubmissions of same name)
- Address the rejection reason — check Meta Business Suite for specific feedback
- If repeatedly rejected, try a different category or simpler wording

### MESSAGE DELIVERY OPTIMIZATION

**Rule 11: Optimal send times (India)**
- B2C: 9-11am IST or 7-9pm IST (highest open rates)
- B2B: 10am-12pm IST weekdays
- Avoid: Before 8am, after 10pm, Sunday mornings
- Festival messages: send 2-3 days before, not on the day (everyone sends on the day)

**Rule 12: Batch your broadcasts**
- Don't send 10,000 messages at once — stagger in batches of 1,000-2,000
- Wait 15-30 minutes between batches
- This prevents sudden quality rating drops from spike in blocks/reports
- Happilee's broadcast scheduling handles this automatically

**Rule 13: Personalize everything**
- Messages with `{{name}}` get 20-30% higher read rates
- Include relevant context: order number, product name, specific offer
- Generic "Dear Customer" feels like spam — personal feels like a conversation

**Rule 14: Rich media increases engagement**
- Image templates: 2x click-through vs text-only
- Video templates: highest engagement but highest cost
- Document templates: useful for invoices, receipts, catalogs
- Header media must be under 5MB

**Rule 15: Use interactive templates**
- Quick reply buttons: 3x higher response rate
- Call-to-action buttons (URL, phone): 2x click-through
- List messages: best for catalogs, menus, options
- Always have a clear CTA — don't just inform, invite action

### COMPLIANCE

**Rule 16: Data handling**
- Store customer data securely — don't log WhatsApp message content in plain text
- API keys are project-specific — never share across teams
- Regularly rotate API keys (quarterly recommended)

**Rule 17: Conversation pricing awareness**
- Marketing conversations: most expensive (~₹0.80-1.20 per conversation)
- Utility conversations: cheaper (~₹0.30-0.50)
- Service conversations: free when customer messages first (within 24h window)
- Authentication: special pricing (cheapest)
- 1 conversation = 24-hour window, not per-message

**Rule 18: Rate limits**
- New accounts: 250 conversations/24h
- After verification: 1,000/24h → 10,000/24h → 100,000/24h (auto-scaling)
- Tier upgrades happen automatically based on quality rating + volume
- Don't try to send 10,000 messages on a new account — you'll hit limits

## Quick Reference Commands

If using Happilee MCP tools:
- Check wallet: "What's my wallet balance?"
- List templates: "Show me my approved templates"
- Send broadcast: "Send a broadcast" (triggers the broadcast skill)
- Check analytics: "How did my last campaign do?"
- View contacts: "Search contacts tagged VIP"
