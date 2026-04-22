---
name: happilee-campaign-report
description: Generate WhatsApp campaign analytics reports with delivery stats, engagement rates, and actionable insights
version: 1.0.0
author: Happilee
license: MIT
tags: whatsapp, analytics, campaign, report, broadcast, insights, happilee
---

# Happilee Campaign Report

Generate a comprehensive analytics report for your WhatsApp broadcast campaigns. Pulls data from multiple Happilee tools and formats it with insights and recommendations.

## Trigger Conditions

Activate when the user mentions: campaign report, broadcast analytics, how did my campaign do, message delivery stats, broadcast performance, campaign results, weekly report, monthly report, WhatsApp marketing report.

## Workflow

### Step 1: Determine Report Scope

Ask: "What period should the report cover?"
- Last 24 hours
- Last 7 days (default)
- Last 30 days
- Custom date range

### Step 2: Pull Campaign Data

Call these tools in parallel:
1. `happilee_list_broadcasts` — get all broadcasts in the period
2. `happilee_get_analytics` — get overall broadcast analytics
3. `happilee_today_dashboard` — get today's summary metrics

For each broadcast found, call `happilee_broadcast_delivery_stats` to get per-campaign delivery data.

### Step 3: Generate Report

Format the report as:

```
📊 WhatsApp Campaign Report — [date range]
═══════════════════════════════════════════

OVERVIEW
- Campaigns sent: X
- Total messages: X
- Total recipients reached: X
- Overall delivery rate: X%
- Overall read rate: X%

CAMPAIGN BREAKDOWN
┌─────────────────────┬──────────┬──────────┬──────────┬──────────┐
│ Campaign            │ Sent     │ Delivered│ Read     │ Replied  │
├─────────────────────┼──────────┼──────────┼──────────┼──────────┤
│ [campaign_name]     │ X        │ X (X%)   │ X (X%)   │ X (X%)   │
│ [campaign_name]     │ X        │ X (X%)   │ X (X%)   │ X (X%)   │
└─────────────────────┴──────────┴──────────┴──────────┴──────────┘

TOP PERFORMING CAMPAIGN
- Name: [campaign_name]
- Read rate: X% (above X% average)
- Reply rate: X%

UNDERPERFORMING CAMPAIGN
- Name: [campaign_name]
- Delivery rate: X% (below average)
- Possible reasons: [timing, template quality, audience fatigue]

WALLET STATUS
- Current balance: ₹X
- Estimated messages remaining: X (at current rate)

RECOMMENDATIONS
1. [Actionable insight based on data]
2. [Actionable insight based on data]
3. [Actionable insight based on data]
```

### Step 4: Recommendations Engine

Generate insights based on the data:

**If delivery rate < 90%:**
"Delivery rate is below 90%. Check for invalid phone numbers in your contact list. Consider cleaning contacts with `happilee_search_contacts`."

**If read rate < 50%:**
"Read rate is low. Try sending at different times — 9-11am and 7-9pm IST typically get the highest engagement."

**If reply rate > 10%:**
"High reply rate! Your audience is engaged. Consider setting up automated flows to handle replies via `happilee_list_flows`."

**If one campaign significantly outperforms:**
"[Campaign X] had 2x the read rate of others. Analyze what's different — template content, send time, or audience segment."

**If wallet balance is low:**
"Wallet balance is running low. At current send rate, you have approximately X days of campaigns remaining."

### Step 5: Export Option

Ask: "Want me to save this report or share any specific insights?"

## Error Handling

- No broadcasts found: "No campaigns found in this period. Create your first broadcast with: 'Send a broadcast'"
- Analytics endpoint returns no data: fall back to listing broadcasts only
- Partial data: generate report with available data, note what's missing
