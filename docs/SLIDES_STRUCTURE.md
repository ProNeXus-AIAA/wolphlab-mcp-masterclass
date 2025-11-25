# 📽️ STRUCTURE DES SLIDES – MASTERCLASS MCP × WOLF LAB

> 18 slides pour la présentation
> Lien Canva : https://www.canva.com/d/GUwYrRKlczSI5Ef

---

## SLIDE 1 – TITRE
**🐺 MASTERCLASS MCP × WOLF LAB**
- "Donne des mains à Claude"
- Par Oli / ProNeXus™
- [Date]

---

## SLIDE 2 – AGENDA
**Ce qu'on va voir aujourd'hui**
- Comprendre MCP en 5 min
- Connecter Claude à n8n (démo live)
- Tour des connecteurs : Notion, GitHub, Discord, Airtable, OpenAI
- Cas concrets + Q&A

---

## SLIDE 3 – LE PROBLÈME
**L'IA est aveugle**
- Claude répond bien… mais ne voit pas vos outils
- Pas d'accès à Notion, GitHub, Discord, etc.
- Résultat : vous copiez-collez en permanence

---

## SLIDE 4 – LA SOLUTION : MCP
**Model Context Protocol**
- Protocole standard créé par Anthropic
- Permet à Claude de "parler" à des outils externes
- Open source, extensible, sécurisé

---

## SLIDE 5 – ARCHITECTURE MCP
**Claude = Cerveau | MCP = Système nerveux | Outils = Corps**
- `Claude Desktop` ↔ `MCP Server` ↔ `API Outil`
- Le serveur MCP expose des "tools"
- Claude appelle les tools, récupère les résultats

*(Schéma visuel)*

---

## SLIDE 6 – SETUP n8n (1/3)
**Pourquoi n8n ?**
- Node natif "MCP Server Trigger"
- Zéro code serveur
- Parfait pour comprendre le flow

---

## SLIDE 7 – SETUP n8n (2/3)
**Créer le workflow**
1. MCP Server Trigger → définir tool `hello_pnx`
2. Set → message de réponse
3. Activer → récupérer l'URL SSE

---

## SLIDE 8 – SETUP n8n (3/3)
**Configurer Claude Desktop**
```json
"n8n": {
  "command": "npx",
  "args": ["-y", "mcp-remote", "URL_SSE"]
}
```
- Relancer Claude Desktop
- Tester : "Utilise le tool hello_pnx"

---

## SLIDE 9 – CONNECTEUR NOTION
**Claude ↔ Notion**
- Serveur : `@notionhq/notion-mcp-server`
- Tools : `search_pages`, `create_page`, `update_page`
- Démo : "Crée une page 'Test Wolf Lab' dans Notion"

---

## SLIDE 10 – CONNECTEUR GITHUB
**Claude ↔ GitHub**
- Serveur : `@modelcontextprotocol/server-github` (officiel)
- Tools : `list_repos`, `create_issue`, `get_file_contents`
- Démo : "Liste mes repos GitHub"

---

## SLIDE 11 – CONNECTEUR DISCORD
**Claude ↔ Discord**
- Serveur : MCP Discord (community/custom)
- Tools : `send_message`, `read_messages`
- Démo : "Envoie 'Hello Wolf Lab' dans #general"

---

## SLIDE 12 – CONNECTEUR AIRTABLE
**Claude ↔ Airtable**
- Serveur : `mcp-server-airtable`
- Tools : `list_records`, `create_record`, `search_records`
- Démo : "Ajoute un contact 'Wolf Test' dans ma table"

---

## SLIDE 13 – CONNECTEUR OPENAI
**Claude ↔ GPT (via MCP)**
- Serveur : custom Node.js (proxy vers API OpenAI)
- Tool : `chat_completion`
- Démo : "Demande à GPT-4 de résumer ce texte"

---

## SLIDE 14 – ARCHITECTURE FINALE
**Tous les connecteurs ensemble**
*(Schéma : Claude Desktop au centre, 6 serveurs MCP autour)*
- Chaque serveur = un bloc dans `mcpServers`
- Claude choisit le bon tool automatiquement

---

## SLIDE 15 – INDUSTRIALISER
**Bonnes pratiques**
- Secrets : fichiers `.env`, jamais en dur
- Organisation : 1 serveur = 1 domaine
- Logs : activer le mode debug pour troubleshoot
- Sécurité : limiter les scopes des tokens

---

## SLIDE 16 – RESSOURCES
**Pour aller plus loin**
- Repo officiel MCP : github.com/modelcontextprotocol
- Awesome MCP Servers : github.com/punkpeye/awesome-mcp-servers
- Cheatsheet PNX : [ce repo]
- Discord Wolf Lab : [lien]

---

## SLIDE 17 – Q&A
**Questions ?**
- 🐺 Go !

---

## SLIDE 18 – MERCI
**Merci les Wolves !**
- Oli / ProNeXus™
- Contact : Discord Wolf Lab
- "Claude parle maintenant à vos outils. À vous de jouer."

---

> 🐺 **Wolf Lab × ProNeXus™**
