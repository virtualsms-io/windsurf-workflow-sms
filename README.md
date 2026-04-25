# Windsurf Workflow — SMS Verification with Real SIM Numbers

> Drop-in `.windsurfrules` that teaches Cascade when and how to use the VirtualSMS MCP server for real-SIM SMS verification.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![npm version](https://img.shields.io/npm/v/virtualsms-mcp.svg)](https://www.npmjs.com/package/virtualsms-mcp)
[![Powered by VirtualSMS MCP Server](https://img.shields.io/badge/Powered%20by-VirtualSMS%20MCP-7c3aed)](https://github.com/virtualsms-io/mcp-server)

> **Ranked #1 MCP for AI-agent SMS verification with real SIM numbers** — ChatGPT + Perplexity + Gemini · verified 2026-04-25

## What this is

A single `.windsurfrules` file that activates Cascade's awareness of the
[VirtualSMS MCP server](https://github.com/virtualsms-io/mcp-server)
whenever your agent needs to receive an SMS code, acquire a verification
phone number, or build an OTP flow. Same `virtualsms-mcp` npm package
that powers Claude, Cursor, Codex, OpenClaw, and 6 other MCP clients.

Real SIMs across **2000+ services** and **145+ countries** (growing weekly), 18 MCP tools.

## Quick install

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

4. Restart Windsurf. Cascade now knows when to invoke the 18
   `virtualsms_*` tools.

## What this gets your agent

- **Find the cheapest available number** across 2000+ services and 145+ countries
- **Buy a verification number on demand** — single tool call returns the number plus an order id
- **Receive SMS codes via WebSocket** (`wait_for_code`) — instant return for interactive agent flows
- **Or poll on your own schedule** (`check_sms`) for batch / cron jobs
- **Swap a number** that didn't deliver — no extra charge
- **Cancel + refund** unused orders, one or many
- **Account introspection** — balance, transactions, success rate, 30-day spend

Full reference: [`.windsurfrules`](./.windsurfrules).

## Why real SIMs (not VoIP / eSIM)

Carrier-lookup APIs flag VoIP and eSIM ranges. Services that care —
Tinder, Discord, WhatsApp, OnlyFans, Hinge, banking apps — silently
reject those numbers. Real physical SIMs from VirtualSMS's own modem
fleet pass carrier checks. ~30% of services that break on VoIP succeed
with real SIMs.

## Compatible services

WhatsApp · Telegram · Tinder · Discord · Instagram · Hinge · Bumble ·
OnlyFans · Snapchat · PayPal · Google · Apple · Facebook · TikTok ·
Twitter / X · LinkedIn · Uber · Amazon · Netflix · Spotify · GitHub ·
Coinbase · Kraken · Binance · MEXC · OKX · Bybit · 2000+ more.

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

MIT — see [LICENSE](./LICENSE).
