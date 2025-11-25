# 📋 PLAN MASTERCLASS MCP × WOLF LAB

> **"Donne des mains à Claude"**  
> Durée totale : 60-75 minutes

---

## ACTE I – COMPRENDRE MCP SANS JARGON
**⏱️ Durée : 12 min**

| Section | Contenu | Timing |
|---------|---------|--------|
| **1.1 – Le problème** | L'IA est "aveugle" : elle ne voit pas tes outils (Notion, GitHub, etc.). Elle répond dans le vide. | 3 min |
| **1.2 – La solution MCP** | MCP = Model Context Protocol. Un protocole standard pour que Claude "parle" à des serveurs d'outils. Analogie : Claude = cerveau, MCP = système nerveux, Outils = membres du corps. | 4 min |
| **1.3 – Architecture générale** | Schéma : `Claude Desktop` ↔ `MCP Server` ↔ `API Outil`. Notion de "tools" exposés par le serveur. | 3 min |
| **1.4 – Ce qu'on va faire aujourd'hui** | Connecter Claude Desktop à 6 outils : n8n, Notion, GitHub, Discord, Airtable, OpenAI. | 2 min |

**🎬 Démo** : Aucune (théorie pure)

---

## ACTE II – MISE EN PLACE D'UN EXEMPLE SIMPLE : n8n
**⏱️ Durée : 15 min**

| Section | Contenu | Timing |
|---------|---------|--------|
| **2.1 – Pourquoi n8n en premier ?** | n8n a un node natif "MCP Server Trigger" = zéro code serveur. Parfait pour comprendre le flow. | 2 min |
| **2.2 – Création du workflow n8n** | Créer un workflow avec : MCP Server Trigger → Set (réponse) → Respond. Configurer le tool "hello_pnx". | 5 min |
| **2.3 – Récupérer l'URL MCP** | n8n génère une URL SSE. On la note. | 1 min |
| **2.4 – Configurer Claude Desktop** | Ouvrir `claude_desktop_config.json`, ajouter le bloc `mcpServers` avec `mcp-remote` pointant vers n8n. | 4 min |
| **2.5 – Test live** | Relancer Claude Desktop. Dire : "Utilise le tool hello_pnx". Observer la magie. | 3 min |

**🎬 Démos** :
- Création workflow n8n (screen share)
- Modification `claude_desktop_config.json`
- Test "hello_pnx" dans Claude Desktop

---

## ACTE III – TOUR DES CONNECTEURS PNX
**⏱️ Durée : 30 min**

| Section | Connecteur | Contenu | Timing |
|---------|------------|---------|--------|
| **3.1** | **Notion** | Serveur MCP Notion (officiel ou community). Tool : `search_pages`, `create_page`. Démo : "Crée une page 'Test Wolf Lab' dans ma DB Notion". | 6 min |
| **3.2** | **GitHub** | Serveur MCP GitHub (officiel Anthropic). Tools : `list_repos`, `create_issue`, `get_file_contents`. Démo : "Liste mes repos GitHub". | 5 min |
| **3.3** | **Discord** | Serveur MCP Discord (custom ou community). Tools : `send_message`, `read_messages`. Démo : "Envoie 'Hello Wolf Lab' dans #general". | 5 min |
| **3.4** | **Airtable** | Serveur MCP Airtable. Tools : `list_records`, `create_record`. Démo : "Ajoute un enregistrement 'Test MCP' dans ma table Contacts". | 5 min |
| **3.5** | **OpenAI/ChatGPT** | Serveur MCP custom (Node.js) qui proxyfie vers l'API OpenAI. Tool : `chat_completion`. Démo : "Demande à GPT-4 de résumer ce texte". | 5 min |
| **3.6** | **Récap architecture** | Schéma final avec tous les connecteurs. Comment ils cohabitent dans `mcpServers`. | 4 min |

**🎬 Démos** : 1 démo par connecteur (phrases préparées)

---

## ACTE IV – CAS CONCRETS ET Q&A
**⏱️ Durée : 15-20 min**

| Section | Contenu | Timing |
|---------|---------|--------|
| **4.1 – Use cases Wolf Lab** | Comment utiliser MCP pour : automatiser des posts, gérer des projets, faire du reporting cross-tools. | 5 min |
| **4.2 – Industrialiser** | Gestion des secrets (env vars, fichiers .env). Organisation des serveurs MCP. Logs et debug. | 5 min |
| **4.3 – Ressources** | Liens vers repos MCP officiels, communauté, cheatsheet PNX. | 2 min |
| **4.4 – Q&A** | Questions libres. | 5-10 min |

**🎬 Démo** : Optionnel selon questions

---

## 📊 TIMELINE GLOBALE

```
00:00 ─────── ACTE I : Comprendre MCP (12 min)
00:12 ─────── ACTE II : Setup n8n (15 min)
00:27 ─────── ACTE III : Tour des connecteurs (30 min)
00:57 ─────── ACTE IV : Cas concrets + Q&A (15-20 min)
01:15 ─────── FIN
```

---

> 🐺 **Wolf Lab × ProNeXus™**
