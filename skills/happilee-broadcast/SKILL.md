---
name: happilee-broadcast
description: Guided WhatsApp broadcast campaign creation — select template, pick audience, schedule, and send via Happilee MCP
version: 1.0.0
author: Happilee
license: MIT
tags: whatsapp, broadcast, campaign, marketing, bulk-message, happilee
---

# Happilee Broadcast Campaign

Create and send WhatsApp broadcast campaigns through a guided multi-step workflow. Chains multiple Happilee MCP tools together to go from zero to a live campaign in one interaction.

## Trigger Conditions

Activate when the user mentions: send broadcast, create campaign, bulk message, mass message, send to all contacts, festival offer, promotional message, Diwali offer, marketing campaign, send template to multiple people.

## Workflow

Follow these steps in order. Ask the user for input at each step before proceeding.

### Step 1: List Available Templates

Call `happilee_list_templates` with `limit: 10` to show the user their approved templates.

Present templates in a clean format:
```
Available Templates:
1. [template_name] (ID: xxx) — "body text preview..."
2. [template_name] (ID: xxx) — "body text preview..."
```

Ask: "Which template would you like to use for this broadcast?"

### Step 2: Identify the Audience

Ask the user who they want to send to. Options:

**Option A — By tags:** "Send to all contacts tagged 'VIP'"
- Call `happilee_search_contacts` with the tag filter to estimate audience size
- Show count: "Found X contacts with tag 'VIP'"

**Option B — By search:** "Send to contacts matching 'Mumbai'"
- Call `happilee_search_contacts` with search term
- Show matching contacts

**Option C — All contacts:** "Send to everyone"
- Call `happilee_search_contacts` with a high limit to estimate total count

Confirm: "Ready to send to X contacts. Proceed?"

### Step 3: Template Parameters

If the selected template has variables (e.g. `{{name}}`, `{{order_id}}`):
- Ask the user what value to use for each variable
- For personalized variables like `{{name}}`, explain: "The contact's name will be automatically filled from their profile"

### Step 4: Schedule or Send Now

Ask: "Send now or schedule for later?"

**Send now:**
- Call `happilee_send_broadcast` with the template ID, recipients, and params

**Schedule:**
- Ask for date and time
- Call `happilee_schedule_broadcast` with the schedule details

### Step 5: Confirmation

After sending/scheduling, present:
```
Broadcast Created
- Template: [name]
- Recipients: [count]
- Status: Sent / Scheduled for [datetime]
- Broadcast ID: [id]

To check delivery stats later, say: "Show me broadcast analytics"
```

## Error Handling

- If no templates found: suggest creating one first via `happilee_create_template`
- If no contacts match: suggest broadening the search or checking tags
- If send fails: show the error and suggest checking wallet balance via `happilee_get_wallet_balance`
- If rate limited: inform user and suggest scheduling for later

## Tips

- Always confirm recipient count before sending — broadcasts consume message credits
- Recommend sending a test to one number first before mass broadcast
- For templates with media headers, remind user to check the media URL is accessible
