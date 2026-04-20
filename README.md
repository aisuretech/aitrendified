# AI Trendified - Next.js TED Talk Digest with AI Summaries and Essay Pages

AI Trendified is a Next.js and TypeScript web app for learners, curious professionals, and developers who want daily trend-driven TED Talk curation with AI summaries.

Built for fast discovery and strong search visibility, it combines server-side rendering, structured SEO metadata, dynamic sitemap generation, and API-based digest workflows.

## Live Demo
- Production: https://aitrendified.com

<!-- Use absolute production URLs for README images (https://...), not relative paths. -->
![AI Trendified homepage preview](https://aitrendified.com/images/og-default.jpg)

## Why This Project Is Discoverable on GitHub
- Uses clear domain keywords across title, intro, features, and stack: Next.js, TED Talks, AI summaries, SEO, SSR.
- Includes runnable setup commands for npm users and explicit environment variable guidance.
- Documents real route architecture and backend API integration patterns from the codebase.
- Covers common search-intent FAQ queries for learners and developers evaluating AI-curated content platforms.

## Table of Contents
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Environment Variables](#environment-variables)
- [Architecture](#architecture)
- [Learning Modules](#learning-modules)
- [Deployment](#deployment)
- [SEO and Performance](#seo-and-performance)
- [Screenshots](#screenshots)
- [Use Cases](#use-cases)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [FAQ](#faq)
- [Suggested GitHub Topics](#suggested-github-topics)
- [Links](#links)
- [License](#license)

## Features

### For Learners
- Browse daily trending topics paired with relevant TED Talks in a single digest view.
- Read AI-generated summaries, quotes, and discussion prompts to understand talks quickly.
- Open full essay pages for deeper topic reflection and guided learning.
- Explore archive pages by date to revisit historical trend snapshots.

### For Developers
- Next.js Pages Router app with TypeScript, SSR, and route-level data fetching.
- API service layer that transforms flat backend rows into frontend-friendly topic/talk/summary models.
- Built-in SEO utilities for meta tags, Open Graph, Twitter cards, canonical URLs, and schema markup.
- Test coverage with Jest and React Testing Library for key components and SEO utilities.

## Tech Stack
- Frontend: Next.js 16, React 19, TypeScript, CSS Modules
- Runtime/Platform: Node.js 18+ (recommended), npm, Vercel-compatible deployment
- Analytics and Monitoring: Not configured by default in this repository
- Testing: Jest, ts-jest, React Testing Library, jest-dom
- PWA: Web App Manifest (`site.webmanifest`) with app icons and install metadata

## Quick Start

### Prerequisites
- Node.js 18.x or newer
- npm 9.x or newer

### Install and Run
```bash
npm install
npm run dev
```

Open http://localhost:3000

### Build and Validate
```bash
npm run lint
npm run test
npm run build
npm run start
```

## Project Structure
```text
digest/
|- pages/
|  |- index.tsx
|  |- archive.tsx
|  |- ai-investing.tsx
|  |- digest/[date].tsx
|  |- talk/[id].tsx
|  |- sitemap.xml.tsx
|  |- robots.txt.tsx
|  |- _app.tsx
|  |- _document.tsx
|- components/
|  |- Layout.tsx
|  |- DateNavigation.tsx
|  |- TopicList.tsx
|  |- TalkCard.tsx
|  |- SummaryBlock.tsx
|- services/
|  |- api.ts
|- utils/
|  |- seo.ts
|  |- faqSchema.ts
|- styles/
|  |- globals.css
|  |- *.module.css
|- __tests__/
|  |- components/*.test.tsx
|  |- utils/*.test.ts
|- public/
|  |- images/
|  |- site.webmanifest
|- package.json
|- next.config.ts
|- tsconfig.json
```

## Environment Variables
Create a .env file in the project root:

```env
NEXT_PUBLIC_API_BASE_URL=http://localhost:8000/api
NEXT_PUBLIC_SITE_URL=http://localhost:3000
NEXT_PUBLIC_SITE_NAME=AI Trendified
NEXT_PUBLIC_SITE_DESCRIPTION=Daily trending content with matched TED Talks, AI summaries, and insightful essays
```

## Architecture
This project uses SSR-first Next.js pages that fetch digest data from backend endpoints, normalize flat API rows, and render SEO-optimized learning pages.

1. The homepage fetches the latest digest from `/digest/digest-data` via `getServerSideProps`.
2. The service layer normalizes flat rows into `topics`, `talks`, and `summaries` for UI components.
3. Date-based archive pages fetch scoped data from `/digest/digest-data-by?digestDate=...`.
4. Essay pages load detailed markdown-like content from `/digest/essay?essayId=...`.
5. Layout and SEO utilities generate canonical metadata, Open Graph tags, and structured data on every page.

```text
User Request -> Next.js Page Route -> getServerSideProps -> services/api.ts
-> Backend Digest API -> transformDigestRows -> React Components
-> Layout SEO Meta + Schema -> Rendered HTML + Sitemap/Robots
```

## Learning Modules
- Daily Digest module: topic discovery with matched TED Talks and trend context.
- Talk Exploration module: summaries, quotes, tags, and outbound watch links.
- Deep Dive module: discussion prompts and essay pages for extended learning.
- Resource Expansion module: curated links, archive navigation, and related educational pages.

## Deployment
Recommended deployment target: Vercel

```bash
npm install
npm run build
npm run start
```

Production URL:
- https://aitrendified.com

## SEO and Performance
- Server-side rendering on core pages for crawlable content and strong first paint.
- Dynamic metadata generation with canonical URLs, Open Graph, and Twitter Card tags.
- Structured data support (Organization, Website, Breadcrumb, Article schema patterns).
- Dynamic sitemap and robots routes for discoverable indexing and crawl guidance.
- Optimized image handling with Next.js plus configured remote image patterns.
- Semantic page structure and descriptive route paths for user and search intent clarity.

## Screenshots
<!-- Use absolute production URLs for all screenshot images (https://...), not ./assets paths. -->

| Feature | Preview |
|--------|--------|
| Homepage Digest Experience | ![](https://aitrendified.com/images/og-default.jpg) |
| Branding and Identity | ![](https://aitrendified.com/logo.png) |

## Use Cases
- Learn key ideas from trending TED Talks in minutes before watching full videos.
- Build daily reading or team learning routines around AI-curated topic digests.
- Prototype and extend a SEO-focused educational content platform using Next.js.
- Integrate with custom backend pipelines that produce trend, talk, and summary rows.

## Roadmap
- [ ] Add first-party analytics and performance monitoring dashboards.
- [ ] Add richer filtering and sorting by theme, duration, and recency.
- [ ] Expand test coverage for SSR routes and API failure scenarios.
- [ ] Add optional newsletter and digest subscription workflow.

## Contributing
Contributions are welcome.

1. Fork the repository
2. Create a feature branch: git checkout -b feature/your-feature
3. Commit your changes
4. Push to your branch
5. Open a pull request

## FAQ

### How do I run this Next.js TED digest project locally?
Install dependencies with `npm install`, run `npm run dev`, and open `http://localhost:3000`.

### Does this repository include a backend API service?
This repository is frontend-focused and expects backend endpoints for digest and essay data. The API contract is documented in the integration docs.

### Which API endpoints are required for production data?
The app expects `/digest/digest-data`, `/digest/digest-data-by?digestDate=YYYY-MM-DD`, and `/digest/essay?essayId=...` under `NEXT_PUBLIC_API_BASE_URL`.

### Is AI Trendified optimized for SEO and social sharing?
Yes. It includes SSR, dynamic metadata, canonical URLs, Open Graph/Twitter tags, and sitemap/robots support.

## Suggested GitHub Topics
Add these in repository settings for discoverability:
- nextjs
- typescript
- react
- seo
- ted-talks
- ai-summaries
- server-side-rendering
- jest-testing

## Links
- GitHub Organization: https://github.com/aisuretech/
- Website: https://aitrendified.com
- Contact: info@AISureTech.com

## License
No license file is currently defined in this repository (all rights reserved by default).
