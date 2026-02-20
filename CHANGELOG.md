# Changelog

All notable changes to the Lua documentation will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).

## [3.5.0] - 2026-02-20

### Updated - Documentation for lua-cli v3.5.0

#### New Features Documented
- **User Lookup by Email or Phone** - `User.get()` now supports email/phone lookup
  - `User.get({ email: 'customer@example.com' })` - Look up by email
  - `User.get({ phone: '+1234567890' })` - Look up by phone
  - Returns `null` instead of throwing when user not found
- **Integrations Command** - Connect 250+ third-party services via Unified.to
  - `lua integrations connect` - OAuth and API token authentication
  - `lua integrations list` - View connected accounts
  - `lua integrations webhooks` - Manage webhook triggers
  - `lua integrations mcp` - Manage MCP servers for connections
  - Server-side finalization for reliable connection setup
  - Auth URL redirect resolution for seamless OAuth flows
- **Webhook Triggers for Integrations** - Event-driven triggers that wake up your agent
  - `--triggers` flag for specifying events
  - `--custom-webhook` and `--hook-url` flags for custom webhook URLs
  - Triggers pre-selected by default in interactive mode
- **Project Backup & Restore** - `lua push backup` and `lua init --restore-sources`
  - Content-addressed deduplication, S3 direct upload (no size limits)
- **CI/CD Mode** - `--ci` global flag fails loudly on missing required flags
- **`lua agents` Command** - List all organizations and agents with `--json` output
- **`lua update` Command** - Self-update from npm with background outdated version warning
- **Auto-Add `dist-v2/` to `.gitignore`** - Added on compile and init
- **Variable References in Primitive Config** - Variables, imports, and expressions in config properties
- **Complete `push all`** - Now includes persona and source backup
- **MCP and Mastra Log Types** - `--type mcp` and `--type mastra` in logs command
- **User ID Filtering in Logs** - `--user-id` option
- **Non-Interactive Configure** - `--api-key`, `--email`, `--otp` options
- **Non-Interactive Sandbox Views** - `lua persona sandbox view`, `lua skills sandbox view`
- **Post-Process Display** - Post-processed responses shown in chat streaming

#### Performance Improvements
- Parallel server sync during compilation (~3-6s → ~1s)
- Batch version checks in `lua push all`
- Lazy authentication (no upfront validation call)

#### Breaking Changes
- Push flag renamed: `--version` → `--set-version`
- Compile sync default changed: `--no-sync` (opt-out) → `--sync` (opt-in)
- New compile flag: `--verbose` for detailed output

#### Bug Fixes
- Job creation regression from new bundle format (BAC-40)
- Backup "request entity too large" with S3 presigned uploads (BAC-39)
- MCP server duplicate name race condition (BAC-44)
- Email channel creation aligned with API schema (LUA-122)
- Agent config arrays with variables no longer silently empty
- Webhook `headerSchema` key mapping fixed
- Tool condition regression fixed
- MCP server push pipeline (3 bugs) fixed
- Auth error handling improved (403, sync propagation)
- Compile sync stale config fixed
- Marketplace approved-only filtering
- PreProcessor test object format handling

#### Interface Changes
- Added `UserLookupOptions`, `EmailChannelMode`, `MCPServerSource`
- Added `CreateGeneratedEmailChannelResponse`, `CreateExistingEmailChannelResponse`
- Added `'mcp'` and `'mastra'` to log type enums
- Updated `User.get()` return type to `UserDataInstance | null`

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

