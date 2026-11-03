<p align="center"><img src="assets/logo.png" width="96" alt="AIToURL logo"></p>

# AIToURL — Your AI makes the file. You get the link.

**AIToURL** is a remote MCP server that lets your AI assistant publish files and hand you back a permanent public link. Ask Claude, ChatGPT, Cursor or any MCP client to write a PDF, export an image or package a ZIP — AIToURL hosts it and returns a clean URL you can share anywhere (email, Instagram DMs, Slack, a client portal).

- 🌐 Website: https://aitourl.com
- 🔌 MCP server URL: `https://aitourl.com/mcp`
- 🔐 Auth: OAuth 2.1 (sign in with Google or GitHub, no API key to copy)
- 🆓 Free plan includes MCP access

> This repository is the public presentation of AIToURL (docs, setup, screenshots). The service itself is hosted at aitourl.com.

---

## Why

AI assistants are great at *creating* files — checklists, reports, quotes, e-books — but sharing them is clunky: download, re-upload somewhere, copy a link. AIToURL removes those steps:

> "Write me a launch checklist as a PDF and give me the link."

…and the link arrives in the conversation.

## Connect your AI

The server uses **streamable HTTP** at `https://aitourl.com/mcp`. On first use you'll be redirected to aitourl.com to sign in and approve access (`files:read` / `files:write`).

### Claude (claude.ai, desktop, mobile)
Add a **custom connector** in Claude's connector settings and paste:
```
https://aitourl.com/mcp
```

### Claude Code
```bash
claude mcp add --transport http aitourl https://aitourl.com/mcp
```

### Cursor
In `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):
```json
{
  "mcpServers": {
    "aitourl": {
      "url": "https://aitourl.com/mcp"
    }
  }
}
```

### ChatGPT
Enable **developer mode** in ChatGPT, then add a custom connector with the URL `https://aitourl.com/mcp`. (Availability depends on your ChatGPT plan.)

### Other MCP clients
Any client that supports remote MCP servers with OAuth works — point it at `https://aitourl.com/mcp`.

## Tools

| Tool | What it does |
|---|---|
| `publish_document` | Turns Markdown into a PDF, hosts it, returns the link |
| `import_from_url` | Fetches a file from a URL and hosts it |
| `create_upload_link` / `check_upload` | One-time upload address for larger files |
| `upload_file` | Direct upload for small files (base64) |
| `list_files` / `get_file` | List your files, with size, date and downloads |
| `search_files` | Typo-tolerant search by name, folder, tag and file type |
| `replace_file` | Update a file's content while keeping the same link *(Pro)* |
| `delete_file` | Delete a file; its link stops working |
| `list_folders`, `create_folder`, `move_file`, `rename_folder`, `delete_folder` | Private folders — links never change when you move files *(Pro)* |
| `update_tags` / `list_tags` | Tag files and folders *(adding tags: Pro)* |

## Example prompts

- "Write a one-page onboarding guide for new clients as a PDF and give me a link."
- "Turn this table into a CSV, publish it and send me the URL."
- "List the files I published this week and how many times each was downloaded."
- "Move all my invoices into the folder Clients/Dupont."

## Plans

| | Free | Pro |
|---|---|---|
| MCP access | ✅ | ✅ |
| Files | 100 | More |
| Max file size | 25 MB | Larger |
| Delivery | Download page | Viewed on aitourl.com |
| Folders, tags, replace file | — | ✅ |
| Price | 0 € | 5 €/month or 49 €/year *(coming soon)* |

## Security & privacy

- OAuth 2.1 with PKCE, short-lived access tokens, rotating refresh tokens, instant revocation from your dashboard.
- Files are stored in a private bucket in Europe.
- Abuse reports: abuse@aitourl.com · Contact: contact@aitourl.com

## Screenshots

<!-- Add: conversation with the link, download page, dashboard -->

---

Made in France by Anthony Perinot · https://aitourl.com
