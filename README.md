# Case — A Case-Study-First Portfolio Theme for Astro

[![Built with Astro](https://astro.badg.es/v2/built-with-astro/tiny.svg)](https://astro.build)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

A case-study-first portfolio theme for Astro. Designed for professionals who want to showcase their thinking, decisions, and real impact—not just screenshots and tech stacks.

## Why Case?

Most portfolio themes focus on listing projects with screenshots and bullet points. Case takes a different approach: it treats every project as a case study with a structured narrative—problem, constraints, approach, key decisions, and measurable outcomes.

This lets you demonstrate not just what you built, but how you think. Hiring managers and clients see your decision-making process, trade-offs you considered, and the real impact of your work. You stand out by showing depth, not just breadth.

## Demo

<div align="center">

[![View Demo](https://img.shields.io/badge/View_Demo-→-0077FF?style=for-the-badge&logo=astro&logoColor=white)](https://case.erland.me)

<table>
  <tr>
    <td width="50%">
      <img src="./screenshots/light-mode.webp" loading="lazy" alt="Light Mode">
      <p align="center"><em>Light Mode</em></p>
    </td>
    <td width="50%">
      <img src="./screenshots/dark-mode.webp" loading="lazy" alt="Dark Mode">
      <p align="center"><em>Dark Mode</em></p>
    </td>
  </tr>
</table>

</div>

## Features

### Case Studies, Not Screenshots

A structured narrative format that showcases your engineering thinking, not just the final product.

- **Structured storytelling**: Problem → Constraints → Approach → Decisions → Impact → Learnings
- **Key decisions with reasoning**: Document trade-offs and alternatives considered
- **Quantifiable impact**: Metrics and qualitative outcomes in every case study
- **Featured projects**: Highlight your best work on the homepage

### Decision Documentation

Built-in decision log for architectural and technical decisions (ADRs).

- Context and background for each decision
- Alternatives with pros/cons analysis
- Reasoning and outcome documentation
- Tag-based categorization

### Professional Content Collections

Multiple content types designed for engineering portfolios.

- **Projects**: Case studies with structured narrative format
- **Decisions**: Technical decision records with alternatives analysis
- **Journey**: Career timeline with milestones, learnings, and transitions
- **Writing**: Blog posts with auto-generated table of contents
- **Speaking**: Conference talks, podcasts, and workshops
- **Uses**: Tools, tech stack, and development environment
- **Testimonials**: Colleague and client recommendations

### Performance & SEO

Static site generation with modern optimizations.

- Zero JavaScript by default — minimal JS only where needed
- Automatic image optimization with Sharp
- SEO-ready with Open Graph, Twitter Cards, and JSON-LD structured data
- Auto-generated sitemap for search engines
- Strong Lighthouse performance with sensible defaults

### Developer Experience

Clean codebase with sensible defaults.

- **Astro 5** with View Transitions for smooth navigation
- **TypeScript** with strict type checking
- **Zod schemas** for content validation
- **Modern CSS** with custom properties — framework-agnostic, long-term maintainable
- **Environment-based config** — customize via `.env` file

### Theming & Customization

Fully customizable without touching the core code.

- Light/dark mode with system preference detection
- CSS custom properties for colors, typography, and spacing
- Configurable navigation and social links
- Analytics ready (Plausible, Fathom, Google Analytics)

## Quick Start

### 1. Create a new project

```bash
npm create astro@latest -- --template erlandv/case
```

### 2. Configure your site

```bash
cp .env.example .env
# Edit .env with your information
```

### 3. Start development

```bash
npm run dev
```

Your site is now running at [http://localhost:4321](http://localhost:4321)

## Documentation

Full documentation is available in the [`docs/`](./docs/) folder:

- [Getting Started](./docs/getting-started.md) — Installation, setup, and project structure
- [Configuration](./docs/configuration.md) — Environment variables and site settings
- [Content Guide](./docs/content-guide.md) — Adding projects, decisions, articles, and more
- [Customization](./docs/customization.md) — Styling, colors, typography, and layouts
- [Deployment](./docs/deployment.md) — Deploy to Netlify, Vercel, GitHub Pages, and more
- [Troubleshooting](./docs/troubleshooting.md) — Common issues and solutions

## License

Case Theme is free for personal and commercial use under the [MIT License](./LICENSE). Attribution is not required, but a link back to this repository is always appreciated if you find the theme useful.
