# Hero Image Specifications

## Required Images

Place these images in this directory:

1. `hero-light.png` - Hero image for light theme
2. `hero-dark.png` - Hero image for dark theme

## Specifications

### Dimensions
- **Width**: 1200px
- **Height**: 600px  
- **Aspect Ratio**: 2:1
- **Format**: PNG with transparency support

### Design Guidelines

#### Content to Include
1. **Visual representation** of AI agent + API integration
2. **Code snippet** showing TypeScript tool example
3. **Conversation flow** showing user chat → AI action
4. **Connection lines** showing API integrations

#### Suggested Layout

```
┌─────────────────────────────────────────────────────┐
│                                                     │
│  [Lua Logo]         AI Agents + Your APIs          │
│                                                     │
│  ┌──────────┐      ┌──────────┐      ┌──────────┐ │
│  │   USER   │ ───▶ │    AI    │ ───▶ │YOUR APIs │ │
│  │   CHAT   │      │  AGENT   │      │  Stripe  │ │
│  └──────────┘      └──────────┘      │ Shopify  │ │
│                                       │  Custom  │ │
│  "Where's my order?"                  └──────────┘ │
│       ↓                                             │
│  [Code snippet showing TypeScript tool]            │
│                                                     │
│  class OrderLookup implements LuaTool {            │
│    async execute(input) {                          │
│      return fetch('your-api.com/orders')           │
│    }                                                │
│  }                                                  │
│                                                     │
└─────────────────────────────────────────────────────┘
```

#### Color Scheme

**Light Theme (hero-light.png):**
- Background: White or light gradient
- Primary color: #8B5CF6 (Purple)
- Accent: #A78BFA
- Text: Dark gray (#2C3E50)
- Code background: Light gray (#F8F9FA)

**Dark Theme (hero-dark.png):**
- Background: Dark gradient (#1A1A2E to #16213E)
- Primary color: #A78BFA (Lighter purple)
- Accent: #8B5CF6
- Text: White (#FFFFFF)
- Code background: Darker gray (#0F1419)

### Elements to Include

1. **Lua branding** - Logo in corner
2. **Tagline** - "Build AI Agents That Do Anything"
3. **Visual flow** - User → AI → APIs diagram
4. **Code snippet** - TypeScript tool example
5. **API logos** - Stripe, Shopify, custom backend icons
6. **Modern aesthetic** - Clean, developer-focused

### Style References

Look at hero images from:
- Vercel - Developer-focused, clean, code-centric
- Stripe - Professional, technical, clear
- Supabase - Modern, visual flow diagrams
- Linear - Minimalist, high-quality visuals

### Technical Requirements

- **File size**: < 500KB (optimize for web)
- **Format**: PNG (supports transparency)
- **Retina-ready**: 2x resolution (2400x1200) then scale down
- **Compression**: Use TinyPNG or similar
- **Alt text ready**: Descriptive for accessibility

## Temporary Placeholder

Until designed, the page will use the images if they exist, or gracefully show without them.

## Design Tools

Recommended tools:
- **Figma** - Primary design tool
- **Canva** - Quick mockups
- **Adobe Illustrator** - Vector graphics
- **Sketch** - Alternative to Figma

## Delivery

Once designed:
1. Export both light and dark versions
2. Name exactly: `hero-light.png` and `hero-dark.png`
3. Place in `/images/` directory
4. Optimize file size
5. Commit to repository

The hero images will automatically appear on the overview page.

