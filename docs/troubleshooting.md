# Troubleshooting

Common issues and their solutions.

## Build Errors

### Schema Validation Error

**Problem:** Build fails with content validation error.

```
[ERROR] Invalid frontmatter in "src/content/projects/my-project.mdx"
```

**Solution:** Check the error message for which field is invalid. Common issues:

- Missing required field
- Wrong data type (e.g., string instead of number for `year`)
- Invalid enum value (e.g., `type: "talk"` instead of `type: "conference"`)

Run `npm run build` to see detailed validation errors.

### TypeScript Errors

**Problem:** TypeScript errors in `.astro` files.

**Solution:** Run the type checker:

```bash
npm run astro check
```

This shows detailed errors with file locations and suggested fixes.

### Module Not Found

**Problem:** `Cannot find module` error.

**Solution:**

1. Delete `node_modules` and reinstall:

```bash
rm -rf node_modules
npm install
```

2. Clear Astro cache:

```bash
rm -rf .astro
npm run dev
```

## Development Server

### Port Already in Use

**Problem:** Port 4321 is already in use.

**Solution:** Use a different port:

```bash
npm run dev -- --port 3000
```

Or kill the process using port 4321:

```bash
# Find the process
lsof -i :4321

# Kill it
kill -9 <PID>
```

### Hot Reload Not Working

**Problem:** Changes don't reflect in the browser.

**Solution:**

1. Hard refresh the browser (Ctrl+Shift+R / Cmd+Shift+R)
2. Restart the dev server
3. Clear browser cache
4. Check for syntax errors in your files

### Styles Not Updating

**Problem:** CSS changes don't appear.

**Solution:**

1. Check for CSS syntax errors
2. Clear browser cache
3. Restart dev server
4. Check if styles are scoped (Astro styles are scoped by default)

## Content Issues

### Images Not Loading

**Problem:** Images in `src/assets/` not displaying.

**Solution:**

1. Use the correct import syntax:

```astro
---
import myImage from '../assets/image.png';
---

<img src={myImage.src} alt="Description" />
```

2. Or use the `OptimizedImage` component:

```astro
---
import OptimizedImage from '../components/OptimizedImage.astro';
---

<OptimizedImage src="/path/to/image.png" alt="Description" />
```

### MDX Component Not Rendering

**Problem:** Custom component in MDX not working.

**Solution:** Import the component in your MDX file:

```mdx
---
title: "My Article"
---

import MyComponent from '../../components/MyComponent.astro';

# Article Title

<MyComponent />
```

### Draft Content Showing

**Problem:** Draft articles appear in production.

**Solution:** Ensure `draft: true` is set in frontmatter:

```yaml
---
title: "Work in Progress"
draft: true
---
```

Draft filtering only works in production builds (`npm run build`), not in development.

## Deployment Issues

### Environment Variables Not Working

**Problem:** Site shows default values instead of configured values.

**Solution:**

1. Verify environment variables are set in your hosting platform
2. Check variable names match exactly (case-sensitive)
3. Rebuild after adding/changing variables
4. For local testing, ensure `.env` file exists

### 404 on Page Refresh

**Problem:** Direct URL access returns 404.

**Solution:** Configure your hosting platform for SPA/static site routing:

**Netlify** - Create `public/_redirects`:
```
/* /index.html 200
```

**Vercel** - Create `vercel.json`:
```json
{
  "rewrites": [{ "source": "/(.*)", "destination": "/" }]
}
```

### Sitemap Not Generated

**Problem:** `/sitemap-index.xml` returns 404.

**Solution:**

1. Ensure `SITE_URL` is set correctly
2. Check `astro.config.mjs` has sitemap integration:

```javascript
import sitemap from '@astrojs/sitemap';

export default defineConfig({
  site: 'https://your-domain.com',
  integrations: [sitemap()],
});
```

3. Rebuild the site

## Performance Issues

### Slow Build Times

**Problem:** Build takes too long.

**Solution:**

1. Optimize images before adding to project
2. Reduce number of large images
3. Use `loading="lazy"` for below-fold images
4. Consider using external image hosting for large galleries

### Large Bundle Size

**Problem:** Site loads slowly.

**Solution:**

1. Check for unnecessary dependencies in `package.json`
2. Use dynamic imports for heavy components
3. Optimize images (the theme does this automatically)
4. Minimize custom JavaScript

## Theme Toggle Issues

### Flash of Wrong Theme

**Problem:** Brief flash of dark/light mode on page load.

**Solution:** This should be handled automatically. If it persists:

1. Check `BaseLayout.astro` has the inline theme script
2. Ensure `data-theme` attribute is on `<html>` element
3. Clear localStorage: `localStorage.removeItem('theme')`

### Theme Not Persisting

**Problem:** Theme resets on page navigation.

**Solution:**

1. Check localStorage is not blocked
2. Verify View Transitions are working
3. Check browser console for JavaScript errors

## Getting Help

If you can't find a solution:

1. Check [Astro Documentation](https://docs.astro.build)
2. Search [Astro Discord](https://astro.build/chat)
3. Open an issue on [GitHub](https://github.com/erlandv/case/issues)

When reporting issues, include:
- Node.js version (`node -v`)
- npm version (`npm -v`)
- Operating system
- Error messages (full stack trace)
- Steps to reproduce
