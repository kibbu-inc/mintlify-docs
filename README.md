# Kibbu documentation

The customer-facing documentation for [Kibbu](https://kibbu.io) — the OpenAI-compatible
control plane that serves AI traffic on the machines your company already owns.

Built on [Mintlify](https://mintlify.com). Pages are MDX with YAML frontmatter;
navigation and theming live in `docs.json`.

## Scope

This site is for **customers**: developers calling the API, and the people who
run a fleet. Operator runbooks, architecture decision records, security
assessments and feature specs live in the main `kibbu` repository and are
deliberately not published here — see `AGENTS.md` for the boundary.

## Layout

| Path | Holds |
| --- | --- |
| `index.mdx`, `quickstart.mdx`, `enroll-a-machine.mdx`, `api-keys.mdx` | Get started |
| `concepts/` | How Kibbu works, fleet and machines, the routing ladder, the admin console |
| `api/` | The `/v1` surface: chat completions, models, embeddings, Kibbu extensions |
| `reference/` | Errors, statuses, client compatibility, limits, data handling, versioning, the machine CLI, security reporting |

## Local preview

```bash
npm i -g mint      # once
mint dev           # run from the repo root, next to docs.json
```

Preview at `http://localhost:3000`. If a page 404s, check it is listed in
`docs.json`; if the CLI misbehaves, `mint update`.

## Publishing

Changes deploy automatically when they land on the default branch, via the
Mintlify GitHub app.

## Editing with an AI tool

```bash
npx skills add https://mintlify.com/docs
```

Installs Mintlify's component reference and writing standards for Claude Code,
Cursor and others. Read `AGENTS.md` first — it carries the terminology and
content boundaries that are specific to Kibbu.
