---
name: happilee-contact-onboarding
description: Interactive WhatsApp contact onboarding — create contact, add tags, assign operator, send welcome message
version: 1.0.0
author: Happilee
license: MIT
tags: whatsapp, contacts, onboarding, crm, tagging, operator, welcome-message, happilee
---

# Happilee Contact Onboarding

Complete contact onboarding workflow — from creating a new contact to sending them a personalized welcome message. Handles the full lifecycle in one interaction.

## Trigger Conditions

Activate when the user mentions: new contact, add contact, onboard customer, register customer, add lead, create contact, sign up customer, new subscriber.

## Workflow

### Step 1: Collect Contact Details

Ask for the required information:

```
Let's add a new contact. I'll need:
1. Phone number (with country code, e.g. 918075614551)
2. Name
3. Email (optional)
```

Validate:
- Phone number has country code prefix
- Name is not empty

### Step 2: Create the Contact

Call `happilee_create_contact` with the provided details.

If contact already exists (duplicate phone):
```
This contact already exists:
- Name: [existing_name]
- Phone: [phone]
- Tags: [existing_tags]

Would you like to update their details or proceed with tagging?
```

If created successfully:
```
✅ Contact created:
- Name: [name]
- Phone: [phone]
- Contact ID: [id]
```

### Step 3: Add Tags

Ask: "What tags should we add? (e.g. VIP, lead, campaign-2026, Mumbai)"

If user provides tags:
- Call `happilee_manage_tags` for each tag
- Confirm: "Added tags: [tag1], [tag2], [tag3]"

If user skips: proceed to next step.

### Step 4: Assign Operator

Call `happilee_list_operators` to show available operators.

```
Available operators:
1. [Operator A] — currently handling X chats
2. [Operator B] — currently handling X chats
3. [Operator C] — currently handling X chats

Assign this contact to an operator? (or skip)
```

If user picks an operator:
- Call `happilee_assign_operator` with the contact and operator
- Confirm: "Assigned to [Operator name]"

### Step 5: Send Welcome Message

Ask: "Send a welcome message to this contact?"

If yes:
- Call `happilee_list_templates` to find welcome/greeting templates
- Present top 3 options
- User picks one
- Call `happilee_send_template` with the contact's phone number and template

### Step 6: Summary

```
✅ Contact Onboarding Complete
━━━━━━━━━━━━━━━━━━━━━━━━━━━
- Contact: [name] ([phone])
- Tags: [tag1], [tag2]
- Assigned to: [operator] (or "unassigned")
- Welcome message: Sent / Skipped
━━━━━━━━━━━━━━━━━━━━━━━━━━━

Next steps:
→ "Import more contacts" — to bulk import from CSV
→ "Send a broadcast" — to reach all contacts with a tag
→ "Search contacts" — to find this contact later
```

## Bulk Onboarding

If the user wants to onboard multiple contacts:

```
For bulk import, I can help you:
1. Import from a list — provide names and phone numbers
2. Import with tags — automatically tag all imported contacts

Say "import contacts" with your list.
```

Use `happilee_import_contacts` for bulk operations.

## Error Handling

- Invalid phone format: "Please include the country code (e.g. 91 for India, 1 for US)"
- Tag creation fails: "Couldn't add tag '[tag]'. It may already exist or contain invalid characters."
- Template send fails: "Welcome message couldn't be sent. Check if the template is approved and wallet has balance."
