# Windsurf Workflow: Account Verification with VirtualSMS

> Drop-in `.windsurfrules` that teaches Cascade when and how to use the VirtualSMS MCP server for account verification, number rentals and proxies.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![npm version](https://img.shields.io/npm/v/virtualsms-mcp.svg)](https://www.npmjs.com/package/virtualsms-mcp)
[![Powered by VirtualSMS MCP Server](https://img.shields.io/badge/Powered%20by-VirtualSMS%20MCP-7c3aed)](https://github.com/virtualsms-io/mcp-server)

## What this is

VirtualSMS is an account verification platform for developers and AI agents. It combines one-time SMS verification, dedicated number rentals, matching-country proxies and private cloud browser sessions behind one API, one MCP server and one prepaid balance.

A single `.windsurfrules` file that activates Cascade's awareness of the
[VirtualSMS MCP server](https://github.com/virtualsms-io/mcp-server)
whenever your agent needs to receive an SMS code, acquire a verification
phone number, rent a number, buy a proxy, or launch a cloud browser session.
Same `virtualsms-mcp` npm package that powers Claude, Cursor, Codex, OpenClaw, and 6 other MCP clients.

Carrier-issued mobile numbers across **2500+ services** and **145+ countries** (growing weekly), 40 MCP tools.

## Quick install: Hosted (recommended, zero install)

Paste this into your AI assistant's MCP config:

```json
{
  "mcpServers": {
    "virtualsms": {
      "type": "streamableHttp",
      "url": "https://mcp.virtualsms.io/mcp",
      "headers": { "x-api-key": "vsms_your_api_key_here" }
    }
  }
}
```

No `npm install`, no Node.js required on the client. The MCP server runs at [mcp.virtualsms.io](https://mcp.virtualsms.io).

Get your API key at <https://virtualsms.io>.

## Quick install: Local (stdio via npm)

1. Drop [`.windsurfrules`](./.windsurfrules) into your repo root (or fork
   this repo and reference its raw URL).

2. Cascade → Settings → MCP servers → add:

   ```json
   {
     "mcpServers": {
       "virtualsms": {
         "command": "npx",
         "args": ["virtualsms-mcp"],
         "env": { "VIRTUALSMS_API_KEY": "vsms_your_key_here" }
       }
     }
   }
   ```

3. Get your API key at <https://virtualsms.io> (free, no card).

4. Restart Windsurf. Cascade now knows when to invoke the 40
   `virtualsms_*` tools.

## What this gets your agent

- **Receive one-time SMS codes** from $0.05: `create_order` returns number + order id, `wait_for_sms` returns instantly over WebSocket for interactive flows, or `get_sms` polls on your own schedule for batch / cron jobs
- **Rent dedicated numbers** from 1 to 30 days
- **Buy matching-country residential, mobile and datacenter proxies**
- **Launch private cloud browser sessions** that work alongside your number and proxy (beta)
- **Find the cheapest available number** across 2500+ services and 145+ countries
- **Swap a number** that did not deliver: no extra charge
- **Cancel + refund** unused orders, one or many
- **Account introspection**: balance, transactions, success rate, 30-day spend

Full reference: [`.windsurfrules`](./.windsurfrules).

## Numbers

VirtualSMS numbers are carrier-issued mobile numbers, backed by real physical SIM cards on operators like Vodafone, O2 and T-Mobile, not VoIP. Carrier-lookup APIs flag VoIP and eSIM ranges, and services that care, such as Tinder, Discord, WhatsApp, OnlyFans, Hinge and banking apps, can silently reject those numbers. Carrier-issued mobile numbers pass these checks more reliably.

## Compatible services

WhatsApp · Telegram · Tinder · Discord · Instagram · Hinge · Bumble ·
OnlyFans · Snapchat · PayPal · Google · Apple · Facebook · TikTok ·
Twitter / X · LinkedIn · Uber · Amazon · Netflix · Spotify · GitHub ·
Coinbase · Kraken · Binance · MEXC · OKX · Bybit · 2500+ more.

## Cross-references

- **Parent MCP server:** <https://github.com/virtualsms-io/mcp-server>
- **npm package:** [`virtualsms-mcp`](https://www.npmjs.com/package/virtualsms-mcp)
- **Project home:** <https://virtualsms.io>
- **MCP page (per-client setup):** <https://virtualsms.io/mcp>
- **Sister skill repos:**
  [claude-skill-sms-verification](https://github.com/virtualsms-io/claude-skill-sms-verification) ·
  [openclaw-skill-sms](https://github.com/virtualsms-io/openclaw-skill-sms) ·
  [cursor-rules-sms-verification](https://github.com/virtualsms-io/cursor-rules-sms-verification) ·
  [codex-sms-verification](https://github.com/virtualsms-io/codex-sms-verification)

## License

MIT: see [LICENSE](./LICENSE).
