# Developer Setup Guide

Quick setup guide for engineers working on Lua documentation.

## Prerequisites

- **Node.js** 16+ and npm
- **Git** for version control
- **Code editor** (VS Code recommended)

## Initial Setup

### 1. Clone Repository

```bash
git clone <repository-url>
cd mintlify-docs
```

### 2. Install Mintlify CLI

**npm:**
```bash
npm install -g mintlify
```

**yarn:**
```bash
yarn global add mintlify
```

**pnpm:**
```bash
pnpm add -g mintlify
```

**Or use package.json script:**
```bash
npm run install-cli
```

Verify installation:
```bash
mintlify --version
```

### 3. Start Development Server

```bash
mintlify dev
# or
npm run dev
```

Open http://localhost:3000 to view documentation.

## Development Environment

### Recommended VS Code Extensions

1. **MDX** - MDX language support
2. **Mintlify** - Official Mintlify extension
3. **Prettier** - Code formatting
4. **ESLint** - Linting
5. **GitLens** - Git integration

### VS Code Settings

Create `.vscode/settings.json`:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "files.associations": {
    "*.mdx": "mdx"
  },
  "[mdx]": {
    "editor.wordWrap": "on"
  }
}
```

## Project Structure Quick Reference

```
mintlify-docs/
├── docs.json              # ⚙️ Main config - navigation & theme
├── index.mdx             # 🏠 Homepage
├── README.md             # 📖 This guide
├── CONTRIBUTING.md       # 🤝 Contribution guidelines
├── CHANGELOG.md          # 📝 Version history
│
├── getting-started/      # 🚀 Onboarding (3 pages)
├── concepts/             # 💡 Core concepts (4 pages)
├── cli/                  # ⌨️  CLI commands (5 pages)
├── api/                  # 📚 API reference (9 pages)
├── template/             # 📦 Template guide (5 pages)
├── examples/             # 💼 Tool examples (7 pages)
└── chat-widget/          # 💬 Widget docs (12 pages)
```

## Common Tasks

### Add a New Page

```bash
# 1. Create the file
touch section-name/new-page.mdx

# 2. Add frontmatter
cat > section-name/new-page.mdx << 'EOF'
---
title: "Page Title"
description: "Page description"
---

## Content here
EOF

# 3. Add to docs.json navigation
# Edit docs.json and add "section-name/new-page" to appropriate group

# 4. Test locally
mint dev
```

### Update Existing Content

```bash
# 1. Find the file
# Example: api/data.mdx

# 2. Edit content
code api/data.mdx

# 3. Preview changes
# Save file, dev server auto-reloads

# 4. Commit
git add api/data.mdx
git commit -m "docs: improve Data API examples"
git push
```

### Change Navigation

```bash
# 1. Edit docs.json
code docs.json

# 2. Update navigation.tabs array

# 3. Test locally
mint dev

# 4. Verify all pages load

# 5. Commit
git add docs.json
git commit -m "docs: reorganize navigation"
```

### Update Branding

```bash
# Colors in docs.json
"colors": {
  "primary": "#8B5CF6",
  "light": "#A78BFA",
  "dark": "#7C3AED"
}

# Logos in /logo/ directory
# Replace light.png and dark.png

# Favicon at root
# Replace favicon.png
```

## Testing Checklist

Before committing:

- [ ] `mint dev` runs without errors
- [ ] All new pages load correctly
- [ ] No broken links (`mint broken-links`)
- [ ] Code examples are correct
- [ ] Mobile view works (resize browser)
- [ ] Search finds new content
- [ ] Images load properly
- [ ] No console errors (F12)

## Debugging

### Common Issues

**Port 3000 in use:**
```bash
lsof -ti:3000 | xargs kill -9
mint dev
```

**Invalid docs.json:**
```bash
# Validate JSON syntax
cat docs.json | python -m json.tool
# or
jq . docs.json
```

**Page not appearing:**
- Check file path in docs.json matches actual file
- Verify frontmatter is valid YAML
- Check for MDX syntax errors

**Styling broken:**
- Check Mintlify component syntax
- Verify all tags are closed
- Check for unclosed code blocks

## Mintlify CLI Commands

```bash
# Development
mint dev                    # Start dev server
mint dev --port 3001       # Use different port

# Building
mint build                  # Build for production

# Utilities
mint broken-links          # Check for broken links
mint --version             # Check Mintlify version
mint --help                # Show all commands
```

## Git Workflow

### Branch Naming

```bash
# Features
git checkout -b feat/add-webhooks-docs

# Fixes
git checkout -b fix/broken-link-in-api

# Documentation
git checkout -b docs/improve-examples

# Refactoring
git checkout -b refactor/reorganize-cli-section
```

### Commit Messages

Follow conventional commits:

```bash
# Adding content
git commit -m "feat: add webhook integration guide"

# Fixing errors
git commit -m "fix: correct API endpoint in example"

# Updating docs
git commit -m "docs: improve quick start clarity"

# Styling changes
git commit -m "style: format code examples"

# Breaking changes
git commit -m "feat!: restructure navigation"
```

## File Naming Conventions

### Pages (.mdx files)
- **Use kebab-case**: `my-new-page.mdx` ✅
- **Be descriptive**: `voice-chat.mdx` ✅
- **Avoid abbreviations**: `configuration.mdx` not `config.mdx` ✅
- **Match content**: filename reflects page content ✅

### Directories
- **Lowercase**: `chat-widget/` ✅
- **Descriptive**: `getting-started/` ✅
- **Hyphenated**: `api-reference/` ✅

### Images
- **Descriptive names**: `cli-workflow-diagram.png` ✅
- **Lowercase**: `logo.png` ✅
- **Include dimensions**: `hero-1200x600.png` (optional) ✅

## Performance Optimization

### Image Optimization

```bash
# Optimize images before adding
# Use tools like:
# - TinyPNG (https://tinypng.com)
# - ImageOptim (Mac)
# - Squoosh (https://squoosh.app)

# Keep images under:
# - Screenshots: < 200KB
# - Logos: < 50KB
# - Icons: < 10KB
```

### Page Load Time

- Keep pages under 100KB when possible
- Lazy load images when appropriate
- Minimize large code blocks
- Use collapsible sections (Accordions) for long content

## 🔐 Security

### What NOT to Commit

- ❌ API keys or tokens
- ❌ Private agent IDs (use placeholders)
- ❌ User data or emails
- ❌ Internal URLs or endpoints
- ❌ `.env` files

### What's Safe to Commit

- ✅ Example/placeholder IDs
- ✅ Public documentation
- ✅ Open source code examples
- ✅ Generic configurations
- ✅ `.env.example` files

## 📚 Resources

### Mintlify Documentation
- **Quickstart**: https://mintlify.com/docs/quickstart
- **Components**: https://mintlify.com/docs/components
- **Configuration**: https://mintlify.com/docs/settings
- **Deployment**: https://mintlify.com/docs/deployment

### Internal Resources
- **README.md** - Main developer guide (this file)
- **CONTRIBUTING.md** - Contribution guidelines
- **CHANGELOG.md** - Version history
- **DEVELOPER_NOTES.md** - Internal notes and decisions

### Style Guides
- **Mintlify Style Guide**: https://mintlify.com/docs/content/text
- **MDX Documentation**: https://mdxjs.com/
- **Conventional Commits**: https://www.conventionalcommits.org/

## 🆘 Getting Help

### Internal
1. Check **DEVELOPER_NOTES.md** for architecture decisions
2. Check **CONTRIBUTING.md** for contribution guidelines
3. Ask in team chat/Slack

### External
1. **Mintlify Docs**: https://mintlify.com/docs
2. **Mintlify Community**: https://mintlify.com/community
3. **GitHub Issues**: For bugs and questions

## ✅ Onboarding Checklist

New team member checklist:

- [ ] Clone repository
- [ ] Install Mintlify CLI
- [ ] Run `mint dev` successfully
- [ ] Read README.md (this file)
- [ ] Read CONTRIBUTING.md
- [ ] Browse documentation locally
- [ ] Understand navigation structure
- [ ] Know where each type of content goes
- [ ] Can add a new page
- [ ] Can update existing page
- [ ] Understand commit conventions
- [ ] Know how to test changes

## 📊 Documentation Stats

- **Total Pages**: 46 MDX files
- **Navigation Tabs**: 2 (CLI, Chat Widget)
- **Groups**: 9 content groups
- **Code Examples**: 200+ working examples
- **Supported Languages**: TypeScript, JavaScript, HTML, CSS, Bash, YAML
- **Supported Frameworks**: React, Vue, Angular, Next.js, Svelte, Nuxt

---

## Quick Commands Reference

```bash
# Development
npm run dev              # Start dev server
mint dev                 # Same as above

# Testing
mint broken-links        # Check for broken links

# Installation
npm run install-cli      # Install Mintlify globally

# Git workflow
git checkout -b feat/my-feature
# Make changes
git add .
git commit -m "feat: describe changes"
git push origin feat/my-feature
# Create pull request
```

---

**Questions?** See [CONTRIBUTING.md](./CONTRIBUTING.md) or ask the team!

