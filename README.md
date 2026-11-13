# Social Media Agent Skills

Social media research skills for AI agents, powered by
[ScrapeAtlas](https://scrapeatlas.com). Give Claude Code, Codex, Cursor, Gemini
CLI or any agent that reads `SKILL.md` files complete research workflows: find
outlier posts, mine comments, analyze transcripts, tear down competitor ads,
prospect influencers, run social listening and validate product demand.

The data comes from public sources: TikTok, Instagram, YouTube, X (Twitter),
Threads, Bluesky, LinkedIn, Facebook, Reddit, Pinterest, Snapchat, Twitch, the
Meta and LinkedIn ad libraries, TikTok Shop, Amazon, Etsy, Product Hunt,
Hacker News, Quora and 30+ more platforms.

⭐ **Star this repo and claim 1,000 free ScrapeAtlas credits** in your
[dashboard](https://scrapeatlas.com/dashboard/).

## Install

```bash
npx skills add OnlineDopamine/social-media-agent-skills
```

Then connect ScrapeAtlas once, so the skills have data to work with:

```bash
# Claude Code: sign in through the browser, no API key needed
claude mcp add --transport http --scope user scrapeatlas https://api.scrapeatlas.com/mcp
claude mcp login scrapeatlas
```

Other options:

- **Claude Code plugin** (skills + MCP server in one step):
  ```bash
  /plugin marketplace add OnlineDopamine/social-media-agent-skills
  /plugin install scrapeatlas@scrapeatlas
  ```
- **Codex:** `codex mcp add scrapeatlas --url https://api.scrapeatlas.com/mcp`, then `codex mcp login scrapeatlas`.
- **Claude.ai and ChatGPT:** add a custom connector with `https://api.scrapeatlas.com/mcp`.
- **Agents without MCP** (servers, CI, Hermes, OpenClaw): install the CLI with the
  [`scrapeatlas-setup`](skills/scrapeatlas-setup/) skill.

Create an account at [scrapeatlas.com](https://scrapeatlas.com). New accounts
start with free credits.

## Skills

| Skill | Use it to... | You get |
|---|---|---|
| [`outlier-post-finder`](skills/outlier-post-finder/) | Find posts that beat a creator's own baseline on TikTok, Instagram, YouTube, X, LinkedIn and more | Outlier table, repeatable patterns, hooks to test |
| [`comment-mining`](skills/comment-mining/) | Mine comments for questions, objections, pains, buying intent and audience language | Voice-of-customer report with verbatim quotes |
| [`transcript-intelligence`](skills/transcript-intelligence/) | Get and analyze TikTok, YouTube, LinkedIn, Reddit and Meta ad transcripts | Summary, hook, structure, claims, quotes |
| [`competitor-content-research`](skills/competitor-content-research/) | Compare what several competitors post and what performs | Benchmark table, top posts, recurring formats |
| [`ad-library-teardown`](skills/ad-library-teardown/) | Analyze Facebook, Instagram and LinkedIn ads from the ad libraries | Longest-running concepts, angles, offers, test ideas |
| [`trend-scan`](skills/trend-scan/) | Find what people post about a keyword or hashtag right now | Trend summary with cited posts |
| [`influencer-prospecting`](skills/influencer-prospecting/) | Find and vet creators in a niche | Ranked prospect list (CSV) with engagement and fit |
| [`social-listening-brief`](skills/social-listening-brief/) | Find what people say about a brand or topic across Reddit, TikTok, YouTube, LinkedIn, Hacker News and more | Themes, sentiment, cited mentions |
| [`product-demand-research`](skills/product-demand-research/) | Validate an idea with Reddit threads, comments and Amazon, Etsy and TikTok Shop reviews | Demand verdict, pains, willingness to pay |
| [`creator-profile-teardown`](skills/creator-profile-teardown/) | Break down why a creator or brand account works | Positioning, pillars, funnel, copyable playbook |
| [`content-repurposing`](skills/content-repurposing/) | Turn videos and posts into LinkedIn posts, X threads, scripts and newsletters | Ready-to-paste drafts |
| [`social-profile-snapshot`](skills/social-profile-snapshot/) | Get a profile and recent posts for a handle on several platforms | One-page profile summary |
| [`scrapeatlas`](skills/scrapeatlas/) | Call any ScrapeAtlas endpoint directly: profiles, posts, comments, search, ads, listings | Correct tool choice, pagination, honest partial results |
| [`scrapeatlas-setup`](skills/scrapeatlas-setup/) | Install and authenticate the CLI for agents that run in their own environment | A verified connection |

Install one skill:

```bash
npx skills add OnlineDopamine/social-media-agent-skills --skill outlier-post-finder
```

## Example prompts

```text
Find the outlier posts from @starterstory's last 50 YouTube Shorts and tell me which hooks to test.
```

```text
Mine the comments on these 3 TikToks. I want objections, questions and buying intent, in the audience's own words.
```

```text
Tear down Notion's active Facebook and Instagram ads. Which concepts have run the longest and what should we test?
```

```text
Find 20 micro-influencers on TikTok and YouTube who post about home espresso, with engagement rates and public contact links.
```

```text
What are people saying about Linear on Reddit, Hacker News and LinkedIn this month?
```

```text
Is there demand for a dog-walking app for apartment buildings? Use Reddit threads and app reviews.
```

## How the skills fit together

```text
scrapeatlas  (connect, choose tools, read status and coverage, paginate, track credits)
     │
     ▼
research workflows
 ├─ outlier-post-finder        ├─ influencer-prospecting
 ├─ comment-mining             ├─ social-listening-brief
 ├─ transcript-intelligence    ├─ product-demand-research
 ├─ competitor-content-research├─ creator-profile-teardown
 ├─ ad-library-teardown        ├─ content-repurposing
 └─ trend-scan                 └─ social-profile-snapshot
```

## Principles

1. **Workflow first.** You ask for an outcome; the skill picks the endpoints.
2. **Public data only.** ScrapeAtlas never logs in to platforms or asks for your
   platform passwords or cookies.
3. **Cited output.** Every claim links back to the post, video, comment or ad.
4. **Baseline-aware.** Performance is judged against each account's own median.
5. **Honest results.** Partial pages and failures are reported, never hidden.
6. **Credit-aware.** Skills estimate calls before running and report credits used.
   Failed calls are free.

## Repository structure

```
social-media-agent-skills/
├── .claude-plugin/
│   ├── marketplace.json      # Claude Code marketplace
│   └── plugin.json           # Claude Code plugin manifest
├── .mcp.json                 # Hosted ScrapeAtlas MCP server (HTTP)
├── scripts/validate-skills.py
└── skills/<skill-name>/SKILL.md
```

## Links

- [ScrapeAtlas](https://scrapeatlas.com) · [API docs](https://scrapeatlas.com/docs/) · [MCP server](https://scrapeatlas.com/mcp/) · [CLI](https://scrapeatlas.com/docs/cli/)
- Support: https://scrapeatlas.com/contact/ · support@scrapeatlas.com

## License

[MIT](./LICENSE)
