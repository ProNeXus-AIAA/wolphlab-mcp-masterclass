# 🐺 CHEATSHEET MCP × WOLF LAB × PRONEXUS™

```
╔══════════════════════════════════════════════════════════════════╗
║            🐺 CHEATSHEET MCP × WOLF LAB × PRONEXUS™              ║
╠══════════════════════════════════════════════════════════════════╣
║                                                                  ║
║  📍 FICHIER CONFIG CLAUDE DESKTOP                                ║
║  ─────────────────────────────────                               ║
║  Mac:     ~/Library/Application Support/Claude/                  ║
║           claude_desktop_config.json                             ║
║  Windows: %APPDATA%\Claude\claude_desktop_config.json            ║
║                                                                  ║
║  📍 STRUCTURE mcpServers                                         ║
║  ─────────────────────────                                       ║
║  {                                                               ║
║    "mcpServers": {                                               ║
║      "nom_serveur": {                                            ║
║        "command": "npx|node|python",                             ║
║        "args": ["..."],                                          ║
║        "env": { "API_KEY": "xxx" }                               ║
║      }                                                           ║
║    }                                                             ║
║  }                                                               ║
║                                                                  ║
║  📍 CONNECTEURS RAPIDES                                          ║
║  ──────────────────────                                          ║
║  n8n       : npx mcp-remote <URL_SSE>                            ║
║  Notion    : npx @notionhq/notion-mcp-server                     ║
║  GitHub    : npx @modelcontextprotocol/server-github             ║
║  Airtable  : npx mcp-server-airtable                             ║
║  Discord   : npx @modelcontextprotocol/server-discord            ║
║  OpenAI    : npx @anthropic/mcp-server-openai                    ║
║                                                                  ║
║  📍 VARIABLES D'ENVIRONNEMENT                                    ║
║  ────────────────────────────                                    ║
║  NOTION_API_KEY          → Integration Token Notion              ║
║  GITHUB_PERSONAL_ACCESS_TOKEN → PAT GitHub (repo, issues)        ║
║  AIRTABLE_API_KEY        → Personal Access Token Airtable        ║
║  DISCORD_BOT_TOKEN       → Token Bot Discord                     ║
║  OPENAI_API_KEY          → Clé API OpenAI                        ║
║                                                                  ║
║  📍 DEBUG                                                        ║
║  ───────                                                         ║
║  1. Vérifier que le serveur MCP apparaît dans Claude Desktop     ║
║     (Settings > MCP)                                             ║
║  2. Relancer Claude Desktop après modif config                   ║
║  3. Logs : ~/Library/Logs/Claude/ (Mac)                          ║
║  4. Tester le serveur en standalone avant Claude                 ║
║                                                                  ║
║  📍 COMMANDES DE TEST                                            ║
║  ─────────────────────                                           ║
║  n8n     : "Utilise le tool hello_pnx"                           ║
║  Notion  : "Crée une page 'Test MCP' dans Notion"                ║
║  GitHub  : "Liste mes repos GitHub"                              ║
║  Discord : "Envoie 'Hello' dans #general"                        ║
║  Airtable: "Ajoute un contact 'Test' dans ma table"              ║
║  OpenAI  : "Demande à GPT de résumer ce texte"                   ║
║                                                                  ║
║  📍 RESSOURCES                                                   ║
║  ───────────                                                     ║
║  Repo officiel : github.com/modelcontextprotocol                 ║
║  Awesome MCP   : github.com/punkpeye/awesome-mcp-servers         ║
║  Docs Claude   : docs.anthropic.com/claude/docs/mcp              ║
║                                                                  ║
╠══════════════════════════════════════════════════════════════════╣
║  🐺 Wolf Lab × ProNeXus™ – "Claude parle à tes outils"           ║
╚══════════════════════════════════════════════════════════════════╝
```

---

> 🐺 **Wolf Lab × ProNeXus™**
