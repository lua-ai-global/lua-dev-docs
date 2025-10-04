# Contributing to Lua Documentation

Thank you for contributing to Lua's documentation! This guide will help you get started.

## 🚀 Quick Start

```bash
# 1. Fork and clone
git clone <your-fork-url>
cd mintlify-docs

# 2. Install Mintlify CLI
npm install -g mintlify

# 3. Create a branch
git checkout -b docs/your-feature-name

# 4. Start development server
mint dev

# 5. Make your changes
# Edit .mdx files

# 6. Test locally
# Verify changes at http://localhost:3000

# 7. Commit and push
git add .
git commit -m "docs: describe your changes"
git push origin docs/your-feature-name

# 8. Create pull request
```

## 📝 What to Contribute

### Content Improvements

- **Fix typos or errors** - Spotted a mistake? Fix it!
- **Clarify explanations** - Make complex topics easier to understand
- **Add examples** - Real-world code examples are always valuable
- **Update outdated info** - Keep docs current with latest features
- **Improve code samples** - Better, clearer examples

### New Content

- **New guides** - Tutorial for a specific use case
- **FAQ entries** - Common questions and answers
- **Troubleshooting** - Solutions to common problems
- **Examples** - Industry-specific implementations
- **Best practices** - Professional patterns and tips

### Technical Improvements

- **Fix broken links** - Internal and external
- **Optimize images** - Compress and format properly
- **Improve navigation** - Better organization
- **Enhance search** - Better keywords and structure
- **Accessibility** - Improve for screen readers

## 📋 Contribution Guidelines

### Content Standards

**Writing Style:**
- Clear and concise
- Active voice
- Present tense
- Professional but friendly tone
- Include practical examples

**Code Examples:**
- Complete and runnable
- Include necessary imports
- Add helpful comments
- Show expected output
- Handle errors properly

**Formatting:**
- Use Mintlify components appropriately
- Follow existing page structure
- Maintain consistent style
- Use proper markdown syntax

### File Naming

- **Use kebab-case**: `new-feature.mdx` ✅
- **Be descriptive**: `voice-chat.mdx` not `vc.mdx` ✅
- **Avoid abbreviations**: spell out names ✅
- **No spaces**: use hyphens ✅

### Commit Messages

Follow conventional commits:

```bash
# Format
<type>: <description>

# Types
feat: new content or feature
fix: correct errors or bugs
docs: documentation meta changes
style: formatting, no content change
refactor: reorganize without changing content
```

**Examples:**
```bash
git commit -m "feat: add webhook integration guide"
git commit -m "fix: correct API endpoint in example"
git commit -m "docs: improve quick start clarity"
git commit -m "style: format code examples consistently"
```

### Pull Request Process

1. **Create descriptive PR title**
   ```
   docs: Add comprehensive webhook guide
   ```

2. **Provide detailed description**
   - What changed and why
   - Which pages were affected
   - Screenshots for visual changes
   - Testing performed

3. **Link related issues**
   ```
   Closes #123
   Relates to #456
   ```

4. **Request review** from maintainers

5. **Address feedback** promptly

6. **Squash commits** if requested

## 🎨 Style Guide

### Page Structure

```mdx
---
title: "Page Title"
description: "Brief description"
---

## Overview
Introduction paragraph

## Main Sections
Content organized logically

## Examples
Practical code examples

## Troubleshooting
Common issues (if applicable)

## Next Steps
<CardGroup cols={2}>
  <Card title="Related" href="/link" />
</CardGroup>
```

### Components

**Use Cards for navigation:**
```mdx
<Card title="Topic" icon="icon-name" href="/path">
  Description
</Card>
```

**Use Steps for procedures:**
```mdx
<Steps>
  <Step title="First">Content</Step>
  <Step title="Second">Content</Step>
</Steps>
```

**Use Tabs for alternatives:**
```mdx
<Tabs>
  <Tab title="Option A">Code A</Tab>
  <Tab title="Option B">Code B</Tab>
</Tabs>
```

**Use Accordions for FAQs:**
```mdx
<AccordionGroup>
  <Accordion title="Question">Answer</Accordion>
</AccordionGroup>
```

### Code Blocks

Always specify the language:

````mdx
```typescript
const example: string = "hello";
```

```bash
npm install package
```

```html
<div>HTML example</div>
```
````

### Icons

Use Font Awesome icon names:
- `rocket` - Getting started, deployment
- `code` - Code examples, development
- `book` - Documentation, guides
- `cog` - Configuration
- `palette` - Styling, customization
- `chart-line` - Analytics
- `shield` - Security

See full list: https://fontawesome.com/icons

## ✅ Pre-Commit Checklist

Before submitting a PR:

- [ ] Tested locally with `mint dev`
- [ ] All pages load without errors
- [ ] Code examples are correct and tested
- [ ] Links work (internal and external)
- [ ] Images load properly
- [ ] Follows style guide
- [ ] No spelling errors
- [ ] Mobile view works
- [ ] Commit messages follow convention
- [ ] PR description is clear

## 🐛 Reporting Issues

### Documentation Bugs

If you find an issue but can't fix it:

1. **Search existing issues** first
2. **Create detailed issue** with:
   - Page URL or file path
   - What's wrong
   - What it should be
   - Screenshots if applicable
   - Browser/device if relevant

### Feature Requests

For new documentation content:

1. **Describe the content** needed
2. **Explain why** it's valuable
3. **Suggest where** it should go
4. **Provide examples** if possible

## 🎓 Learning Mintlify

### Essential Docs

- **Quickstart**: https://mintlify.com/docs/quickstart
- **Components**: https://mintlify.com/docs/components
- **Navigation**: https://mintlify.com/docs/navigation
- **Styling**: https://mintlify.com/docs/settings/global

### Example Repos

Study other Mintlify documentation:
- Mintlify's own docs: https://github.com/mintlify/docs
- Popular open source projects using Mintlify

## 💬 Communication

### Discussions

- **GitHub Discussions**: For questions and ideas
- **Pull Request Comments**: For code review
- **Issues**: For bugs and feature requests

### Response Time

- **Critical bugs**: Within 24 hours
- **Pull requests**: Within 3-5 business days
- **Feature requests**: Reviewed weekly

## 🙏 Thank You!

Your contributions help make Lua's documentation better for everyone. We appreciate your time and effort!

### Recognition

Contributors are recognized in:
- GitHub contributors page
- Release notes (for significant contributions)
- Documentation credits page (coming soon)

---

**Questions?** Open an issue or reach out to the maintainers. Happy contributing! 🎉

