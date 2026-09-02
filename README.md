# Happilee Agent Skills

> WhatsApp Business automation skills for AI agents. The first WhatsApp platform on [skills.sh](https://skills.sh).

## What are these?

Skills are guided workflows that chain [Happilee MCP tools](https://github.com/hyremaster/happilee-mcp-server) together. Instead of calling individual tools, skills provide complete multi-step workflows for common WhatsApp Business operations.

**Works with:** Claude Code, Cursor, Copilot, VS Code, Windsurf, Cline, and 20+ agent platforms.

## Install

```bash
npx skills add hyremaster/happilee-agent-skills
```

## Skills

| Skill | What it does |
|-------|-------------|
| **happilee-broadcast** | Guided broadcast campaign — select template → pick audience → schedule → send |
| **happilee-cart-recovery** | Abandoned cart recovery — find orders → select template → send personalized messages |
| **happilee-campaign-report** | Analytics report — pull data from all campaigns → format with insights + recommendations |
| **happilee-daily-digest** | Morning dashboard — today's stats, pending chats, operator performance, wallet balance |
| **happilee-contact-onboarding** | Contact setup — create → tag → assign operator → send welcome message |
| **happilee-whatsapp-best-practices** | 18 rules for WhatsApp marketing — avoid bans, get templates approved, optimize delivery |

## Prerequisites

These skills work best with the [Happilee MCP Server](https://github.com/hyremaster/happilee-mcp-server) installed for full tool access. The best practices skill works standalone as a knowledge reference.

## Usage Examples

```
"Send a broadcast to all VIP contacts"     → triggers happilee-broadcast
"Recover abandoned carts from last week"    → triggers happilee-cart-recovery
"How did my campaigns do this week?"        → triggers happilee-campaign-report
"Give me my morning report"                 → triggers happilee-daily-digest
"Add a new contact 918075614551"            → triggers happilee-contact-onboarding
"How do I avoid getting my number banned?"  → triggers happilee-whatsapp-best-practices
```

## About Happilee

[Happilee](https://happilee.io) is a WhatsApp Business API automation platform used by 1,600+ Indian businesses for broadcasting, team inbox, chatbot flows, and WhatsApp commerce.

- 43 MCP tools (most in the WhatsApp BSP space)
- 30,000+ broadcasts sent
- 1M+ monthly conversations

## License

MIT


<!-- Security scan triggered at 2026-09-02 15:40:03 -->