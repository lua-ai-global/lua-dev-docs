# Lua Documentation - Developer Guide

Official documentation for Lua CLI and LuaPop Chat Widget. Built with [Mintlify](https://mintlify.com/).

## 🚀 Quick Start for Developers

```bash
# Clone the repository
git clone <repository-url>
cd mintlify-docs
```

Install Mintlify CLI:

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

Start local development server:
```bash
mintlify dev
# or
mint dev
```

The documentation will be available at `http://localhost:3000`

## 📁 Project Structure

```
mintlify-docs/
├── docs.json                   # Main configuration file (navigation, theme, etc.)
├── index.mdx                   # Homepage
├── README.md                   # This file
│
├── getting-started/            # Getting started guides
│   ├── quick-start.mdx
│   ├── installation.mdx
│   └── first-skill.mdx
│
├── concepts/                   # Core concepts
│   ├── skills-and-tools.mdx
│   ├── platform-apis.mdx
│   ├── environment-variables.mdx
│   └── workflows.mdx
│
├── cli/                        # CLI command reference
│   ├── overview.mdx
│   ├── authentication.mdx
│   ├── skill-management.mdx
│   ├── development.mdx
│   └── troubleshooting.mdx
│
├── api/                        # API reference
│   ├── overview.mdx
│   ├── luaskill.mdx
│   ├── luatool.mdx
│   ├── user.mdx
│   ├── data.mdx
│   ├── products.mdx
│   ├── baskets.mdx
│   ├── orders.mdx
│   └── environment.mdx
│
├── template/                   # Template guide
│   ├── overview.mdx
│   ├── project-structure.mdx
│   ├── building-skills.mdx
│   ├── multi-skill-projects.mdx
│   └── best-practices.mdx
│
├── examples/                   # Tool examples
│   ├── overview.mdx
│   ├── weather.mdx
│   ├── user-data.mdx
│   ├── products.mdx
│   ├── baskets.mdx
│   ├── custom-data.mdx
│   └── payment.mdx
│
├── chat-widget/                # LuaPop chat widget docs
│   ├── introduction.mdx
│   ├── quick-start.mdx
│   ├── installation.mdx
│   ├── configuration.mdx
│   ├── styling.mdx
│   ├── events.mdx
│   ├── frameworks.mdx
│   ├── examples.mdx
│   ├── migration.mdx
│   ├── voice-chat.mdx
│   ├── analytics.mdx
│   └── troubleshooting.mdx
│
└── logo/                       # Brand assets
    ├── light.png
    └── dark.png
```

## 🎯 Navigation Structure

The documentation has 2 main tabs configured in `docs.json`:

### Tab 1: CLI (34 pages)
Building AI skills with TypeScript
- Getting Started (4 pages)
- Core Concepts (4 pages)
- CLI Commands (5 pages)
- API Reference (9 pages)
- Template & Examples (12 pages)

### Tab 2: Chat Widget (12 pages)
Embeddable chat widget
- Getting Started (3 pages)
- Configuration (3 pages)
- Integration (3 pages)
- Advanced (3 pages)

## 📝 Adding New Pages

### Step 1: Create MDX File

Create a new `.mdx` file in the appropriate directory:

```mdx
---
title: "Page Title"
description: "Brief description for SEO and previews"
---

## Your Content Here

Use Markdown and Mintlify components...
```

### Step 2: Add to Navigation

Update `docs.json` to include the new page:

```json
{
  "group": "Your Group",
  "pages": [
    "existing/page",
    "your-folder/new-page"  // Add this line
  ]
}
```

### Step 3: Preview Locally

```bash
mint dev
```

The new page will appear in the navigation automatically.

## 🎨 Mintlify Components

### Cards

```mdx
<Card title="Title" icon="rocket" href="/link">
  Description text
</Card>

<CardGroup cols={2}>
  <Card title="Card 1" icon="check">Content</Card>
  <Card title="Card 2" icon="code">Content</Card>
</CardGroup>
```

### Steps

```mdx
<Steps>
  <Step title="First Step">
    Instructions for step one
  </Step>
  <Step title="Second Step">
    Instructions for step two
  </Step>
</Steps>
```

### Tabs

```mdx
<Tabs>
  <Tab title="Option 1">
    Content for option 1
  </Tab>
  <Tab title="Option 2">
    Content for option 2
  </Tab>
</Tabs>
```

### Accordions

```mdx
<AccordionGroup>
  <Accordion title="Question 1">
    Answer to question 1
  </Accordion>
  <Accordion title="Question 2">
    Answer to question 2
  </Accordion>
</AccordionGroup>
```

### Code Blocks

````mdx
```typescript
// Code example with syntax highlighting
const example = "hello world";
```

```bash
# Terminal commands
npm install package
```
````

### Code Groups

````mdx
<CodeGroup>

```typescript TypeScript
const example: string = "typed";
```

```javascript JavaScript
const example = "untyped";
```

</CodeGroup>
````

### Callouts

```mdx
<Note>
  Informational note
</Note>

<Warning>
  Important warning
</Warning>

<Check>
  Success message
</Check>
```

### API Parameters

````mdx
```mdx
<ParamField path="paramName" type="string" required>
  Description of the parameter
  
  **Example:**
  ```javascript
  paramName: "value"
  ```
</ParamField>
```
````

## 🎨 Style Guide

### Frontmatter

Every page must have frontmatter:

```mdx
---
title: "Page Title"
description: "Brief description (50-160 characters)"
---
```

### Headings

Use semantic heading hierarchy:

```mdx
## Main Section (H2)

### Subsection (H3)

#### Detail (H4)
```

### Code Examples

- Use appropriate language tags: `typescript`, `javascript`, `bash`, `html`, `css`, `json`, `yaml`
- Include comments to explain complex code
- Show complete, runnable examples
- Use syntax highlighting

### Links

Internal links:
```mdx
[Link text](/path/to/page)
```

External links:
```mdx
[Link text](https://example.com)
```

Card links:
```mdx
<Card title="Title" href="/path/to/page" />
```

### Writing Style

- **Clear and concise** - Get to the point quickly
- **Action-oriented** - Use verbs (Create, Configure, Deploy)
- **Include examples** - Show, don't just tell
- **Progressive disclosure** - Start simple, add complexity
- **Consistent tone** - Professional but friendly

## 🔧 Configuration Files

### docs.json

Main configuration file controlling:

```json
{
  "name": "Lua CLI",           // Site name
  "colors": {
    "primary": "#8B5CF6",      // Brand colors
    "light": "#A78BFA",
    "dark": "#7C3AED"
  },
  "navigation": {              // Tab and page structure
    "tabs": [...]
  },
  "logo": {                    // Logo files
    "light": "/logo/light.png",
    "dark": "/logo/dark.png"
  }
}
```

**Key sections:**
- `colors` - Brand color scheme
- `navigation` - Tab and page structure
- `logo` - Brand logos (light/dark modes)
- `navbar` - Top navigation links
- `footer` - Social links

### Common Changes

**Update brand colors:**
```json
"colors": {
  "primary": "#8B5CF6",
  "light": "#A78BFA",
  "dark": "#7C3AED"
}
```

**Add new page to navigation:**
```json
"pages": [
  "existing/page",
  "new/page"  // Add here
]
```

**Update logo:**
```json
"logo": {
  "light": "/logo/light.png",
  "dark": "/logo/dark.png"
}
```

## 🚀 Development Workflow

### Local Development

```bash
# Start dev server
mint dev

# Make changes to .mdx files
# Save - browser auto-refreshes

# Check for broken links
mint broken-links
```

### Adding a New Section

1. **Create directory**: `mkdir new-section`
2. **Create pages**: `touch new-section/page1.mdx`
3. **Add frontmatter** to each page
4. **Update docs.json** with navigation
5. **Test locally**: `mint dev`
6. **Commit changes**

### Updating Existing Content

1. **Find the page**: Navigate to `.mdx` file
2. **Edit content**: Maintain Mintlify component syntax
3. **Preview**: Check in local dev server
4. **Test links**: Ensure all links work
5. **Commit**: Push changes

## 📚 Content Guidelines

### Page Structure

Every page should have:

```mdx
---
title: "Clear, Descriptive Title"
description: "SEO-friendly description"
---

## Overview
Brief introduction to the topic

## Main Content
Organized into logical sections

## Examples
Practical, runnable code examples

## Next Steps
<CardGroup cols={2}>
  <Card title="Related Topic 1" href="/link" />
  <Card title="Related Topic 2" href="/link" />
</CardGroup>
```

### Code Examples

**Good example:**
```mdx
```typescript
import { LuaSkill } from 'lua-cli';

// Create a skill
const skill = new LuaSkill({
  name: "my-skill",
  description: "What it does",
  tools: [new MyTool()]
});
```
```

**Include:**
- Complete, runnable code
- Relevant imports
- Clear variable names
- Helpful comments
- Expected output

### Consistency

Maintain consistency across pages:
- ✅ Same component usage patterns
- ✅ Similar section structures
- ✅ Consistent terminology
- ✅ Matching code style
- ✅ Similar example complexity

## 🔗 Cross-Referencing

Link related pages for better navigation:

```mdx
## Next Steps

<CardGroup cols={2}>
  <Card
    title="Related Topic"
    icon="book"
    href="/related/page"
  >
    Short description of related content
  </Card>
</CardGroup>
```

Internal link paths are relative to root:
- `/getting-started/quick-start` ✅
- `../getting-started/quick-start` ❌

## 🎨 Brand Assets

### Logos

Located in `/logo/`:
- `light.png` - Used in light mode
- `dark.png` - Used in dark mode

**Requirements:**
- PNG format
- Transparent background recommended
- Reasonable size (< 100KB)

### Favicon

Located at root: `/favicon.png`

**Requirements:**
- PNG format
- Square dimensions (512x512 recommended)
- Clear at small sizes

### Colors

Defined in `docs.json`:

```json
"colors": {
  "primary": "#8B5CF6",   // Main brand color
  "light": "#A78BFA",     // Lighter variant
  "dark": "#7C3AED"       // Darker variant
}
```

Used throughout the docs for:
- Links and buttons
- Code highlights
- Interactive elements
- Hover states

## 🧪 Testing

### Before Committing

1. **Test locally**: `mint dev`
2. **Check all pages** load correctly
3. **Test navigation** flows logically
4. **Verify code examples** are correct
5. **Check broken links**: `mint broken-links`
6. **Test mobile view** (responsive design)

### Manual Checks

- [ ] All code examples have proper syntax highlighting
- [ ] All internal links work
- [ ] All images load correctly
- [ ] Mobile navigation works
- [ ] Search functionality works
- [ ] No console errors

## 📦 Deployment

### Automatic Deployment

This repository is connected to Mintlify and automatically deploys on:
- Push to `main` branch
- Pull request merge

### Manual Deployment

If needed to deploy manually:

```bash
# Build the documentation
mint build

# Deploy to Mintlify
# (Typically handled by CI/CD)
```

## 🔍 Search & SEO

### Page Metadata

Each page's frontmatter affects SEO:

```mdx
---
title: "Clear, Keyword-Rich Title"
description: "Compelling description with keywords (50-160 chars)"
---
```

### Search Optimization

Mintlify's built-in search indexes:
- Page titles
- Descriptions
- Headings
- Content text
- Code comments

**Tips for better search:**
- Use clear, descriptive titles
- Include common search terms in content
- Add alternative phrasings
- Use semantic headings

## 🤝 Contributing

### Adding New Content

1. **Identify the section** where content belongs
2. **Create the MDX file** in appropriate directory
3. **Add to navigation** in `docs.json`
4. **Follow style guide** for consistency
5. **Test locally** with `mint dev`
6. **Create pull request** with clear description

### Updating Existing Content

1. **Find the file** to update
2. **Make changes** preserving Mintlify syntax
3. **Test locally** to verify
4. **Commit with descriptive message**
5. **Create pull request**

### Pull Request Guidelines

**Title format:**
- `feat: Add new section for X`
- `fix: Correct typo in Y`
- `docs: Update example in Z`
- `style: Improve formatting in W`

**Description should include:**
- What changed and why
- Which pages were affected
- Screenshots if visual changes
- Testing performed

## 🎯 Content Organization

### CLI Section (Tab 1)

**Getting Started** - Onboarding new users
- Quick start guide
- Installation instructions
- First skill tutorial

**Core Concepts** - Fundamental knowledge
- Architecture explanations
- API overviews
- Configuration guides

**CLI Commands** - Command reference
- All CLI commands
- Usage examples
- Troubleshooting

**API Reference** - Technical reference
- Class and interface docs
- Method signatures
- Type definitions

**Template & Examples** - Learning resources
- Template project guide
- Working code examples
- Best practices

### Chat Widget Section (Tab 2)

**Getting Started** - Quick setup
- Introduction
- Quick start
- Installation guides

**Configuration** - Customization
- All config options
- Styling guides
- Event system

**Integration** - Platform guides
- Framework integration
- Real-world examples
- Migration guides

**Advanced** - Advanced features
- Voice chat
- Analytics
- Troubleshooting

## 💡 Best Practices

### Component Usage

**Cards for navigation:**
```mdx
<CardGroup cols={2}>
  <Card title="Next Topic" icon="arrow-right" href="/path">
    Brief description
  </Card>
</CardGroup>
```

**Steps for tutorials:**
```mdx
<Steps>
  <Step title="Do this first">
    Detailed instructions
  </Step>
</Steps>
```

**Tabs for alternatives:**
```mdx
<Tabs>
  <Tab title="Option A">
    Code for option A
  </Tab>
  <Tab title="Option B">
    Code for option B
  </Tab>
</Tabs>
```

**Accordions for FAQs:**
```mdx
<AccordionGroup>
  <Accordion title="Question?">
    Answer with details
  </Accordion>
</AccordionGroup>
```

### Code Examples

**Include complete examples:**
- All necessary imports
- Full context (not just snippets)
- Expected output
- Error handling

**Use appropriate language tags:**
- `typescript` - TypeScript code
- `javascript` - JavaScript code
- `tsx` - React/TypeScript JSX
- `bash` - Shell commands
- `html` - HTML markup
- `css` - Stylesheets
- `json` - JSON data
- `yaml` - YAML configs

### Writing Tips

**Do:**
- ✅ Write clear, concise explanations
- ✅ Use active voice
- ✅ Include practical examples
- ✅ Add "Next Steps" sections
- ✅ Cross-reference related pages
- ✅ Use consistent terminology

**Don't:**
- ❌ Use jargon without explanation
- ❌ Write overly long paragraphs
- ❌ Include outdated information
- ❌ Forget code syntax highlighting
- ❌ Skip error handling in examples

## 🔧 Troubleshooting Development Issues

### Mintlify CLI Issues

**Command not found:**
```bash
npm install -g mintlify
```

**Port 3000 in use:**
```bash
lsof -ti:3000 | xargs kill -9
mint dev
```

**Changes not reflecting:**
- Hard refresh browser (Cmd+Shift+R / Ctrl+Shift+F5)
- Restart dev server
- Clear browser cache

### Build Errors

**Invalid docs.json:**
- Validate JSON syntax
- Check all referenced pages exist
- Verify all URLs are valid

**Broken links:**
```bash
mint broken-links
```

Fix any broken internal links.

**Missing images:**
- Ensure images exist in repository
- Use correct paths (relative to root)
- Check file extensions match

## 📊 Analytics & Monitoring

### Track Documentation Usage

Mintlify provides built-in analytics for:
- Page views
- Popular searches
- User engagement
- Geographic distribution

Access analytics in Mintlify dashboard.

### Custom Analytics

Add custom tracking if needed:

```html
<!-- In a custom component or page -->
<script>
  gtag('event', 'page_view', {
    page_title: 'Documentation Page',
    page_location: window.location.href
  });
</script>
```

## 🔐 Security

### Sensitive Information

**Never commit:**
- API keys or tokens
- Private agent IDs
- User data or emails
- Internal URLs or endpoints

**Safe to commit:**
- Example/placeholder IDs
- Public documentation
- Open source code examples
- Generic configurations

### Environment Variables

For examples requiring sensitive data:

```mdx
```javascript
// Use placeholders
const apiKey = "your-api-key-here";  // User replaces this
const agentId = "your-agent-id";     // User gets from dashboard
```
```

## 📖 Documentation Standards

### File Naming

- Use **kebab-case**: `my-new-page.mdx`
- Be descriptive: `voice-chat.mdx` not `vc.mdx`
- Match content: filename reflects page content

### Directory Organization

- Group related pages in folders
- Keep folder names lowercase
- Use singular for concepts: `api/` not `apis/`
- Use plural for examples: `examples/` not `example/`

### Version Control

**Commit messages:**
```bash
# Good
git commit -m "feat: add voice chat documentation"
git commit -m "fix: correct API endpoint in example"
git commit -m "docs: improve quick start guide"

# Bad
git commit -m "updates"
git commit -m "fixed stuff"
```

**Branch naming:**
```bash
# Feature branches
git checkout -b feat/add-webhook-docs

# Fix branches
git checkout -b fix/broken-link-in-api

# Documentation updates
git checkout -b docs/update-migration-guide
```

## 🚀 Deployment Checklist

Before deploying major changes:

- [ ] All new pages added to `docs.json`
- [ ] All code examples tested
- [ ] All links verified
- [ ] Images optimized and loading
- [ ] Mobile view tested
- [ ] Search works correctly
- [ ] No console errors
- [ ] Spell check completed
- [ ] Peer review done

## 🆘 Getting Help

### Internal Resources

- **Mintlify Docs**: https://mintlify.com/docs
- **Component Reference**: https://mintlify.com/docs/components
- **Style Guide**: This README

### External Support

- **Mintlify Community**: https://mintlify.com/community
- **GitHub Issues**: For bug reports
- **Team Chat**: Internal Slack/Discord

## 📋 Quick Reference

### Common Commands

```bash
# Development
mint dev                 # Start local server
mint broken-links        # Check for broken links
mint --version          # Check Mintlify version

# Build
mint build              # Build for production
```

### Common Tasks

**Add a new page:**
1. Create `section/new-page.mdx`
2. Add to `docs.json` navigation
3. Test with `mint dev`

**Update navigation:**
1. Edit `docs.json`
2. Update `navigation.tabs` array
3. Test locally

**Change colors:**
1. Edit `docs.json`
2. Update `colors` object
3. Refresh to see changes

**Update logo:**
1. Replace files in `/logo/`
2. Update paths in `docs.json` if needed
3. Hard refresh browser

## 📞 Maintainers

For questions about this documentation:

- **Technical Issues**: Create GitHub issue
- **Content Questions**: Contact documentation team
- **Urgent Changes**: Contact repository maintainers

## 🎓 Learning Resources

### Mintlify Documentation

- **Getting Started**: https://mintlify.com/docs/quickstart
- **Components**: https://mintlify.com/docs/components
- **Configuration**: https://mintlify.com/docs/settings
- **Deployment**: https://mintlify.com/docs/deployment

### MDX Resources

- **MDX Docs**: https://mdxjs.com/
- **Markdown Guide**: https://www.markdownguide.org/

## 📄 License

This documentation is part of the Lua project. See LICENSE for details.

---

## 🎉 Quick Start Recap

```bash
# 1. Clone repository
git clone <repository-url>
cd mintlify-docs

# 2. Install Mintlify
npm install -g mintlify

# 3. Start development
mint dev

# 4. Make changes
# Edit .mdx files in your editor

# 5. Commit & push
git add .
git commit -m "docs: your changes"
git push
```

**Happy documenting! 📚✨**
