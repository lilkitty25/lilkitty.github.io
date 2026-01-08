# Content Guide

All content is managed through MDX files in `src/content/`. Each content type has its own collection with schema validation.

## General Workflow

1. Navigate to the appropriate content directory
2. Create a new `.mdx` file
3. Add frontmatter with required fields
4. Write your content in Markdown/MDX
5. Run `npm run build` to validate

If your content doesn't match the schema, the build will fail with clear error messages.

---

## Projects (Case Studies)

Location: `src/content/projects/`

Case studies are the core of this theme. Each project follows a structured narrative: Problem → Constraints → Approach → Decisions → Impact → Learnings.

### Required Fields

```yaml
---
title: "Project Title"
role: "Your Role"
year: 2024
outcomeSummary: "Brief impact summary (1-2 sentences)"
overview: "High-level project overview"
problem: "What problem were you solving?"
constraints:
  - "Constraint 1"
  - "Constraint 2"
approach: "How did you approach the solution?"
keyDecisions:
  - decision: "What you decided"
    reasoning: "Why you made this decision"
    alternatives:
      - "Alternative 1"
      - "Alternative 2"
techStack:
  - "Technology 1"
  - "Technology 2"
impact:
  metrics:
    - label: "Metric Name"
      value: "Metric Value"
  qualitative: "Broader impact description"
learnings:
  - "Key learning 1"
  - "Key learning 2"
---
```

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `featured` | boolean | Show on homepage (default: `false`) |
| `order` | number | Custom sort order (lower = first) |

### Example

See `src/content/projects/payment-system-rebuild.mdx` for a complete example.

---

## Decisions

Location: `src/content/decisions/`

Document architectural and technical decisions with context, alternatives considered, and reasoning.

### Required Fields

```yaml
---
title: "Decision Title"
date: 2024-01-15
context: "What situation required this decision?"
decision: "What did you decide?"
alternatives:
  - option: "Alternative 1"
    pros:
      - "Pro 1"
    cons:
      - "Con 1"
  - option: "Alternative 2"
    pros:
      - "Pro 1"
    cons:
      - "Con 1"
reasoning: "Why did you make this decision?"
---
```

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `tags` | string[] | Categorization tags |

### Example

See `src/content/decisions/choosing-typescript-over-javascript.mdx` for a complete example.

---

## Journey

Location: `src/content/journey/`

Career timeline entries showing milestones, learnings, and transitions.

### Required Fields

```yaml
---
date: 2024-01-15
title: "Entry Title"
type: "milestone"  # Options: milestone, learning, transition
description: "What happened and what you learned"
---
```

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `skills` | string[] | Associated skills |

### Entry Types

- `milestone` — Career achievements, promotions, major accomplishments
- `learning` — Skills learned, certifications, courses completed
- `transition` — Role changes, company changes, career pivots

### Example

See `src/content/journey/transition-to-lead-engineer.mdx` for a complete example.

---

## Writing (Blog)

Location: `src/content/writing/`

Blog posts and technical articles with full MDX support.

### Required Fields

```yaml
---
title: "Article Title"
description: "Brief description for SEO"
publishDate: 2024-01-15
---
```

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `updatedDate` | date | Last updated date |
| `tags` | string[] | Article tags |
| `draft` | boolean | Hide from production (default: `false`) |

### Features

- Articles with 3+ headings automatically get a Table of Contents
- Draft articles (`draft: true`) won't appear in production builds
- Full MDX support for interactive components

### Example

See `src/content/writing/building-resilient-apis.mdx` for a complete example.

---

## Speaking

Location: `src/content/speaking/`

Conference talks, meetup presentations, podcast appearances, and workshops.

### Required Fields

```yaml
---
title: "Talk Title"
description: "Talk description"
event: "Event Name"
date: 2024-01-15
location: "City, Country"  # or "Online"
type: "conference"  # Options: conference, meetup, podcast, workshop, webinar
---
```

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `eventUrl` | string | Event website URL |
| `slides` | string | Link to slides |
| `video` | string | Link to video recording |
| `duration` | string | Talk duration (e.g., "45 min") |
| `topics` | string[] | Topics covered |
| `featured` | boolean | Highlight this talk (default: `false`) |

### Example

See `src/content/speaking/event-sourcing-patterns.mdx` for a complete example.

---

## Uses

Location: `src/content/uses/`

Document your tools, tech stack, and development environment.

### Required Fields

```yaml
---
category: "tools"  # Options: tools, stack, environment
items:
  - name: "Tool Name"
    description: "What you use it for"
order: 1
---
```

### Optional Item Fields

| Field | Type | Description |
|-------|------|-------------|
| `url` | string | Link to the tool/technology |

### Categories

- `tools` — Software tools, editors, apps
- `stack` — Programming languages, frameworks, libraries
- `environment` — Hardware, desk setup, peripherals

### Example

See `src/content/uses/my-setup.mdx` for a complete example.

---

## Testimonials

Location: `src/content/testimonials/`

Endorsements and recommendations from colleagues and clients.

### Required Fields

```yaml
---
name: "Person's Name"
role: "Their Role"
company: "Their Company"
relationship: "How you worked together"
quote: "Their testimonial text"
date: 2024-01-15
---
```

### Optional Fields

| Field | Type | Description |
|-------|------|-------------|
| `linkedin` | string | Their LinkedIn profile URL |
| `featured` | boolean | Show on homepage (default: `false`) |

### Example

See `src/content/testimonials/sarah-chen.mdx` for a complete example.

---

## Tips

### Content Validation

Run `npm run build` to validate all content against schemas. Errors will show:
- Which file has the error
- Which field is invalid
- What was expected vs. provided

### MDX Features

All content files support MDX, allowing you to:
- Use standard Markdown syntax
- Import and use Astro components
- Add interactive elements

### File Naming

Use kebab-case for file names:
- ✅ `payment-system-rebuild.mdx`
- ❌ `Payment System Rebuild.mdx`

The filename becomes the URL slug (e.g., `/projects/payment-system-rebuild`).
