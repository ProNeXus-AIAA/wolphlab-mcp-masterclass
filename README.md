# 🐺 Masterclass MCP × Wolf Lab

> **"Donne des mains à Claude"** – Connecter Claude Desktop à vos outils via Model Context Protocol

[![MCP](https://img.shields.io/badge/MCP-Model%20Context%20Protocol-blue)](https://modelcontextprotocol.io)
[![Claude](https://img.shields.io/badge/Claude-Desktop-orange)](https://claude.ai)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

---

## 🎯 Objectif

Cette masterclass vous apprend à connecter **Claude Desktop** à 6 outils externes via **MCP (Model Context Protocol)** :

| Connecteur | Description | Difficulté |
|------------|-------------|------------|
| 🔄 **n8n** | Orchestrateur d'automations | ⭐ Facile |
| 📝 **Notion** | Workspace collaboratif | ⭐⭐ Moyen |
| 🐙 **GitHub** | Gestion de code | ⭐⭐ Moyen |
| 💬 **Discord** | Communication | ⭐⭐ Moyen |
| 📊 **Airtable** | Base de données | ⭐⭐ Moyen |
| 🤖 **OpenAI** | GPT via proxy MCP | ⭐⭐⭐ Avancé |

---

## 📁 Structure du repo

```
wolphlab-mcp-masterclass/
├── README.md                    # Ce fichier
├── docs/
│   ├── PLAN_MASTERCLASS.md      # Plan détaillé (60-75 min)
│   ├── SCRIPT_LIVE.md           # Script à lire pendant la session
│   ├── SLIDES_STRUCTURE.md      # Structure des 18 slides
│   ├── CONNECTEURS_MCP.md       # Détail des 6 connecteurs
│   └── CHEATSHEET.md            # Résumé 1 page
├── configs/
│   ├── claude_desktop_config.json   # Config complète (template)
│   ├── claude_desktop_config.example.json
│   └── .env.example             # Variables d'environnement
└── demos/
    └── n8n/
        └── hello_pnx_workflow.json  # Workflow n8n de démo
```

---

## 🚀 Quickstart

### 1. Prérequis

- [Claude Desktop](https://claude.ai/download) installé
- Accès aux outils que vous souhaitez connecter
- Tokens/API Keys pour chaque service

### 2. Configuration rapide

```bash
# Cloner le repo
git clone https://github.com/ProNeXus-AIAA/wolphlab-mcp-masterclass.git
cd wolphlab-mcp-masterclass

# Copier le template de config
cp configs/claude_desktop_config.example.json ~/Library/Application\ Support/Claude/claude_desktop_config.json

# Éditer avec vos tokens
open ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

### 3. Tester

1. Relancer Claude Desktop
2. Ouvrir Settings > MCP
3. Vérifier que vos serveurs apparaissent
4. Tester : *"Utilise le tool hello_pnx"*

---

## 📚 Documentation

| Document | Description |
|----------|-------------|
| [Plan Masterclass](docs/PLAN_MASTERCLASS.md) | Structure complète de la session |
| [Script Live](docs/SCRIPT_LIVE.md) | Texte à lire pendant la présentation |
| [Slides Structure](docs/SLIDES_STRUCTURE.md) | Contenu des 18 slides |
| [Connecteurs MCP](docs/CONNECTEURS_MCP.md) | Détail technique de chaque connecteur |
| [Cheatsheet](docs/CHEATSHEET.md) | Résumé 1 page à imprimer |

---

## 🔧 Fichier de config complet

Voir [`configs/claude_desktop_config.json`](configs/claude_desktop_config.json) pour un exemple avec les 6 connecteurs.

**Emplacement du fichier :**
- **Mac** : `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows** : `%APPDATA%\Claude\claude_desktop_config.json`

---

## 🔗 Ressources externes

- [Repo officiel MCP](https://github.com/modelcontextprotocol)
- [Awesome MCP Servers](https://github.com/punkpeye/awesome-mcp-servers)
- [Documentation Anthropic](https://docs.anthropic.com)
- [Présentation Canva](https://www.canva.com/d/GUwYrRKlczSI5Ef)

---

## 🐺 Crédits

**Masterclass créée par :**
- **Oli / ProNeXus™** – Architecte IA & Automatisation
- Pour le **Wolf Lab** 🐺

**Avec le support de :**
- Claude (Anthropic) – Génération de la documentation
- Canva – Création des slides

---

## 📄 Licence

MIT License – Libre d'utilisation et de modification.

---

> *"Claude parle maintenant à vos outils. À vous de jouer."* 🚀
