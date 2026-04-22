---
name: happilee-daily-digest
description: Morning dashboard for WhatsApp Business — today's stats, pending chats, scheduled campaigns, operator performance, wallet balance
version: 1.0.0
author: Happilee
license: MIT
tags: whatsapp, dashboard, daily, digest, morning-report, business-intelligence, happilee
---

# Happilee Daily Digest

Your morning WhatsApp Business dashboard in one command. Pulls data from 6 Happilee tools and presents a unified view of what happened, what's pending, and what's coming up.

## Trigger Conditions

Activate when the user mentions: daily digest, morning report, what happened today, daily summary, business overview, dashboard, how's my WhatsApp doing, any updates, what's going on, start of day briefing.

## Workflow

### Step 1: Pull All Data (Parallel Calls)

Call all these tools simultaneously for speed:
1. `happilee_today_dashboard` — today's key metrics
2. `happilee_check_notifications` — unread notifications
3. `happilee_list_schedules` — upcoming scheduled campaigns
4. `happilee_operator_performance` — operator activity
5. `happilee_get_wallet_balance` — message credits remaining
6. `happilee_list_broadcasts` — recent broadcast performance

### Step 2: Format the Digest

```
☀️ Good morning! Here's your Happilee Daily Digest
══════════════════════════════════════════════════

📈 TODAY'S NUMBERS
- New conversations: X
- Messages received: X
- Messages sent: X
- Contacts added: X
- Chats resolved: X

💬 PENDING ATTENTION
- Unresolved chats: X
- Unread notifications: X
- Chats waiting > 1 hour: X
[List top 3 pending items if any]

👥 TEAM PERFORMANCE
- Active operators: X / X total
- [Operator A]: X chats handled, X resolved
- [Operator B]: X chats handled, X resolved
- [Operator C]: X chats handled, X resolved

📢 RECENT CAMPAIGNS
- Last broadcast: [name] — sent X, delivered X%, read X%
- [Next scheduled]: [name] at [time]

💰 WALLET
- Balance: ₹X
- Estimated runway: X days at current rate
[⚠️ Low balance alert if < 3 days runway]

📋 TODAY'S SCHEDULE
- [time]: [scheduled campaign name]
- [time]: [scheduled campaign name]
- No upcoming schedules ✓
```

### Step 3: Smart Alerts

Flag anything that needs immediate attention:

**High priority (show first):**
- Wallet balance < ₹500: "⚠️ Low wallet balance — top up to avoid campaign interruptions"
- Unresolved chats > 20: "⚠️ X chats unresolved — consider assigning more operators"
- Failed broadcast: "⚠️ Last broadcast had X% failure rate — check template approval status"

**Medium priority:**
- No operator active: "ℹ️ No operators currently online"
- Scheduled campaign in < 2 hours: "ℹ️ Campaign '[name]' launching in X hours"

### Step 4: Quick Actions

End with actionable suggestions based on the data:

```
QUICK ACTIONS
→ "Show me unresolved chats" — to triage pending conversations
→ "Send a broadcast" — to create a new campaign
→ "Show campaign report" — for detailed analytics
→ "Check my contacts" — to see recent contacts
```

## Error Handling

- If any tool fails, show the digest with available data and note: "Some data unavailable — [tool name] returned an error"
- If project not configured: "Set up your Happilee project first at app.happilee.io"
- If no data (new account): "Looks like you're just getting started! Send your first broadcast to see data here."
