# SpawnDock

**AI-powered development platform for Telegram Mini Apps on the TON blockchain.**

One command to bootstrap a project, get a live preview tunnel,
and let AI agents help you build.

---

## How it works

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#ff8c00', 'primaryTextColor': '#fff', 'primaryBorderColor': '#e67300', 'lineColor': '#ffa500', 'secondaryColor': '#2d2d2d', 'tertiaryColor': '#3a3a3a', 'edgeLabelBackground': '#1a1a1a', 'clusterBkg': '#1e1e1e', 'clusterBorder': '#ff8c00', 'background': '#0d1117'}}}%%
flowchart LR
  subgraph you["Your machine"]
    direction TB
    create["npx @spawn-dock/create"]
    dev["pnpm run dev"]
    create --> dev
  end

  subgraph cloud["SpawnDock"]
    direction TB
    tunnel["Dev tunnel"]
    kb["Knowledge base\n55+ docs"]
  end

  subgraph tg["Telegram"]
    preview["Mini App\npreview"]
  end

  subgraph ai["AI agent"]
    mcp["MCP client"]
  end

  dev <-->|WebSocket| tunnel
  tunnel --> preview
  mcp -->|SSE| kb

  style create fill:#ff8c00,stroke:#e67300,color:#fff
  style dev fill:#ff9800,stroke:#e67300,color:#fff
  style tunnel fill:#ffb74d,stroke:#e67300,color:#1a1a1a
  style kb fill:#ffb74d,stroke:#e67300,color:#1a1a1a
  style preview fill:#ff8c00,stroke:#e67300,color:#fff
  style mcp fill:#ffe0b2,stroke:#e67300,color:#1a1a1a
```

---

## Quick start

```bash
# 1 — Create a new project
npx -y @spawn-dock/create@beta --token <pairing-token> my-app

# 2 — Start dev server + tunnel
cd my-app
pnpm run dev

# 3 — Open the Telegram deep link printed in the console
```

The CLI scaffolds a **Next.js + TypeScript + TON Connect** app, connects a live tunnel for real-device previews, and wires up MCP so AI agents have full context on TMA and TON APIs.

---

## What you get

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#ff8c00', 'primaryTextColor': '#fff', 'primaryBorderColor': '#e67300', 'lineColor': '#ffa500', 'clusterBkg': '#1e1e1e', 'clusterBorder': '#ff8c00', 'background': '#0d1117'}}}%%
flowchart TD
  A["Starter template\nNext.js + TON Connect + Telegram UI"] --> B["Dev tunnel\nInstant Telegram previews"]
  B --> C["AI knowledge base\n55+ searchable docs"]
  C --> D["AI runtime\nClaude Code / Cursor / Codex"]

  style A fill:#ff8c00,stroke:#e67300,color:#fff
  style B fill:#ff9800,stroke:#e67300,color:#fff
  style C fill:#ffa726,stroke:#e67300,color:#fff
  style D fill:#ffb74d,stroke:#e67300,color:#1a1a1a

  linkStyle default stroke:#ff8c00,stroke-width:2px
```

| Feature | Details |
| :--- | :--- |
| **Project scaffolding** | Production-ready TMA template with TON Connect wallet integration |
| **Live preview tunnel** | WebSocket tunnel exposes `localhost` to Telegram — test on a real device instantly |
| **AI knowledge base** | 55+ docs on Telegram Mini Apps, TON smart contracts, wallets, deployment, and more |
| **AI runtime** | Sandboxed launcher for Claude Code, Cursor, or Codex with full MCP context |

---

## Packages

| Package | What it does |
| :--- | :--- |
| [`@spawn-dock/create`](https://github.com/SpawnDock/create-spawn-dock) | Scaffolds a new project with tunnel and MCP pre-configured |
| [`@spawn-dock/dev-tunnel`](https://github.com/SpawnDock/dev-tunnel) | Exposes your local dev server for Telegram previews |
| [`@spawn-dock/mcp`](https://github.com/SpawnDock/mcp-client) | Gives AI agents searchable access to the knowledge base |
| [`@spawn-dock/cli`](https://github.com/SpawnDock/cli) | Detects config and launches the AI agent of your choice |
| [`tma-project`](https://github.com/SpawnDock/tma-project) | Starter template every project is built from |

---

## Knowledge base topics

| Area | Covers |
| :--- | :--- |
| **Telegram Mini Apps** | WebApp API, navigation, theming, testing, security, performance |
| **TON Blockchain** | Smart contracts (Tolk / Tact / FunC), jettons, NFTs, DeFi, wallets, DNS, payments |
| **TON Connect** | Wallet integration, authentication, TON Proof |
| **Deployment** | Cloudflare Pages, Vercel, GitHub Pages |
| **Templates** | Shop, game, landing, quiz, menu, portfolio |

---

## License

MIT
