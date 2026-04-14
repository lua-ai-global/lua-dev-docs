# lua-dev-docs — Public Documentation for Lua CLI

This is the **public-facing** documentation site for `lua-cli`, built with [Mintlify](https://mintlify.com). It is a separate repo from `lua-core-services` (where `lua-cli` source lives).

## Critical Rule: No Internal Details

`lua-cli` is a **private** repository. This repo is **public**. Never include:

- Internal function/variable names (`getKeytar`, `replaceApiKey`, `persistApiKey`, `withErrorHandling`)
- Internal error codes or Node.js internals (`MODULE_NOT_FOUND`, `clearTimeout`, `ESM interop`)
- Internal ticket IDs as root causes (okay as feature refs like `(BAC-131)` if already established in existing entries)
- Internal packaging details (`58MB from node_modules`, workspace dependency resolution, pnpm hoisting)
- Internal architecture details (bundler internals, handler hierarchy, plugin system, compiler pipeline)
- Internal file paths or module structure (`src/services/auth.ts`, `src/utils/cli.ts`)

Write **what changed for the user**, not how it was implemented.

## Structure

```
lua-dev-docs/
├── docs.json              # Mintlify site config (navigation, theme, metadata)
├── index.mdx              # Landing page
├── overview.mdx           # Platform overview
├── CHANGELOG.md           # Public changelog (Keep a Changelog format)
├── changelog.mdx          # Public changelog (Mintlify AccordionGroup format)
├── cli/                   # CLI command documentation
│   ├── overview.mdx
│   ├── authentication.mdx
│   ├── skill-management.mdx
│   ├── production-command.mdx
│   ├── troubleshooting.mdx
│   └── ...
├── getting-started/       # Quickstart and installation guides
├── concepts/              # Platform concepts (agents, skills, workflows)
├── api/                   # REST API reference
├── chat-widget/           # Embeddable chat widget docs
├── channels/              # Messaging channel integrations
├── integrations/          # Third-party integrations
└── examples/              # Code examples
```

## Changelog Format

There are two changelog files that must be updated together for every `lua-cli` release:

### `CHANGELOG.md` — Keep a Changelog format

```markdown
## [X.Y.Z] - YYYY-MM-DD

### Features
- **Feature title (TICKET-ID)** — User-facing description of what's new.

### Improvements
- **Improvement title** — What's better for the user.

### Bug Fixes
- **Fix title** — What was broken, now fixed.
```

### `changelog.mdx` — Mintlify AccordionGroup format

```mdx
## vX.Y.Z

**Released:** Month Day, Year

### ✨ New Features

<AccordionGroup>
  <Accordion title="Feature title (TICKET-ID)">
    User-facing description with code examples.

    ```bash
    lua new-command --flag
    ```
  </Accordion>
</AccordionGroup>

### 🐛 Bug Fixes

<AccordionGroup>
  <Accordion title="Fix title">
    What was broken and how it's fixed from the user's perspective.
  </Accordion>
</AccordionGroup>
```

Section emoji conventions: `✨` New Features, `🔧` Improvements, `🐛` Bug Fixes.

## Development

```bash
# Install dependencies
npm install

# Run local dev server (Mintlify)
npx mintlify dev

# Preview at http://localhost:3000
```

## Relationship to `lua-cli` Releases

This repo is updated as part of every `lua-cli` release. See `lua-core-services/packages/lua-cli/CLAUDE.md` → "Release Process" for the full checklist. The relevant steps for this repo are:

1. Write user-facing changelog entries in both `CHANGELOG.md` and `changelog.mdx`
2. Update any `.mdx` pages affected by the release (new commands, changed behavior, new options)
3. Commit and push separately (this is not part of the monorepo)
