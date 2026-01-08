# Configuration

All site configuration is managed through environment variables, making it easy to customize without touching the code.

## Environment Variables

Copy `.env.example` to `.env` and configure the following:

### Site Settings

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `SITE_URL` | Yes | `https://example.com` | Your production URL (used for sitemap, OG tags) |
| `SITE_LANGUAGE` | No | `en` | ISO 639-1 language code (e.g., `en`, `id`, `de`, `fr`) |
| `SITE_TITLE` | No | `Professional Portfolio` | Site title for SEO |
| `SITE_DESCRIPTION` | No | - | Default meta description |

### Author Information

| Variable | Required | Default | Description |
|----------|----------|---------|-------------|
| `SITE_AUTHOR_NAME` | Yes | `Your Name` | Your full name |
| `SITE_AUTHOR_TITLE` | Yes | `Senior Software Engineer` | Your job title |
| `SITE_AUTHOR_BIO` | No | - | Short professional bio |
| `SITE_AUTHOR_EMAIL` | Yes | `hello@example.com` | Contact email |
| `SITE_AUTHOR_LOCATION` | No | - | Your location (leave empty to hide) |

### Social Links

Leave empty to hide a platform from your site.

| Variable | Description |
|----------|-------------|
| `SOCIAL_GITHUB` | GitHub profile URL |
| `SOCIAL_LINKEDIN` | LinkedIn profile URL |
| `SOCIAL_TWITTER` | Twitter/X profile URL |
| `SOCIAL_MASTODON` | Mastodon profile URL |
| `SOCIAL_BLUESKY` | Bluesky profile URL |

### Analytics

Configure one or more analytics services. Leave empty to disable.

| Variable | Description |
|----------|-------------|
| `ANALYTICS_PLAUSIBLE_DOMAIN` | Your Plausible domain |
| `ANALYTICS_FATHOM_SITE_ID` | Fathom site ID |
| `ANALYTICS_GA_ID` | Google Analytics measurement ID |

## Example Configuration

```bash
# .env
SITE_URL=https://johndoe.dev
SITE_LANGUAGE=en

SITE_AUTHOR_NAME="John Doe"
SITE_AUTHOR_TITLE="Staff Software Engineer"
SITE_AUTHOR_BIO="Building distributed systems at scale. I write about architecture decisions and engineering leadership."
SITE_AUTHOR_EMAIL=hello@johndoe.dev
SITE_AUTHOR_LOCATION="San Francisco, CA"

SOCIAL_GITHUB=https://github.com/johndoe
SOCIAL_LINKEDIN=https://linkedin.com/in/johndoe
SOCIAL_TWITTER=https://twitter.com/johndoe

ANALYTICS_PLAUSIBLE_DOMAIN=johndoe.dev
```

## Navigation

Navigation links are configured in `src/config.ts`. Edit the `nav` array to customize:

```typescript
nav: [
  { label: 'Projects', href: '/projects' },
  { label: 'Decisions', href: '/decisions' },
  { label: 'Journey', href: '/journey' },
  { label: 'Writing', href: '/writing' },
  { label: 'Speaking', href: '/speaking' },
  { label: 'Uses', href: '/uses' },
  { label: 'Contact', href: '/contact' },
],
```

To remove a section, simply delete its entry from the array.

## Favicon Setup

Replace the following files in `public/` with your own:

| File | Size | Purpose |
|------|------|---------|
| `favicon.svg` | - | Main favicon (modern browsers) |
| `favicon-32x32.png` | 32×32 | PNG fallback |
| `favicon-16x16.png` | 16×16 | PNG fallback |
| `favicon-192x192.png` | 192×192 | Android Chrome |
| `favicon-512x512.png` | 512×512 | PWA icon |
| `apple-touch-icon.png` | 180×180 | iOS icon |
| `og-image.png` | 1200×630 | Social sharing image |

Update `public/site.webmanifest` with your site name and theme colors.

**Tip**: Use [RealFaviconGenerator](https://realfavicongenerator.net/) to generate all sizes from a single image.
