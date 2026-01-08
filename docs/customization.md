# Customization

This theme uses modern CSS with custom properties (no Tailwind). All styles are easily customizable.

## Color System

Edit CSS custom properties in `src/styles/global.css`:

### Dark Mode (Default)

```css
:root {
  --color-bg: #0a0a0a;
  --color-bg-secondary: #111111;
  --color-bg-elevated: #1a1a1a;
  --color-text: #e5e5e5;
  --color-text-secondary: #a3a3a3;
  --color-text-muted: #737373;
  --color-border: #262626;
  --color-accent: #3b82f6;
  --color-accent-hover: #60a5fa;
}
```

### Light Mode

```css
[data-theme="light"] {
  --color-bg: #ffffff;
  --color-bg-secondary: #f5f5f5;
  --color-bg-elevated: #fafafa;
  --color-text: #171717;
  --color-text-secondary: #525252;
  --color-text-muted: #a3a3a3;
  --color-border: #e5e5e5;
  --color-accent: #2563eb;
  --color-accent-hover: #1d4ed8;
}
```

### Changing the Accent Color

To change the accent color throughout the site, update these variables:

```css
:root {
  --color-accent: #10b981;        /* Your accent color */
  --color-accent-hover: #34d399;  /* Hover state */
  --color-accent-muted: rgba(16, 185, 129, 0.15);
  --color-accent-glow: rgba(16, 185, 129, 0.25);
}

[data-theme="light"] {
  --color-accent: #059669;
  --color-accent-hover: #047857;
  --color-accent-muted: rgba(5, 150, 105, 0.1);
  --color-accent-glow: rgba(5, 150, 105, 0.15);
}
```

## Typography

Typography settings are in `src/styles/global.css`:

```css
:root {
  /* Font Sizes */
  --font-size-xs: 0.75rem;    /* 12px */
  --font-size-sm: 0.875rem;   /* 14px */
  --font-size-base: 1rem;     /* 16px */
  --font-size-lg: 1.125rem;   /* 18px */
  --font-size-xl: 1.25rem;    /* 20px */
  --font-size-2xl: 1.5rem;    /* 24px */
  --font-size-3xl: 1.875rem;  /* 30px */
  --font-size-4xl: 2.25rem;   /* 36px */
  
  /* Line Heights */
  --line-height-tight: 1.25;
  --line-height-normal: 1.5;
  --line-height-relaxed: 1.75;
}
```

### Custom Fonts

To use custom fonts, update the `body` font-family in `src/styles/global.css`:

```css
body {
  font-family: 'Inter', system-ui, -apple-system, sans-serif;
}
```

Don't forget to import your font in `src/layouts/BaseLayout.astro`:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

## Spacing

The spacing system uses consistent values:

```css
:root {
  --space-xs: 0.25rem;   /* 4px */
  --space-sm: 0.5rem;    /* 8px */
  --space-md: 1rem;      /* 16px */
  --space-lg: 1.5rem;    /* 24px */
  --space-xl: 2rem;      /* 32px */
  --space-2xl: 3rem;     /* 48px */
  --space-3xl: 4rem;     /* 64px */
}
```

## Layout

### Content Width

```css
:root {
  --max-width-prose: 65ch;      /* Reading content */
  --max-width-content: 1200px;  /* Page content */
}
```

### Border Radius

```css
:root {
  --border-radius-sm: 0.25rem;
  --border-radius-md: 0.5rem;
  --border-radius-lg: 1rem;
}
```

## Page Customization

### Home Page

Edit `src/pages/index.astro` to customize:

- Hero section text and CTAs
- Featured projects display
- Introduction content
- "Problems I Enjoy Solving" section

### Contact Page

Edit `src/pages/contact.astro` to customize:

- Contact page messaging
- Response time expectations

## Component Customization

### Navigation

Navigation is configured in `src/config.ts`. To change the navigation style, edit `src/components/Navigation.astro`.

### Footer

Edit `src/components/Footer.astro` to customize footer content and links.

### Cards

Card components are in `src/components/`:
- `ProjectCard.astro` — Case study cards
- `ArticleCard.astro` — Blog post cards
- `DecisionCard.astro` — Decision log cards
- `TalkCard.astro` — Speaking engagement cards

## Code Syntax Highlighting

The theme uses Shiki for syntax highlighting. Configure in `astro.config.mjs`:

```javascript
markdown: {
  shikiConfig: {
    theme: 'github-dark',  // Change theme here
    wrap: true
  }
}
```

Available themes: `github-dark`, `github-light`, `dracula`, `nord`, `one-dark-pro`, etc.

See [Shiki themes](https://shiki.style/themes) for all options.

## Adding New Pages

1. Create a new `.astro` file in `src/pages/`
2. Import and use `BaseLayout`:

```astro
---
import BaseLayout from '../layouts/BaseLayout.astro';
import SEO from '../components/SEO.astro';
---

<BaseLayout title="Page Title" description="Page description">
  <SEO title="Page Title" description="Page description" />
  
  <main class="page-content">
    <!-- Your content -->
  </main>
</BaseLayout>

<style>
  .page-content {
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem 1.5rem;
  }
</style>
```

## Removing Sections

To remove a section (e.g., Speaking):

1. Remove from navigation in `src/config.ts`
2. Delete the page file (e.g., `src/pages/speaking.astro`)
3. Delete the content folder (e.g., `src/content/speaking/`)
4. Remove the collection from `src/content.config.ts`
