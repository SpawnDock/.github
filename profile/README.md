# SpawnDock

**AI-powered development platform**

## TMA Spawner

The first SpawnDock product — a Telegram bot that creates ready-to-code TMA projects in seconds.

Send `/new` to the bot, run one command locally, and get a live Mini App preview right inside Telegram — with an AI agent that knows TMA and TON inside out.

---

### How it works

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#ff8c00', 'primaryTextColor': '#fff', 'primaryBorderColor': '#e67300', 'lineColor': '#ffa500', 'secondaryColor': '#2d2d2d', 'tertiaryColor': '#3a3a3a', 'edgeLabelBackground': '#1e1e1e', 'clusterBkg': '#161b22', 'clusterBorder': '#e67300', 'background': '#0d1117'}}}%%
flowchart TD
  A["1. /new my-app\nTelegram bot creates the project\nand returns a pairing token"]
  B["2. npx @spawn-dock/create --token ...\nCLI clones the template, configures\ntunnel + MCP, claims the token"]
  C["3. pnpm run dev\nNext.js starts, tunnel connects\nto the SpawnDock control plane"]
  D["4. Open the Telegram deep link\nPreview your Mini App\non a real device"]
  E["5. AI agent assists development\n55+ docs on TMA, TON, wallets,\nsmart contracts, deployment"]

  A --> B --> C --> D
  C --> E

  style A fill:#ff8c00,stroke:#e67300,color:#fff
  style B fill:#ff9800,stroke:#e67300,color:#fff
  style C fill:#ffa726,stroke:#e67300,color:#fff
  style D fill:#ff8c00,stroke:#e67300,color:#fff
  style E fill:#ffb74d,stroke:#e67300,color:#1a1a1a

  linkStyle default stroke:#ffa500,stroke-width:2px
```

---

### Quick start

```bash
# The bot gives you a pairing token and a bootstrap command.
# Run it locally:
npx -y @spawn-dock/create@beta --token <pairing-token> my-app

# Start dev server + tunnel:
cd my-app
pnpm run dev

# Open the Telegram deep link printed in the console.
```

---

### What each package does

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#ff8c00', 'primaryTextColor': '#fff', 'primaryBorderColor': '#e67300', 'lineColor': '#ffa500', 'clusterBkg': '#161b22', 'clusterBorder': '#e67300', 'background': '#0d1117'}}}%%
flowchart LR
  subgraph bot["Telegram Bot"]
    spawner["TMA Spawner\n/new /launch /help"]
  end

  subgraph local["Developer machine"]
    create["@spawn-dock/create\nBootstrap CLI"]
    tmpl["tma-project\nNext.js + TON Connect\n+ Telegram UI"]
    tunnel["@spawn-dock/dev-tunnel\nWebSocket tunnel"]
    mcp["@spawn-dock/mcp\nAI knowledge client"]
    cli["@spawn-dock/cli\nAI runtime launcher"]
  end

  subgraph cloud["SpawnDock control plane"]
    api["Project registry\nTunnel routing\nKnowledge base"]
  end

  subgraph tg["Telegram"]
    preview["Mini App preview"]
  end

  spawner -->|"pairing token"| create
  create -.->|clones| tmpl
  tunnel <-->|WebSocket| api
  mcp -->|SSE| api
  api --> preview

  style spawner fill:#ff8c00,stroke:#e67300,color:#fff
  style create fill:#ff9800,stroke:#e67300,color:#fff
  style tmpl fill:#ffb74d,stroke:#e67300,color:#1a1a1a
  style tunnel fill:#ffa726,stroke:#e67300,color:#fff
  style mcp fill:#ffe0b2,stroke:#e67300,color:#1a1a1a
  style cli fill:#ffe0b2,stroke:#e67300,color:#1a1a1a
  style api fill:#ff8c00,stroke:#e67300,color:#fff
  style preview fill:#ff8c00,stroke:#e67300,color:#fff
```

| Package | Role |
| :--- | :--- |
| [`@spawn-dock/create`](https://github.com/SpawnDock/create-spawn-dock) | Clones the template, applies SpawnDock overlay, claims the pairing token |
| [`@spawn-dock/dev-tunnel`](https://github.com/SpawnDock/dev-tunnel) | Exposes `localhost` to Telegram via the control plane |
| [`@spawn-dock/mcp`](https://github.com/SpawnDock/mcp-client) | Gives AI agents (Claude, Cursor, Codex) access to 55+ docs on TMA and TON |
| [`@spawn-dock/cli`](https://github.com/SpawnDock/cli) | Detects `spawndock.config.json` and launches the configured AI agent |
| [`tma-project`](https://github.com/SpawnDock/tma-project) | Starter template — Next.js + TypeScript + TON Connect + Telegram UI |

---

### Knowledge base

The MCP server gives AI agents searchable access to **55+ documents** (29,500+ lines):

| Area | Topics |
| :--- | :--- |
| **Telegram Mini Apps** | WebApp API, navigation, theming, testing, security, performance |
| **TON Blockchain** | Smart contracts (Tolk / Tact / FunC), jettons, NFTs, DeFi, wallets, DNS, payments |
| **TON Connect** | Wallet integration, authentication, TON Proof |
| **Deployment** | Cloudflare Pages, Vercel, GitHub Pages |
| **Templates** | Shop, game, landing, quiz, menu, portfolio |

---

### License

MIT
