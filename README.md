# ScrapeAtlas Agent Skills

Agent skills for [ScrapeAtlas](https://scrapeatlas.com), the public-data API for
social, video, commerce, community and ad-library platforms. The skills teach an
AI agent to connect to ScrapeAtlas through its hosted MCP server or CLI, choose the
right endpoint, read partial results and failures correctly, paginate with cursors
and keep track of credits.

They work with Claude Code, Cursor, Codex, OpenCode, Gemini CLI and other agents
that load `SKILL.md` files.

## Installation

### Option 1: npx

```bash
# Install all skills
npx skills add OnlineDopamine/scrapeatlas-agent-skills

# Install one skill
npx skills add OnlineDopamine/scrapeatlas-agent-skills --skill scrapeatlas

# List available skills
npx skills add OnlineDopamine/scrapeatlas-agent-skills --list
```

The skills do not connect your agent to ScrapeAtlas on their own. Connect the
[MCP server](https://scrapeatlas.com/mcp/) in your client, or install the CLI with
the `scrapeatlas-setup` skill.

### Option 2: Claude Code plugin

The plugin installs every skill and adds the hosted ScrapeAtlas MCP server
(`https://api.scrapeatlas.com/mcp`).

```bash
/plugin marketplace add OnlineDopamine/scrapeatlas-agent-skills
/plugin install scrapeatlas@scrapeatlas
```

Then open `/mcp`, select the ScrapeAtlas server and sign in to your ScrapeAtlas
account in the browser.

To connect with an API key instead, skip the plugin's server and run:

```bash
claude mcp add --transport http scrapeatlas https://api.scrapeatlas.com/mcp \
  --header "Authorization: Bearer YOUR_API_KEY"
```

### Option 3: Direct link

Give any agent the raw URL of a skill:

```
Load and follow the instructions from:
https://raw.githubusercontent.com/OnlineDopamine/scrapeatlas-agent-skills/main/skills/scrapeatlas/SKILL.md
```

## Available skills

| Skill | What it does |
| --- | --- |
| `scrapeatlas` | Connect through MCP or the CLI, find the right tool, read `status`, `coverage` and failure codes, paginate with cursors and track credits |
| `scrapeatlas-setup` | Install `@scrapeatlas/cli` and authenticate it with an API key in agents that run in their own environment (Hermes, OpenClaw, NanoClaw, Paperclip, Grok bots, servers, CI) |
| `social-profile-snapshot` | Retrieve the profile and recent posts for a handle on several platforms and summarize them |
| `competitor-content-research` | Rank the top posts of a set of accounts by views, likes and comments and compare what they post |
| `trend-scan` | Search a keyword or hashtag on the platforms that support search and summarize the results |

Example prompts:

```
"Get the TikTok profile and latest videos for @khaby.lame"
"Compare the most popular videos from these three YouTube channels"
"What are people posting about #matcha on TikTok, YouTube and Reddit this week?"
```

## Requirements

- A ScrapeAtlas account. Create an API key at https://scrapeatlas.com/dashboard/keys/
  for the CLI or header-based MCP clients; browser sign-in clients do not need one.
- Retrievals spend credits from your account. Each tool description states its
  price; failed calls are free.
- For the CLI: Node.js 22 or newer.

ScrapeAtlas retrieves public data only. It never needs your platform logins,
passwords or cookies, and the skills tell agents never to ask for them or to put
an API key in a prompt or tool argument.

## Repository structure

```
scrapeatlas-agent-skills/
├── .claude-plugin/
│   ├── marketplace.json      # Claude Code marketplace
│   └── plugin.json           # Claude Code plugin manifest
├── .mcp.json                 # Hosted ScrapeAtlas MCP server (HTTP)
└── skills/
    ├── scrapeatlas/                    # Main skill
    ├── scrapeatlas-setup/              # CLI install and authentication
    ├── social-profile-snapshot/        # Recipe
    ├── competitor-content-research/    # Recipe
    └── trend-scan/                     # Recipe
```

## Documentation

- API and endpoint reference: https://scrapeatlas.com/docs/
- MCP server: https://scrapeatlas.com/mcp/
- CLI guide: https://scrapeatlas.com/docs/cli/

## License

[MIT](./LICENSE)

## Support

- Website: https://scrapeatlas.com
- Contact: https://scrapeatlas.com/contact/
- Email: support@scrapeatlas.com
