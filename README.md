# Breadbox documentation

Source for [docs.breadbox.sh](https://docs.breadbox.sh) — the user-facing documentation for [Breadbox](https://github.com/canalesb93/breadbox), an open-source self-hosted financial data aggregator for households.

Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter; site-wide configuration lives in `docs.json`.

## Repo layout

| Path | What it is |
| --- | --- |
| `docs.json` | Site configuration: navigation, theme, colors, banner, redirects. |
| `introduction.mdx`, `installation.mdx`, `quickstart.mdx` | Top-of-funnel pages — "what is Breadbox", install paths, onboarding walkthrough. |
| `connections/` | Per-provider bank-connection guides (Plaid, Teller, CSV import). |
| `transactions/` | Transaction-level concepts: categories, tags, rules, review workflow. |
| `mcp/` | MCP integration guides and reference tool pages. |
| `api/` | REST API reference. |
| `guides/` | End-to-end agent workflows (multi-agent reviewer, Gmail cross-referencing, subscription tracking, etc.). |
| `changelog.mdx` | User-visible changes since the V1 docs launch. |
| `AGENTS.md` | Conventions for AI agents editing this repo — terminology, style, component preferences. |
| `CONTRIBUTING.md` | How humans contribute. |

## Local preview

Install the [Mintlify CLI](https://www.npmjs.com/package/mint):

```bash
npm i -g mint
```

Run the dev server from the repo root (where `docs.json` lives):

```bash
mint dev
```

The preview opens at `http://localhost:3000` with live reload.

Before pushing, check internal links:

```bash
mint broken-links
```

## Deployment

`main` is auto-deployed to [docs.breadbox.sh](https://docs.breadbox.sh) by Mintlify's GitHub app. Open a PR with your changes; the Mintlify Deployment check renders a preview URL on the PR. Merging to `main` ships to production.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the contribution workflow. AI agents (Claude Code, Cursor, Windsurf, etc.) should read [AGENTS.md](./AGENTS.md) before making changes — it captures the terminology, style, and component preferences used across the site.

## Other Breadbox repos

- **[canalesb93/breadbox](https://github.com/canalesb93/breadbox)** — the Breadbox application itself (Go binary, MCP server, REST API, admin dashboard).
- **[breadbox.sh](https://breadbox.sh)** — the public marketing site, in a separate repo.
