# Documentation project instructions

These instructions guide AI agents (and humans) editing the Breadbox documentation site.

## About this project

- This is the documentation site for **Breadbox**, an open-source self-hosted financial data aggregator for households (banks → PostgreSQL → MCP / REST API).
- Built on [Mintlify](https://mintlify.com). Pages are MDX files with YAML frontmatter; site config lives in `docs.json`.
- Source for the product itself lives in a separate repo (`canalesb93/breadbox`); this repo contains only the documentation.
- Run `mint dev` to preview locally, `mint broken-links` to check internal links, and `mint validate` to validate the site builds.

## Terminology

Use the canonical terms below. If you find an older synonym in a page, prefer to update it rather than introduce a new alternative.

- **household** — the group of people sharing one Breadbox instance. Not "team", "organization", or "workspace".
- **family member** — an individual in the household. Not "user" (which is reserved for the dashboard login or API caller).
- **connection** — a link to a financial institution through Plaid, Teller, or a CSV import target. Not "integration" or "account".
- **account** — a single bank/credit/loan/investment account within a connection. Distinct from a connection.
- **sync** — the act of pulling transactions from a provider. Triggered by cron, webhook, or manual action.
- **transaction** — a single posted or pending bank transaction. Amounts follow the Plaid sign convention (positive = debit / money out).
- **rule** — a stored condition + action that auto-categorizes or tags matching transactions on every sync.
- **tag** — a freeform label on a transaction. `needs-review` is the seeded review-queue tag.
- **category** — a node in the two-level category taxonomy. Always referred to by `slug` in code and API examples (e.g., `food-and-drink-groceries`).
- **review queue** — the workflow built around the `needs-review` tag, not a distinct database object.
- **agent** — an AI client connected over MCP (Claude, ChatGPT, Codex, Manus, Openclaw, etc.). Distinct from the human reader.
- **MCP** — Model Context Protocol. Always introduce on first use with `<Tooltip>` if the page hasn't already.
- **API key** — credentials for HTTP MCP and REST API access. Format: `bb_...`. Distinct from provider credentials (Plaid `client_id` / Teller `app_id`).

## Style preferences

- Sentence case for headings — "Getting started", not "Getting Started".
- Active voice and second person ("you"). Avoid "the user" / "the reader".
- One idea per sentence; lead with the goal before the mechanics.
- Bold for UI elements: Click **Settings**.
- Code formatting for file names, commands, paths, env vars, slugs, and code references.
- No marketing language: avoid "powerful", "seamless", "robust", "cutting-edge", "blazing fast".
- No decorative emoji. Emoji are reserved for places where they carry semantic weight (currently: none).
- Em-dashes are fine but don't lean on them — use a period or a colon where they'd otherwise become a tic.
- All code blocks must declare a language tag (\`\`\`bash, \`\`\`json, \`\`\`toml — never bare \`\`\`).
- All `<img>` references must point to files that exist in this repo. Don't ship references to images that haven't been added yet.

## Component preferences

- `<Steps>` for sequential procedures.
- `<Tabs>` to offer alternate paths the reader chooses one of (e.g., transport options, OS variants).
- `<CodeGroup>` for multiple language variants of the same call.
- `<Accordion>` to collapse long response examples or supplementary detail that's not load-bearing for the default scan.
- `<Card>` (in `<Columns cols={2}>`) for next-step landings at the end of overview pages.
- `<Note>` / `<Warning>` / `<Tip>` for callouts — pick by severity (`<Note>` supplementary, `<Tip>` recommended, `<Warning>` for destructive or hard-to-reverse).
- `<Tooltip>` for inline term gloss when a deep dive would derail the sentence.
- `<ParamField>` / `<ResponseField>` for API parameter and field reference. The canonical field list goes at the bottom of each endpoint page; per-endpoint response examples can be collapsed in an Accordion to keep the parameter table scannable.

## Content boundaries

- This repo documents the **user-facing** Breadbox experience: install, onboard, connect a bank, attach an agent, use the API/MCP. Engineering-internal architecture lives in `docs/` in the product repo.
- The public marketing site (breadbox.sh) lives in a separate repo. Hero copy, install one-liner marketing, screenshots-for-social, and OG metadata belong there — not here.
- Don't document internal admin features or DB schema details. The MCP and REST reference pages describe the public surface; everything else stays in the product repo.
- Don't introduce screenshots or images without checking the file exists in the repo first.

## Workflow notes for agents

- Single-PR-per-change is the default. Each PR should be small enough that a human reviewer can read the diff start to finish.
- Run `mint broken-links` before pushing. Fix any broken link the change introduces.
- Branch names: `docs/<topic>` or `docs/polish-iter-NN` for iterative polish loops.
- Mintlify's deployment preview is non-blocking; the only required gate is reviewer approval. PRs may be merged via `gh pr merge --auto --squash` once approved.
