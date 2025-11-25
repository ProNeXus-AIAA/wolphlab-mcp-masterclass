# 🎤 SCRIPT MASTERCLASS MCP × WOLF LAB

> Version : 15 min condensé (pour intro + n8n)

---

## INTRO (2 min)

> Salut les Wolves ! 🐺
>
> Aujourd'hui, on va faire quelque chose de puissant : **donner des mains à Claude**.
>
> Vous connaissez Claude – l'IA d'Anthropic. Vous lui posez des questions, il répond. Mais jusqu'ici, Claude était un cerveau **sans corps**. Il ne pouvait pas aller chercher vos données dans Notion, créer un issue GitHub, ou poster dans votre Discord.
>
> Ça, c'était avant **MCP**.
>
> MCP – Model Context Protocol – c'est un protocole standard créé par Anthropic pour permettre à Claude de **parler à des outils externes**. Et aujourd'hui, on va connecter Claude Desktop à :
> - n8n (votre orchestrateur d'automations)
> - Notion
> - GitHub
> - Discord
> - Airtable
> - Et même OpenAI, pour faire parler GPT depuis Claude.
>
> À la fin de cette session, vous saurez reproduire tout ça chez vous.
>
> Let's go. 🚀

---

## ACTE I – LE CONCEPT (3 min)

> **Le problème**, c'est simple : une IA classique est **coupée du monde**. Elle ne voit pas vos fichiers, vos bases de données, vos projets.
>
> **La solution MCP**, c'est de créer un **pont** entre Claude et vos outils.
>
> Imaginez : Claude, c'est le **cerveau**. MCP, c'est le **système nerveux**. Et vos outils – Notion, GitHub, etc. – ce sont les **membres du corps**.
>
> Le cerveau envoie un signal → le système nerveux transmet → le membre agit.
>
> Techniquement, voilà comment ça marche :
> 1. Claude Desktop se connecte à un **serveur MCP** (un petit programme qui tourne en local ou sur un serveur)
> 2. Ce serveur MCP expose des **tools** – des actions que Claude peut appeler
> 3. Quand Claude veut faire une action, il appelle le tool → le serveur MCP fait le job → renvoie le résultat à Claude.
>
> C'est tout. C'est élégant. C'est puissant.

---

## ACTE II – SETUP n8n (8 min)

> On commence par le plus simple : **n8n**.
>
> Pourquoi n8n ? Parce que n8n a un node natif "**MCP Server Trigger**". Vous n'avez pas besoin de coder un serveur. n8n fait tout.
>
> **Étape 1** : Créez un nouveau workflow dans n8n.
>
> Ajoutez un node **MCP Server Trigger**. Dans les settings, vous allez définir un tool. Appelons-le `hello_pnx`. Description : "Dit bonjour depuis n8n".
>
> **Étape 2** : Ajoutez un node **Set** qui retourne un message, par exemple : `"🐺 Hello Wolf Lab depuis n8n !"`.
>
> **Étape 3** : Connectez le tout et **activez** le workflow.
>
> n8n vous donne une **URL SSE** – c'est l'adresse de votre serveur MCP. Copiez-la.
>
> **Étape 4** : Ouvrez le fichier de config de Claude Desktop.
> - Sur Mac : `~/Library/Application Support/Claude/claude_desktop_config.json`
> - Sur Windows : `%APPDATA%\Claude\claude_desktop_config.json`
>
> Ajoutez ce bloc dans `mcpServers` :
>
> ```json
> "n8n": {
>   "command": "npx",
>   "args": ["-y", "mcp-remote", "https://votre-url-n8n.com/mcp/sse"]
> }
> ```
>
> **Étape 5** : Relancez Claude Desktop. Allez dans les settings MCP, vérifiez que "n8n" apparaît.
>
> **Étape 6** : Testez !
>
> Dans Claude, tapez : *"Utilise le tool hello_pnx"*.
>
> Et là… magie. Claude appelle n8n, n8n répond, Claude affiche le message.
>
> Vous venez de faire parler Claude à n8n. **First blood.** 🎉

---

## TRANSITION (1 min)

> Ce qu'on vient de faire avec n8n, on peut le faire avec **n'importe quel outil** qui a un serveur MCP.
>
> Notion, GitHub, Discord, Airtable, OpenAI… chacun a son serveur MCP – soit officiel, soit community.
>
> Le principe est toujours le même :
> 1. Lancer le serveur MCP
> 2. Ajouter le bloc dans `claude_desktop_config.json`
> 3. Tester un tool
>
> On va faire le tour ensemble.

---

## OUTRO SCRIPT COURT (1 min)

> Voilà pour l'intro et le setup de base.
>
> Dans la suite, on détaille chaque connecteur. Mais vous avez compris l'essentiel : **MCP transforme Claude en agent connecté**.
>
> Des questions avant qu'on continue ?

---

> 🐺 **Wolf Lab × ProNeXus™**
