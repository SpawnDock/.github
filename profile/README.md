# SpawnDock

**Платформа для создания Telegram Mini Apps на TON blockchain.**

Всё настроено за тебя — шаблон, туннель для превью на телефоне, AI-ассистент с базой знаний по TMA и TON. Напиши боту `/new`, запусти одну команду — и приложение уже работает в Telegram.

---

## TMA Spawner

Telegram-бот, который создаёт проект и выдаёт всё необходимое для старта.

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#ff8c00', 'primaryTextColor': '#fff', 'primaryBorderColor': '#e67300', 'lineColor': '#ffa500', 'secondaryColor': '#2d2d2d', 'tertiaryColor': '#3a3a3a', 'edgeLabelBackground': '#1e1e1e', 'clusterBkg': '#161b22', 'clusterBorder': '#e67300', 'background': '#0d1117'}}}%%
flowchart TD
  A["1. /new my-app\nБот создаёт проект\nи отдаёт команду для терминала"]
  B["2. npx @spawn-dock/create --token ...\nШаблон клонируется, туннель\nи AI-ассистент настраиваются"]
  C["3. pnpm run dev\nДев-сервер запускается,\nтуннель подключается"]
  D["4. Открой ссылку из консоли\nПревью Mini App\nна реальном устройстве"]
  E["5. AI помогает разрабатывать\n55+ документов по TMA, TON,\nкошелькам, контрактам, деплою"]

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

## Быстрый старт

```bash
# Бот выдаёт команду с токеном — запусти её:
npx -y @spawn-dock/create@beta --token <pairing-token> my-app

# Запусти дев-сервер и туннель:
cd my-app
pnpm run dev

# В консоли появится ссылка — открой в Telegram.
```

---

## Как устроена платформа

```mermaid
%%{init: {'theme': 'base', 'themeVariables': {'primaryColor': '#ff8c00', 'primaryTextColor': '#fff', 'primaryBorderColor': '#e67300', 'lineColor': '#ffa500', 'clusterBkg': '#161b22', 'clusterBorder': '#e67300', 'background': '#0d1117', 'edgeLabelBackground': '#161b22'}}}%%
flowchart TD
  subgraph start [" "]
    direction LR
    spawner["TMA Spawner\n/new  /launch  /help"]
  end

  subgraph setup ["Настройка проекта"]
    direction LR
    create["create\nбутстрап"]
    tmpl["tma-project\nNext.js + TON Connect\n+ Telegram UI"]
    create -.->|клонирует| tmpl
  end

  subgraph dev ["Разработка"]
    direction LR
    tunnel["dev-tunnel\nтуннель для превью"]
    mcp["mcp\nAI-клиент к базе знаний"]
    cli["cli\nзапуск AI-агента"]
    cli -.-> mcp
  end

  subgraph cloud ["Контрольная плоскость"]
    api["Реестр проектов · Маршрутизация туннелей · База знаний"]
  end

  subgraph result [" "]
    direction LR
    preview["Mini App — превью в Telegram"]
  end

  spawner -->|"токен"| create
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

  linkStyle default stroke:#ffa500,stroke-width:2px
```

| Пакет | Что делает |
| :--- | :--- |
| [`@spawn-dock/create`](https://github.com/SpawnDock/create-spawn-dock) | Клонирует шаблон, настраивает туннель и MCP, привязывает проект к аккаунту |
| [`@spawn-dock/dev-tunnel`](https://github.com/SpawnDock/dev-tunnel) | Пробрасывает `localhost` в Telegram — превью на телефоне без деплоя |
| [`@spawn-dock/mcp`](https://github.com/SpawnDock/mcp-client) | Даёт AI-агентам (Claude, Cursor, Codex) доступ к 55+ документам по TMA и TON |
| [`@spawn-dock/cli`](https://github.com/SpawnDock/cli) | Запускает AI-агента в песочнице внутри проекта |
| [`tma-project`](https://github.com/SpawnDock/tma-project) | Стартовый шаблон — Next.js + TypeScript + TON Connect + Telegram UI |

---

## База знаний

AI-ассистент работает с **55+ документами** (29 500+ строк):

| Тема | Что покрывает |
| :--- | :--- |
| **Telegram Mini Apps** | WebApp API, навигация, темы, тестирование, безопасность, производительность |
| **TON Blockchain** | Смарт-контракты (Tolk / Tact / FunC), жетоны, NFT, DeFi, кошельки, DNS, платежи |
| **TON Connect** | Подключение кошельков, аутентификация, TON Proof |
| **Деплой** | Cloudflare Pages, Vercel, GitHub Pages |
| **Шаблоны** | Магазин, игра, лендинг, квиз, меню, портфолио |

---

## Лицензия

MIT
