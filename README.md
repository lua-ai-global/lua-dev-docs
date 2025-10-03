# Lua CLI Documentation

Official documentation for Lua CLI - Build AI agents with custom capabilities using TypeScript.

## 🚀 Quick Start

```bash
# Install dependencies
npm install

# Start local development server
npm run dev
# or
mint dev
```

The documentation will be available at `http://localhost:3000`

## 📁 Documentation Structure

```
mintlify-docs/
├── getting-started/        # Getting started guides
│   ├── quick-start.mdx
│   ├── installation.mdx
│   └── first-skill.mdx
├── concepts/              # Core concepts
│   ├── skills-and-tools.mdx
│   ├── platform-apis.mdx
│   ├── environment-variables.mdx
│   └── workflows.mdx
├── cli/                   # CLI command reference
│   ├── overview.mdx
│   ├── authentication.mdx
│   ├── skill-management.mdx
│   ├── development.mdx
│   └── troubleshooting.mdx
├── api/                   # API reference
│   ├── overview.mdx
│   ├── luaskill.mdx
│   ├── luatool.mdx
│   ├── user.mdx
│   ├── data.mdx
│   ├── products.mdx
│   ├── baskets.mdx
│   ├── orders.mdx
│   └── environment.mdx
├── template/              # Template guide
│   ├── overview.mdx
│   ├── project-structure.mdx
│   ├── building-skills.mdx
│   ├── multi-skill-projects.mdx
│   └── best-practices.mdx
├── examples/              # Tool examples
│   ├── overview.mdx
│   ├── weather.mdx
│   ├── user-data.mdx
│   ├── products.mdx
│   ├── baskets.mdx
│   ├── custom-data.mdx
│   └── payment.mdx
├── docs.json              # Mintlify configuration
├── index.mdx              # Homepage
└── README.md              # This file
```

## 🎨 Mintlify Features Used

- **Card & CardGroup**: Feature highlights and navigation
- **Tabs**: Code examples and comparisons
- **Steps**: Sequential tutorials
- **Accordion**: FAQs and collapsible content
- **Code blocks**: Syntax-highlighted examples
- **ParamField**: API parameter documentation

## 📝 Contributing

### Adding New Pages

1. Create `.mdx` file in appropriate directory
2. Add frontmatter with `title` and `description`
3. Add page reference to `docs.json` navigation
4. Use Mintlify components for rich formatting

### Style Guide

- Use clear, concise language
- Include code examples for all concepts
- Add cross-references to related pages
- Use appropriate Mintlify components
- Maintain consistent formatting

## 🔗 Links

- **Platform**: https://heylua.ai
- **GitHub**: https://github.com/lua-ai/lua-cli
- **npm**: https://www.npmjs.com/package/lua-cli
- **Support**: support@lua.ai

## 📄 License

This documentation is part of the Lua CLI project.
