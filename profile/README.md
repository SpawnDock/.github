# SpawnDock

AI-powered development platform for Telegram Mini Apps on the TON blockchain. Bootstrap a project, get a live preview tunnel, and let AI agents help you build — all from one command.

## How it works

```
npx -y @spawn-dock/create@beta --token <pairing-token> my-app
cd my-app && pnpm run dev
```

The bootstrap CLI clones the starter template, configures the tunnel, wires up MCP for AI agents, and gives you a Telegram deep link to preview your app instantly.

## Packages

| Package | Description |
|---------|-------------|
| [`create`](https://github.com/SpawnDock/create) | Bootstrap CLI. Scaffolds a new TMA project with SpawnDock config, dev tunnel, and MCP integration out of the box. |
| [`dev-tunnel`](https://github.com/SpawnDock/dev-tunnel) | WebSocket tunnel client. Exposes your local dev server through the SpawnDock control plane so you can preview your TMA from a real Telegram client. |
| [`mcp`](https://github.com/SpawnDock/mcp-client) | MCP knowledge client. A stdio-to-SSE bridge that gives AI agents (Claude Code, Cursor, Codex) access to 55+ docs on TMA development, TON smart contracts, and deployment. |
| [`cli`](https://github.com/SpawnDock/cli) | AI runtime launcher. Detects `spawndock.config.json` and starts the configured agent (OpenCode, Claude, or Codex) in a sandboxed environment. |
| [`tma-project`](https://github.com/SpawnDock/tma-project) | Starter template. Next.js + TypeScript + TON Connect + Telegram UI — the base every `@spawn-dock/create` project is built from. |

## Architecture

```
Developer machine                          SpawnDock control plane
+--------------------------+               +---------------------------+
| Next.js dev server :3000 |               |  API / MCP server         |
|        ^                 |  WebSocket    |    - preview routing      |
|        |                 | <-----------> |    - knowledge base (55+) |
| @spawn-dock/dev-tunnel   |               |    - Telegram bot         |
+--------------------------+               +---------------------------+
                                                      |
AI agent (Claude / Codex / Cursor)                    |
+--------------------------+               Telegram   |
| @spawn-dock/mcp (stdio)  | ---SSE--->   +----------+---------+
|   search("how to ...")   |               | Mini App preview   |
+--------------------------+               +--------------------+
```

## Knowledge base

The MCP server provides AI agents with searchable access to 55+ documents covering:

- **Telegram Mini Apps** — WebApp API, navigation, theming, testing, security, performance
- **TON Blockchain** — smart contracts (Tolk/Tact/FunC), jettons, NFTs, DeFi, wallets, DNS, payments
- **TON Connect** — wallet integration, authentication, TON Proof
- **Deployment** — Cloudflare Pages, Vercel, GitHub Pages
- **Templates** — shop, game, landing, quiz, menu, portfolio

## Quick start

```bash
# 1. Create a new project
npx -y @spawn-dock/create@beta --token <pairing-token> my-app

# 2. Start dev server + tunnel
cd my-app
pnpm run dev

# 3. Open the Telegram deep link printed in the console
```

## License

MIT
