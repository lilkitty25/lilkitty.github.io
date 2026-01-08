# Deployment

This theme generates a static site that can be deployed to any static hosting service.

## Build

Generate the production build:

```bash
npm run build
```

This creates a `dist/` folder with all static files.

Preview the build locally:

```bash
npm run preview
```

## Deployment Platforms

### Netlify

1. Push your repository to GitHub/GitLab/Bitbucket
2. Connect your repository to [Netlify](https://netlify.com)
3. Configure build settings:
   - Build command: `npm run build`
   - Publish directory: `dist`
4. Add environment variables in Netlify dashboard

**netlify.toml** (optional):

```toml
[build]
  command = "npm run build"
  publish = "dist"

[build.environment]
  NODE_VERSION = "20"
```

### Vercel

1. Push your repository to GitHub/GitLab/Bitbucket
2. Import your repository to [Vercel](https://vercel.com)
3. Configure build settings:
   - Framework Preset: Astro
   - Build command: `npm run build`
   - Output directory: `dist`
4. Add environment variables in Vercel dashboard

### Cloudflare Pages

1. Push your repository to GitHub/GitLab
2. Connect to [Cloudflare Pages](https://pages.cloudflare.com)
3. Configure build settings:
   - Build command: `npm run build`
   - Build output directory: `dist`
4. Add environment variables in Cloudflare dashboard

### GitHub Pages

1. Install the GitHub Pages adapter:

```bash
npm install @astrojs/github-pages
```

2. Update `astro.config.mjs`:

```javascript
import { defineConfig } from 'astro/config';

export default defineConfig({
  site: 'https://username.github.io',
  base: '/repository-name',  // Remove if using custom domain
});
```

3. Create `.github/workflows/deploy.yml`:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [main]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
          cache: npm
      - run: npm ci
      - run: npm run build
        env:
          SITE_URL: ${{ vars.SITE_URL }}
          SITE_AUTHOR_NAME: ${{ vars.SITE_AUTHOR_NAME }}
          # Add other env vars as needed
      - uses: actions/upload-pages-artifact@v3
        with:
          path: dist

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - uses: actions/deploy-pages@v4
        id: deployment
```

4. Enable GitHub Pages in repository settings (Settings → Pages → Source: GitHub Actions)

### AWS S3 + CloudFront

1. Build your site: `npm run build`
2. Create an S3 bucket with static website hosting enabled
3. Upload the `dist/` folder contents to S3
4. Create a CloudFront distribution pointing to the S3 bucket
5. Configure custom domain (optional)

### Docker

Create a `Dockerfile`:

```dockerfile
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

Build and run:

```bash
docker build -t my-portfolio .
docker run -p 8080:80 my-portfolio
```

## Environment Variables

Most platforms support environment variables through their dashboard. Set these before building:

**Required:**
- `SITE_URL`
- `SITE_AUTHOR_NAME`
- `SITE_AUTHOR_TITLE`
- `SITE_AUTHOR_EMAIL`

**Optional:**
- `SITE_LANGUAGE`
- `SITE_AUTHOR_BIO`
- `SITE_AUTHOR_LOCATION`
- `SOCIAL_GITHUB`
- `SOCIAL_LINKEDIN`
- `SOCIAL_TWITTER`
- `ANALYTICS_*`

## Custom Domain

1. Add your domain in your hosting platform's dashboard
2. Update DNS records:
   - For apex domain: A record pointing to platform's IP
   - For subdomain: CNAME record pointing to platform's domain
3. Update `SITE_URL` environment variable
4. Enable HTTPS (usually automatic)

## Performance Checklist

Before deploying:

- [ ] Run `npm run build` successfully
- [ ] Test with `npm run preview`
- [ ] Verify all environment variables are set
- [ ] Check images are optimized
- [ ] Test on mobile devices
- [ ] Verify meta tags and OG images
- [ ] Test all navigation links
