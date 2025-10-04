# Images Directory

## Hero Images

Add your hero images here:
- `hero-light.png` - For light theme (1200x600px)
- `hero-dark.png` - For dark theme (1200x600px)

See `HERO_IMAGE_SPECS.md` for complete design specifications.

## Other Images

Place other documentation images here:
- Screenshots
- Diagrams
- Icons
- Illustrations

## Image Guidelines

### File Naming
- Use lowercase with hyphens: `my-image.png`
- Be descriptive: `cli-workflow-diagram.png`
- Include dimensions if helpful: `screenshot-1200x800.png`

### Optimization
- Compress images before committing
- Use appropriate formats:
  - PNG for screenshots, diagrams, logos
  - JPG for photos
  - SVG for icons and simple graphics
  - WebP for modern browsers (with PNG fallback)

### File Sizes
- Screenshots: < 200KB
- Hero images: < 500KB
- Icons: < 50KB
- Logos: < 100KB

### Tools
- **TinyPNG**: https://tinypng.com
- **ImageOptim**: macOS app
- **Squoosh**: https://squoosh.app

## Usage in MDX

```mdx
<!-- Simple image -->
![Alt text](/images/my-image.png)

<!-- Light/dark theme images -->
<img
  className="block dark:hidden"
  src="/images/hero-light.png"
  alt="Hero Light"
/>
<img
  className="hidden dark:block"
  src="/images/hero-dark.png"
  alt="Hero Dark"
/>

<!-- With caption -->
<Frame>
  <img src="/images/diagram.png" alt="Architecture" />
</Frame>
```

## Accessibility

Always include descriptive alt text:
```mdx
![A flowchart showing the order of operations from user input to API response](/images/flow.png)
```

