# Documentation project instructions

## About this project

- The customer-facing documentation site for [Kibbu](https://kibbu.io), built on [Mintlify](https://mintlify.com)
- Pages are MDX files with YAML frontmatter; configuration lives in `docs.json`
- A new page is invisible until it is listed in `docs.json` — always add both
- Use the Mintlify MCP server, `https://mcp.mintlify.com`, to edit content and settings via MCP
- Use the Mintlify docs MCP server, `https://www.mintlify.com/docs/mcp`, to query information about using Mintlify via MCP
- For Mintlify product knowledge (components, configuration, writing standards), install the Mintlify skill: `npx skills add https://mintlify.com/docs`

## Terminology

- **Kibbu** — capitalized in prose. Lowercase `kibbu` only when it is literally
  the command, the package, or a key prefix (`kibbu status`, `kibbu_...`).
- **Machine** — never "node". A machine is one computer enrolled in a fleet.
  The word "node" appears nowhere on this site; keep it that way.
- **Fleet** — the set of machines an organization has enrolled.
- **Control plane** — the server the machines and the API clients both talk to.
- **Admin console** — the web UI. Not "dashboard", not "admin panel".
- **Organization** — the tenant boundary. Not "workspace", not "project".

Prefer the word a customer would use over the word the code uses. Internal
identifiers — capability classes, runtime families, engine names, internal
spec or ticket numbers — do not belong in customer prose. If a mechanism
genuinely needs naming, describe what it does.

## Style preferences

- Use active voice and second person ("you")
- Keep sentences concise — one idea per sentence
- Use sentence case for headings
- Bold for UI elements: Click **Settings**
- Code formatting for file names, commands, paths, and code references
- Lead with the answer, then the caveat. State limits plainly rather than
  implying there are none — the existing pages set this tone deliberately.
- Reach for a component when it earns its place: `<Note>` for a caveat that
  changes what the reader does, `<AccordionGroup>` for a set of independent
  questions, `<Steps>` for an ordered procedure, `<CodeGroup>` for the same
  operation in several languages. Prose is the default.

## Content boundaries

**Publish here** — anything a customer needs to use a fleet they do not
maintain the source of: the API surface, client compatibility, error and
status vocabularies, limits, data handling, enrolling a machine, the machine
CLI, and how to report a vulnerability.

**Do not publish here** — these live in the `kibbu` repository and are not
customer documentation: operator runbooks, deployment and infrastructure
topology, architecture decision records, feature specs, security assessments
and pen-test scope, internal benchmarks, and release process.

**Never commit** a real hostname, API key, enrollment token, customer name, or
internal control-plane URL. Use placeholders: `https://<your-control-plane>/v1`,
`$KIBBU_API_KEY`, `$KIBBU_MODEL`. Model ids shown in examples should be read
from `GET /v1/models` by the reader, not hardcoded from our catalog.

## Accuracy

Statements about behavior must match what the shipped control plane and agent
actually do. When the two disagree, the code wins and the page is a bug. Two
places make this easy to get wrong:

- **Error codes and statuses** are a frozen wire contract in the `kibbu`
  repository. Copy them exactly; do not paraphrase a code.
- **Anything unreleased.** Do not document a package, endpoint, or flag that a
  reader cannot use yet — a first step that fails is worse than a missing page.
