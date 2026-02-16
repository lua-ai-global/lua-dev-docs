# Changelog

All notable changes to the Lua documentation will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [3.5.0-alpha.7] - 2026-02-16

### Updated - Documentation for lua-cli v3.5.0-alpha.7 (Alpha Release)

#### Bug Fixes
- **Email channel creation** - Aligned with updated API schema: mode selection (generated inbox or existing email forwarding), `name` renamed to `displayName`, and both response types handled correctly (LUA-122)

#### Interface Changes
- Added `EmailChannelMode` type (`'generated' | 'existing'`)
- Added `CreateGeneratedEmailChannelResponse` and `CreateExistingEmailChannelResponse` interfaces
- Updated `CreateEmailChannelRequest.email` to use `{ mode, displayName, email? }`

---

## [3.5.0-alpha.6] - 2026-02-11

### Updated - Documentation for lua-cli v3.5.0-alpha.6 (Alpha Release)

#### New Features Documented
- **Variable references in primitive config** - Properties like `schedule`, `retry`, `tools`, and resolver functions can now be defined using variables, imports, and expressions (not just inline literals)
- **Complete `push all`** - Now includes persona and source backup in addition to all primitives, agents, and MCP servers. Persona is deployed when `--auto-deploy` is set

#### Bug Fixes
- **Agent config arrays with variables** - Defining `jobs: MY_JOBS` or `tools: MY_TOOLS` via variables no longer silently produces an empty agent. Also fixes `skill.addTools(MY_TOOLS)`
- **Webhook `headerSchema`** - Header validation schemas are now correctly pushed to the server (was silently dropped due to key mapping bug)

---

## [3.5.0-alpha.5] - 2026-02-10

### Updated - Documentation for lua-cli v3.5.0-alpha.5 (Alpha Release)

#### New Features Documented
- **Auto-Add `dist-v2/` to `.gitignore`** - Automatically added on compile and init
  - New projects via `lua init` include it in template `.gitignore`
  - Existing projects get it added after first successful compilation
  - Creates `.gitignore` if missing; idempotent

#### Performance Improvements
- **Parallel server sync** during compilation (6 sequential HTTP calls → parallel)
- **Batch version checks** in `lua push all` (one call per type instead of per entity)
- **Lazy authentication** — no upfront validation call; first API call validates

#### Bug Fixes
- **Tool condition regression** — tools without `condition()` no longer fail with "Tool condition evaluation failed"
- **MCP server push** — fixed detection, manifest metadata, and push pipeline (3 bugs)
- **Auth error handling** — `AuthenticationError` properly propagated during sync; 403 handling added
- **Compile sync** — fixed stale config bug where handlers overwrote each other's IDs

---

## [3.5.0-alpha.4] - 2026-02-09

### Updated - Documentation for lua-cli v3.5.0-alpha.4 (Alpha Release)

#### New Features Documented
- **Project Backup & Restore** - Back up and restore project source files
  - `lua push backup` for cloud backup with content-addressed deduplication
  - `lua init --agent-id X --restore-sources` for full project recovery
- **CI/CD Mode** - New `--ci` global flag for non-TTY environments
  - Fails loudly on missing required flags instead of silently canceling
  - Auto-detects non-TTY and warns about potential prompt issues
- **`lua agents` Command** - List all organizations and agents with `--json` output
- **Non-Interactive Sandbox Views** - `lua persona sandbox view` and `lua skills sandbox view`

#### Breaking Changes
- **Push flag renamed**: `--version` → `--set-version`
- **Compile sync default changed**: `--no-sync` (opt-out) → `--sync` (opt-in)
- **New compile flag**: `--verbose` for detailed output

#### Improvements
- Push `--force` now checks server for highest version to avoid conflicts
- Sync command compiles before checking drift for accurate comparison
- Chat preprocessor block now shows response text instead of empty response
- Improved error messages through centralized error handling

---

## [3.5.0-alpha.3] - 2026-02-04

### Updated - Documentation for lua-cli v3.5.0-alpha.3 (Alpha Release)

#### New Features Documented
- **Webhook Triggers for Integrations** - Event-driven triggers that wake up your agent
  - `--triggers` flag for specifying events (e.g., `task_task.created,task_task.updated`)
  - `--custom-webhook` and `--hook-url` flags for custom webhook URLs
  - Triggers pre-selected by default in interactive mode
  - Friendly labels for OAuth scopes and webhook events
- **Webhooks List JSON Output** - `lua integrations webhooks list --json` for scripting
- **Webhook IDs in List Output** - IDs now displayed for easier deletion

#### Improvements
- Push command: correct HTTP methods and improved error handling
- Automated push & deploy with `--force --auto-deploy` flags
- Terminology update: "Integration" instead of "Account", "Trigger" instead of "Webhook Subscription"

#### Bug Fixes
- Trigger preservation when updating connection scopes (per-trigger hookUrl and interval restored)

---

## [3.5.0-alpha.2] - 2026-01-30

### Updated - Documentation for lua-cli v3.5.0-alpha.2 (Alpha Release)

#### New Features Documented
- **Integrations Command** - Connect 250+ third-party services via Unified.to
  - `lua integrations connect` - OAuth and API token authentication
  - `lua integrations list` - View connected accounts
  - `lua integrations webhooks` - Manage webhook subscriptions
  - `lua integrations mcp` - Manage MCP servers for connections
- **MCP and Mastra Log Types** - New `--type mcp` and `--type mastra` options in logs command
- **User ID Filtering in Logs** - `--user-id` option for filtering logs by user
- **Non-Interactive Configure** - `--api-key`, `--email`, `--otp` options for CI/CD and automation
- **Post-Process Display** - Post-processed responses now shown in chat streaming

#### Improvements
- Sync command refactored with dedicated endpoints for name/persona updates
- `--force-sync` flag removed (sync is now default behavior)

#### Bug Fixes
- Marketplace filtering for approved versions only
- PreProcessor test handling fixed for object format

#### Interface Changes
- Added `MCPServerSource` enum for tracking MCP server origin
- Added `'mcp'` and `'mastra'` to log type enums

---

## [3.5.0-alpha.1] - 2026-01-23

### Updated - Documentation for lua-cli v3.5.0-alpha.1 (Alpha Release)

#### New Features Documented
- **User Lookup by Email or Phone** - `User.get()` now supports email/phone lookup
  - `User.get({ email: 'customer@example.com' })` - Look up by email
  - `User.get({ phone: '+1234567890' })` - Look up by phone (with or without + prefix)
  - Returns `null` instead of throwing when user not found
  - Useful for webhooks receiving contact info from external systems

#### Interface Changes
- Added `UserLookupOptions` interface for email/phone lookup
- Updated `User.get()` return type to `UserDataInstance | null`
- Exported `UserLookupOptions` and `ProfileResponse` types

---

## [3.4.0] - 2026-01-22

### Updated - Documentation for lua-cli v3.4.0

#### New Features Documented
- **Non-Destructive Compile Sync** - `lua compile` now warns about orphaned primitives instead of auto-deleting
  - Safer workflow: orphaned skills/webhooks/jobs/MCP servers show warnings
  - Only CLI-sourced skills trigger warnings (not marketplace or manual)
- **Delete Commands** - New explicit commands for removing primitives
  - `lua skills delete --skill-name <name>`
  - `lua webhooks delete --webhook-name <name>`
  - `lua jobs delete --job-name <name>`
  - Interactive confirmation with `--force` flag for automation
- **Streamable HTTP MCP Transport** - Modern MCP transport (spec 2025-03-26)
  - New `transport: 'streamable-http'` option for MCP servers
  - Recommended over legacy `sse` transport for new integrations
  - stdio transport removed (not supported yet in production)

#### Bug Fixes
- Fixed crash when pushing primitives without version field (first push)

#### Interface Changes
- Added `MCPStreamableHttpServerConfig` interface
- Updated `MCPTransport` type to `'sse' | 'streamable-http'`
- Added `SkillSource` type for tracking skill origin

---

## [3.3.0] - 2026-01-20

### Updated - Documentation for lua-cli v3.3.0

#### New Features Documented
- **Non-Interactive Mode** - Complete automation support for all CLI commands
  - Consistent option naming patterns (`--<entity>-name`, `--<entity>-version`)
  - `--force` flag for dangerous operations
  - `--json` flag for machine-readable output
  - Action arguments for entity management
- **User Message and Agent Response Logs** - Filter logs by `user_message` and `agent_response` types
- **MCP Server Environment Resolution** - Function-based `env()` API in MCP configs
- **Products.get() Filter Support** - New filter options with backward compatibility

#### Improvements
- Chat works without mandatory skills
- Better error handling and visual feedback in CLI

#### Bug Fixes
- Normalized action handling for case-insensitive commands

---

## [3.2.0] - 2026-01-13

### Updated - Documentation for lua-cli v3.2.0

#### New Features Documented
- **Sync Command** - `lua sync` for drift detection between server and local code
- **Chat Clear Command** - `lua chat clear` to clear conversation history
- **Lua Runtime API** - `Lua.request.channel` for channel identification
- **Lua.request.webhook** - Access raw webhook payloads in tool execute functions
- **Marketplace Pagination** - Browse skills with page navigation

#### Improvements
- Simplified agent creation flow
- Better TypeScript path alias support

#### Bug Fixes
- Fixed sync command drift detection issues
- Fixed skill publishing
- Fixed compilation for inline skill definitions

---

## [3.0.0] - 2025-12-07

### Updated - Documentation for lua-cli v3.1.0

#### New Features Documented
- **MCP Server Support** - `LuaMCPServer` class, `lua mcp` command
- **Tool Conditions** - Dynamic tool availability with `condition()` function
- **CDN API** - File upload and retrieval
- **Jobs API Enhancements** - `Jobs.getAll()`, `job.activate()`, `job.deactivate()`, `job.trigger()`
- **Evaluations Dashboard** - `lua evals` command
- **Templates API** - WhatsApp template messaging
- **Marketplace CLI** - Discover, install, and publish skills
- **Enhanced Logs Command** - Interactive filtering by primitive type
- **Immutable User Profile** - `user._luaProfile` for read-only core data

#### Breaking Changes Documented
- JobInstance restructured (uses `activeVersion`)
- `welcomeMessage` removed from LuaAgent
- Webhook execute function signature changed to event object
- PreProcessor response redesigned with discriminated union

#### Improvements
- Data API type safety (searchText, Record types)
- PostProcessor simplified return type
- Removed deprecated `async` field from PreProcessor

---

## [2.0.0] - 2025-10-04

### Added - Complete Documentation Rewrite

#### CLI Documentation (34 pages)
- **Getting Started Section**
  - Quick start guide with 5-minute setup
  - Complete installation and authentication guide
  - Task management tutorial (first skill)

- **Core Concepts Section**
  - Skills and tools architecture explained
  - Platform APIs overview (User, Data, Products, Baskets, Orders)
  - Environment variables and configuration management
  - Development workflows and best practices

- **CLI Commands Section**
  - Complete command reference for all CLI commands
  - Authentication commands (configure, key, logout)
  - Skill management (init, compile, test, push, deploy)
  - Development mode with live reload
  - Comprehensive troubleshooting guide

- **API Reference Section**
  - LuaSkill class complete API documentation
  - LuaTool interface implementation guide
  - User API for profile management
  - Data API with vector search capabilities
  - Products API for e-commerce
  - Baskets API for shopping carts
  - Orders API for order management
  - Environment utilities (env function)

- **Template & Examples Section**
  - Template project overview (30+ tools)
  - Project structure and file organization
  - Building custom skills step-by-step
  - Multi-skill project patterns
  - Best practices and professional patterns
  - 7 detailed tool examples (Weather, User Data, Products, Baskets, Custom Data, Payment)

#### Chat Widget Documentation (12 pages)
- **Getting Started**
  - LuaPop introduction with features and benefits
  - 2-minute quick start guide
  - Installation for CDN, NPM, and platforms (WordPress, Shopify, etc.)

- **Configuration**
  - Complete configuration reference with all options
  - Styling and customization guide
  - Events API and callbacks

- **Integration**
  - Framework integration (React, Vue, Angular, Next.js, Svelte)
  - Real-world industry examples (E-commerce, SaaS, Healthcare, Hotels)
  - Migration guides from Intercom, Zendesk, Drift, Tawk.to, LiveChat

- **Advanced Features**
  - Voice chat capabilities and setup
  - Analytics integration (Google Analytics, Mixpanel, Segment)
  - Comprehensive troubleshooting

### Changed
- Simplified navigation from 4 tabs to 2 tabs (CLI, Chat Widget)
- Moved API Reference and Template Guide into CLI tab
- Updated brand colors to match Lua AI purple theme
- Updated logo references to PNG format

### Removed
- Old Mintlify template files and directories
- Example content from template (ai-tools, essentials, etc.)
- Template images and assets
- Generic placeholder content

## [1.0.0] - Previous

### Initial Mintlify Template
- Generic Mintlify starter template
- Placeholder content
- Example pages for reference

---

## Future Planned Changes

### Upcoming
- [ ] Interactive code playground
- [ ] Video tutorials
- [ ] Community-contributed examples
- [ ] Multi-language support
- [ ] API versioning documentation
- [ ] Performance optimization guides
- [ ] Advanced deployment strategies

### Under Consideration
- [ ] GraphQL API documentation (if added to platform)
- [ ] Mobile SDK documentation (if developed)
- [ ] Desktop app documentation (if developed)
- [ ] Enterprise features documentation
- [ ] White-label documentation

---

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md) for how to contribute to this documentation.

## Questions?

- **Discord Community**: [Join our Discord](https://discord.gg/SRPEuwCzaD) - Chat with other builders, get help, discuss ideas, and stay updated with announcements
- **Pull Requests**: For contributions
- **Email**: support@heylua.ai for general questions

