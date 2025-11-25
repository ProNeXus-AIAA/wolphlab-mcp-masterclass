# 🔌 CONNECTEURS MCP – DÉTAILS TECHNIQUES

> Documentation complète des 6 connecteurs MCP pour la Masterclass Wolf Lab

---

## Table des matières

1. [n8n](#-connecteur-1--n8n)
2. [Notion](#-connecteur-2--notion)
3. [GitHub](#-connecteur-3--github)
4. [Discord](#-connecteur-4--discord)
5. [Airtable](#-connecteur-5--airtable)
6. [OpenAI](#-connecteur-6--openai--chatgpt)

---

## 🔌 CONNECTEUR 1 : n8n

### Principe

n8n intègre nativement un node **MCP Server Trigger** qui transforme n'importe quel workflow en serveur MCP. Claude Desktop se connecte via `mcp-remote` (proxy SSE).

**Flow** :
```
Claude Desktop → mcp-remote (npx) → URL SSE n8n → MCP Server Trigger → Workflow → Réponse
```

### Bloc `mcpServers` (Claude Desktop)

```json
{
  "mcpServers": {
    "n8n": {
      "command": "npx",
      "args": [
        "-y",
        "mcp-remote",
        "https://votre-instance-n8n.com/webhook/mcp/sse"
      ]
    }
  }
}
```

### Setup côté n8n

1. **Créer un workflow** avec le node "MCP Server Trigger"
2. **Configurer le tool** dans le node :
   - Name : `hello_pnx`
   - Description : `Dit bonjour depuis n8n`
   - Input Schema : `{}` (aucun paramètre)
3. **Ajouter un node Set** avec la réponse
4. **Activer** le workflow
5. **Copier l'URL SSE** générée par n8n

### Démo

> "Utilise le tool hello_pnx pour me dire bonjour"

---

## 🔌 CONNECTEUR 2 : NOTION

### Principe

Notion expose une API REST officielle. Le serveur MCP Notion fait le pont entre Claude et cette API.

**Flow** :
```
Claude Desktop → MCP Server Notion (npx) → API Notion (api.notion.com) → Workspace Notion
```

### Bloc `mcpServers`

```json
{
  "mcpServers": {
    "notion": {
      "command": "npx",
      "args": ["-y", "@notionhq/notion-mcp-server"],
      "env": {
        "NOTION_API_KEY": "secret_XXXXXXXXXXXXXXXX"
      }
    }
  }
}
```

### Setup côté Notion

1. Créer une Integration sur [notion.so/my-integrations](https://www.notion.so/my-integrations)
2. Copier le **Internal Integration Secret**
3. **Connecter** l'integration aux pages/databases à exposer

### Tools exposés

| Tool | Description |
|------|-------------|
| `notion-search` | Recherche dans le workspace |
| `notion-fetch` | Récupère le contenu d'une page/DB |
| `notion-create-pages` | Crée une ou plusieurs pages |
| `notion-update-page` | Met à jour une page |

### Démo

> "Crée une nouvelle page dans Notion intitulée 'Test Wolf Lab'"

---

## 🔌 CONNECTEUR 3 : GITHUB

### Principe

Le serveur MCP GitHub (officiel Anthropic) permet d'interagir avec l'API GitHub.

**Flow** :
```
Claude Desktop → MCP Server GitHub (npx) → API GitHub (api.github.com) → Repos/Issues/PRs
```

### Bloc `mcpServers`

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_XXXXXXXXXXXX"
      }
    }
  }
}
```

### Setup côté GitHub

1. Créer un PAT sur [github.com/settings/tokens](https://github.com/settings/tokens)
2. Permissions recommandées : Contents, Issues, Pull requests, Metadata

### Tools exposés

| Tool | Description |
|------|-------------|
| `search_repositories` | Recherche des repos |
| `get_file_contents` | Lit un fichier |
| `create_issue` | Crée une issue |
| `list_commits` | Liste les commits |
| `create_pull_request` | Crée une PR |

### Démo

> "Liste mes 5 derniers repos GitHub modifiés"

---

## 🔌 CONNECTEUR 4 : DISCORD

### Principe

Le serveur MCP Discord permet d'envoyer des messages et lire l'historique via un bot Discord.

**Flow** :
```
Claude Desktop → MCP Server Discord (node) → API Discord → Serveur Discord → Salons
```

### Bloc `mcpServers`

```json
{
  "mcpServers": {
    "discord": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-discord"],
      "env": {
        "DISCORD_BOT_TOKEN": "MTIzNDU2Nzg5MDEyMzQ1Njc4OQ.XXXXXX"
      }
    }
  }
}
```

### Setup côté Discord

1. Créer une application sur [discord.com/developers/applications](https://discord.com/developers/applications)
2. Créer un Bot et copier le token
3. Activer **MESSAGE CONTENT INTENT**
4. Inviter le bot sur le serveur avec les permissions appropriées

### Tools exposés

| Tool | Description |
|------|-------------|
| `send-message` | Envoie un message dans un salon |
| `read-messages` | Lit les messages récents |

### Démo

> "Envoie le message '🐺 Test MCP réussi !' dans le salon #general"

---

## 🔌 CONNECTEUR 5 : AIRTABLE

### Principe

Airtable expose une API REST. Le serveur MCP Airtable permet de lire et modifier des enregistrements.

**Flow** :
```
Claude Desktop → MCP Server Airtable (npx) → API Airtable (api.airtable.com) → Bases/Tables
```

### Bloc `mcpServers`

```json
{
  "mcpServers": {
    "airtable": {
      "command": "npx",
      "args": ["-y", "mcp-server-airtable", "--baseId", "appXXXXXXXXXXXX"],
      "env": {
        "AIRTABLE_API_KEY": "patXXXXXXXXXXXXXXXX"
      }
    }
  }
}
```

### Setup côté Airtable

1. Créer un PAT sur [airtable.com/create/tokens](https://airtable.com/create/tokens)
2. Scopes : `data.records:read`, `data.records:write`, `schema.bases:read`
3. Récupérer le Base ID depuis l'URL de la base

### Tools exposés

| Tool | Description |
|------|-------------|
| `list_records` | Liste les enregistrements |
| `create_record` | Crée un enregistrement |
| `update_records` | Met à jour des enregistrements |
| `search_records` | Recherche textuelle |

### Démo

> "Ajoute un nouveau contact 'Wolf Test' dans ma table Contacts"

---

## 🔌 CONNECTEUR 6 : OPENAI / CHATGPT

### Principe

Ce connecteur permet à Claude d'appeler l'API OpenAI via un serveur MCP proxy.

**Flow** :
```
Claude Desktop → MCP Server OpenAI (node) → API OpenAI (api.openai.com) → GPT-4/GPT-4o
```

### Bloc `mcpServers`

```json
{
  "mcpServers": {
    "openai": {
      "command": "npx",
      "args": ["-y", "@anthropic/mcp-server-openai"],
      "env": {
        "OPENAI_API_KEY": "sk-XXXXXXXXXXXXXXXX"
      }
    }
  }
}
```

### Setup côté OpenAI

1. Créer une API Key sur [platform.openai.com/api-keys](https://platform.openai.com/api-keys)
2. S'assurer d'avoir des crédits disponibles

### Tools exposés

| Tool | Description |
|------|-------------|
| `chat_completion` | Appelle GPT pour une completion |

### Démo

> "Demande à GPT-4 de me donner 5 idées de noms pour une startup IA"

---

## 📊 ARCHITECTURE FINALE

```
┌─────────────────────────────────────────────────────────────────┐
│                      CLAUDE DESKTOP                              │
│                    (claude_desktop_config.json)                  │
└───────────────────────────┬─────────────────────────────────────┘
                            │
            ┌───────────────┼───────────────┐
            │               │               │
            ▼               ▼               ▼
    ┌───────────┐   ┌───────────┐   ┌───────────┐
    │  n8n MCP  │   │ Notion MCP│   │ GitHub MCP│
    └─────┬─────┘   └─────┬─────┘   └─────┬─────┘
          │               │               │
          ▼               ▼               ▼
    ┌───────────┐   ┌───────────┐   ┌───────────┐
    │  n8n API  │   │Notion API │   │GitHub API │
    └───────────┘   └───────────┘   └───────────┘

            ┌───────────────┼───────────────┐
            │               │               │
            ▼               ▼               ▼
    ┌───────────┐   ┌───────────┐   ┌───────────┐
    │Discord MCP│   │Airtable   │   │OpenAI MCP │
    └─────┬─────┘   │   MCP     │   └─────┬─────┘
          │         └─────┬─────┘         │
          ▼               ▼               ▼
    ┌───────────┐   ┌───────────┐   ┌───────────┐
    │Discord API│   │Airtable   │   │OpenAI API │
    └───────────┘   │   API     │   └───────────┘
                    └───────────┘
```

---

> 🐺 **Wolf Lab × ProNeXus™**
