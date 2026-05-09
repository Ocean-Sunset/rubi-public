# 🤖 Solrais - Sol's RNG Macro Tracker

> Solrais is a powerful Discord bot designed for tracking macro sessions in Sol's RNG, featuring AI-powered chat, multi-server support, and a web dashboard.

![Version](https://img.shields.io/badge/version-v1.4.3-blue)
![Node](https://img.shields.io/badge/node-18%2B-green)

---

## ⚠️ NOTICE

> [!NOTE]
> This repository is **PRIVATE**. Do not share, distribute, or publish any part of this code without explicit permission from the owner.

---

## 🌟 Features

### 🤖 AI Chat Integration
- **Groq API** with 12+ callable tools for real-time data
- **User Profile Learning** — Solrais remembers personality traits, writing style, and interests
- **Smart Responses** — Knows Sol's RNG mechanics, aura rarities, potion mechanics, and more
- **Person Lookup** — Can answer questions about specific server members
- **Username Search** — Fuzzy matching for finding users with partial/typo names

### 🖥️ Multi-Server Architecture
- **Per-Server Configuration** — Each server has its own delay channels, webhooks, and settings
- **Relay Nodes** — Distributed nodes handle webhook processing for reliability
- **Real-Time Sync** — Config changes broadcast instantly to all nodes

### 📊 Dashboard
- Web-based dashboard with real-time stats
- Leaderboard visualization
- Session history and daily activity charts
- Discord OAuth2 authentication

### 🛡️ Macro Tracking
- Auto-detection of macro start/stop events
- Support for native Discord webhooks and relay servers
- Daily quest and achievement tracking
- Biome detection and statistics
- Merchant tracking (mari, jester, rin)
- Rare biome alerts (glitch, dreamspace, cyberspace)

---

## 🚀 Setup

### Prerequisites
- Node.js 18+
- Discord Bot Token
- Groq API Key (free tier available)

### Installation

```bash
# Install dependencies
npm install

# Install relay bot dependencies
cd relay-bot-1 && npm install && cd ..
cd relay-bot-2 && npm install && cd ..
cd handler && npm install && cd ..
```

### Configuration

> [!NOTE]
> Copy `.env.example` to `.env` and fill in your credentials.

```bash
cp .env.example .env
```

Edit `.env` with your credentials:

```env
TOKEN=your_discord_bot_token
DISCORD_CLIENT_ID=your_client_id
DISCORD_CLIENT_SECRET=your_client_secret
GROQ_API_KEY=your_groq_api_key
SESSION_SECRET=random_secure_string
PORT=24593
HOST=your-domain.com
```

### Running

```bash
# Start main bot
npm start

# Start relay nodes (in separate terminals)
cd relay-bot-1 && node index.js
cd relay-bot-2 && node index.js

# Start watchdog handler
cd handler && node index.js
```

---

## 📁 Project Structure

```
├── src/
│   ├── bot/server/
│   │   ├── commands.js          # Slash command handlers
│   │   └── configUIHandler.js   # Config UI interactions
│   ├── services/server/
│   │   ├── groqService.js       # AI chat with Groq
│   │   ├── groqTools.js         # AI tool definitions (12+ tools)
│   │   ├── macroService.js      # Macro tracking logic
│   │   ├── nodeService.js       # Node registration
│   │   └── webhookService.js    # Webhook relay
│   └── utils/server/
│       ├── constants.js          # Categories, biomes, merchants
│       ├── macroHandler.js       # Data layer
│       └── configHandler.js      # Config management
├── relay-bot-1/                  # Relay node 1 (server1)
├── relay-bot-2/                  # Relay node 2 (server2)
├── handler/                      # Watchdog handler
├── server.js                     # Express web server + dashboard
├── data/                         # Runtime data (not committed)
└── .env                          # Secrets (not committed)
```

---

## 🎮 Commands

| Command | Description |
|---------|-------------|
| `/category` | Manage delay channels and categories |
| `/solraisconfig` | Configure weather, delays, and webhooks |
| `/stats` | View macro statistics |
| `/leaderboard` | View the macro leaderboard |
| `/daily` | View daily quest status |
| `?ping` | Test bot and node latency |
| `?help` | Show help menu |
| `!assign_channel` | Link Discord channel to macro channel |

### AI Chat
Mention Solrais or use `!` prefix to chat. Solrais can:
- Answer questions about Sol's RNG
- Look up user stats and leaderboard positions
- Compare users
- Show biome breakdowns and session history

---

## 🔧 Configuration

### Multi-Server Setup

Each server in `data/config.json` has its own configuration:

```json
{
  "servers": {
    "server1": {
      "delay_channels": ["hell", "heaven", "dreamspace"],
      "delay": [{ "webhook": "...", "delay": 5 }],
      "weather": [{ "rainy": "..." }],
      "delay_channel_roles": { "dreamspace": "<@&role_id>" }
    },
    "server2": { ... }
  }
}
```

---

## 📜 License

**PRIVATE** — This code is the exclusive property of its owner. All rights reserved.

> [!CAUTION]
> **Do not share, redistribute, or use this code without permission.**
