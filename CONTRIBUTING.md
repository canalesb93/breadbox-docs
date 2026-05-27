# Contributing to the Breadbox docs

Thanks for considering a contribution. This repo is the source for [docs.breadbox.sh](https://docs.breadbox.sh) — the user-facing documentation for [Breadbox](https://github.com/canalesb93/breadbox). It's a Mintlify project; pages are MDX with YAML frontmatter and site config lives in `docs.json`.

## What's in scope here

This repo documents how to **use** Breadbox: install, onboard, connect a bank, attach an AI agent, query via REST or MCP, and the agent-workflow guides. Engineering-internal architecture (sync engine internals, database schema, provider interface specs) lives in the [main Breadbox repo](https://github.com/canalesb93/breadbox/tree/main/docs). Marketing content (hero copy, social previews, install screenshots) lives in the breadbox.sh site repo, not here.

For product bugs and feature requests, file in the [main Breadbox repo](https://github.com/canalesb93/breadbox/issues). For documentation-only issues (a typo, an unclear step, a broken link, an outdated screenshot), file [here](https://github.com/canalesb93/breadbox-docs/issues).

## How to contribute

### Option 1: edit on GitHub

Quickest path for small fixes (typos, link corrections, one-paragraph clarifications):

1. Open the page on [docs.breadbox.sh](https://docs.breadbox.sh) and click **Edit this page** (or navigate to the `.mdx` file in GitHub and click the pencil icon).
2. Make your changes; GitHub forks the repo and creates a branch automatically.
3. Open a PR. Mintlify will attach a preview-deployment link to the PR — use it to confirm your change renders correctly.

### Option 2: local development

For anything larger than a one-paragraph edit (new pages, restructuring, adding components):

1. Fork the repo and clone your fork.
2. Install the Mintlify CLI: `npm i -g mint`.
3. Create a branch: `git checkout -b docs/<short-topic>`.
4. From the repo root, run `mint dev` to open a live-reload preview at `http://localhost:3000`.
5. Before pushing, run `mint broken-links` and fix any broken internal links your change introduces. Run `mint validate` if you've added new components.
6. Commit and push. Open a PR against `main`.

Mintlify auto-deploys `main` to docs.breadbox.sh on merge, so changes go live a couple of minutes after the PR lands.

## Writing guidelines

The full agent-and-human style guide lives in [AGENTS.md](./AGENTS.md). The essentials:

- **Active voice and second person.** Write "Run the command" — not "The command should be run" or "We then run the command".
- **Sentence case for headings.** "Getting started", not "Getting Started".
- **One idea per sentence.** Lead with what you're trying to accomplish before the mechanics.
- **Use the canonical terms.** Household, family member, connection, sync, rule, tag, agent — see [AGENTS.md](./AGENTS.md#terminology) for the full list. Don't introduce new synonyms for the same concept.
- **No marketing language.** Avoid "powerful", "seamless", "robust", "blazing fast". Show what the feature does, don't editorialize.
- **No decorative emoji.** Emoji are reserved for places where they carry semantic meaning.
- **Code blocks need language tags.** \`\`\`bash, \`\`\`json, \`\`\`toml — never bare \`\`\`.
- **Images must exist.** Don't ship references to image files that haven't been added to the repo.

## Component preferences

Mintlify provides a strong set of components. Pick by reader intent — see [AGENTS.md → Component preferences](./AGENTS.md#component-preferences) for the full table. The short version:

- `<Steps>` for sequential procedures.
- `<Tabs>` to offer alternate paths the reader chooses one of.
- `<CodeGroup>` for the same call shown in multiple languages.
- `<Accordion>` to collapse long response examples or supplementary detail.
- `<Card>` (inside `<Columns cols={2}>`) for next-step landings at the end of overview pages.
- `<Note>` / `<Tip>` / `<Warning>` for callouts — pick by severity.
- `<ParamField>` / `<ResponseField>` for API parameter and field reference.

## AI agents

If you're an AI agent (Claude Code, Cursor, Windsurf, etc.) making changes here, **read [AGENTS.md](./AGENTS.md) first**. It captures the terminology rules, style preferences, component preferences, and content boundaries that keep the site consistent. Mintlify's docs skill (`npx skills add https://mintlify.com/docs`) provides general Mintlify component and writing guidance — combine the two.

## Need help?

- General Mintlify questions: [Mintlify docs](https://mintlify.com/docs).
- Breadbox product questions: [main Breadbox repo](https://github.com/canalesb93/breadbox).
- Docs-specific questions: open an [issue here](https://github.com/canalesb93/breadbox-docs/issues).
