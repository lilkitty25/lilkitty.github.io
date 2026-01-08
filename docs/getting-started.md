# Getting Started

Get your Case portfolio up and running in minutes.

## Prerequisites

- [Node.js](https://nodejs.org/) v18.17.1 or higher
- npm, yarn, or pnpm

## Installation

### Option 1: Create New Project (Recommended)

```bash
npm create astro@latest -- --template erlandv/case
```

### Option 2: Clone Repository

```bash
git clone https://github.com/erlandv/case.git my-portfolio
cd my-portfolio
npm install
```

## Configuration

1. Copy the environment example file:

```bash
cp .env.example .env
```

2. Edit `.env` with your information:

```bash
# Required
SITE_URL=https://your-domain.com
SITE_AUTHOR_NAME="Your Name"
SITE_AUTHOR_TITLE="Your Job Title"
SITE_AUTHOR_EMAIL=you@example.com

# Optional
SITE_AUTHOR_BIO="Your professional bio"
SOCIAL_GITHUB=https://github.com/username
SOCIAL_LINKEDIN=https://linkedin.com/in/username
```

See [Configuration Guide](./configuration.md) for all available options.

## Development

Start the development server:

```bash
npm run dev
```

Your site is now running at [http://localhost:4321](http://localhost:4321)

## Project Structure

```
├── public/              # Static assets (favicons, images)
├── src/
│   ├── components/      # Reusable Astro components
│   ├── content/         # MDX content files
│   │   ├── projects/    # Case studies
│   │   ├── decisions/   # Decision logs
│   │   ├── journey/     # Career timeline
│   │   ├── writing/     # Blog posts
│   │   ├── speaking/    # Talks & presentations
│   │   ├── uses/        # Tools & setup
│   │   └── testimonials/# Recommendations
│   ├── layouts/         # Page layouts
│   ├── pages/           # Route pages
│   ├── styles/          # Global CSS
│   └── config.ts        # Site configuration
├── .env                 # Environment variables
└── astro.config.mjs     # Astro configuration
```

## Available Commands

| Command | Description |
|---------|-------------|
| `npm run dev` | Start development server |
| `npm run build` | Build for production |
| `npm run preview` | Preview production build |
| `npm run astro check` | Check for TypeScript errors |

## Next Steps

- [Configure your site](./configuration.md)
- [Add your content](./content-guide.md)
- [Customize the theme](./customization.md)
- [Deploy your site](./deployment.md)
