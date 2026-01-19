# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is Piyush Bhandari's personal portfolio website - a modern, minimalist portfolio built with Astro and Tailwind CSS v4. It's designed to be easily customizable through a single configuration file while maintaining a clean, professional appearance.

**Live Site**: https://piyushbhandaricode.github.io/
**Repository**: https://github.com/piyushbhandaricode/piyushbhandaricode.github.io

## Tech Stack

- **Astro**: Static site generator
- **Tailwind CSS v4**: Utility-first CSS framework using the new @tailwindcss/vite plugin
- **TypeScript**: For type-safe configuration
- **Tabler Icons**: Icon library

## Development Commands

```bash
npm run dev       # Start development server
npm run build     # Build for production
npm run preview   # Preview production build
```

## Architecture

The project follows a component-based architecture with all customization centralized in `src/config.ts`:

- **Components** (`src/components/`): Individual Astro components for each section (Hero, About, Projects, Experience, Education, Header, Footer)
- **Main Layout** (`src/pages/index.astro`): Single-page layout that imports all components
- **Configuration** (`src/config.ts`): Single source of truth for all content and customization

### Key Architectural Decisions

1. **Single Configuration File**: All content is managed through `src/config.ts` to make customization simple
2. **Conditional Rendering**: Sections automatically hide if their data is removed from the config
3. **Component Independence**: Each section is a self-contained component that reads from the config
4. **Accent Color System**: Single `accentColor` in config propagates throughout the site via CSS custom properties

## Important Implementation Details

- The site uses Tailwind CSS v4 with the Vite plugin configuration
- No linting or testing framework is currently configured
- All components are in `.astro` format (not React/Vue/etc)
- The project uses IBM Plex Mono font loaded from Google Fonts
- Social links in the config are all optional and will conditionally render

## Working with Components

When modifying components:
1. Components read directly from the imported `siteConfig` object
2. Use Tailwind utility classes for styling
3. Maintain the existing monospace font aesthetic
4. Use Tabler Icons for consistency with existing icons

## Configuration Structure

The `src/config.ts` exports a `siteConfig` object with these sections:
- Basic info: name, title, description, accentColor
- Social links: email, linkedin, twitter, github (all optional)
- aboutMe: string
- skills: string[]
- projects: array of {name, description, link, skills}
- experience: array of {company, title, dateRange, bullets}
- education: array of {school, degree, dateRange, achievements}

## Deployment

This site is deployed to **GitHub Pages** using **GitHub Actions**.

### Deployment Configuration

1. **Repository Type**: User GitHub Pages site (username.github.io format)
   - Repository name MUST match: `piyushbhandaricode.github.io`
   - This allows the site to be hosted at the root domain without a base path

2. **Astro Configuration** (`astro.config.mjs`):
   ```javascript
   export default defineConfig({
     site: 'https://piyushbhandaricode.github.io',
     vite: {
       plugins: [tailwindcss()],
     },
   });
   ```
   - No `base` path is needed for user GitHub Pages sites
   - `site` URL must match the GitHub Pages domain

3. **GitHub Actions Workflow** (`.github/workflows/deploy.yml`):
   - Triggers on push to `main` branch
   - Also supports manual workflow dispatch
   - Uses `withastro/action@v3` for building
   - Deploys via `actions/deploy-pages@v4`
   - Requires GitHub Pages to be enabled in repository settings

### Deployment Process

1. Push changes to `main` branch
2. GitHub Actions automatically builds and deploys
3. Site is live within 1-2 minutes
4. Check deployment status: `gh run list --repo piyushbhandaricode/piyushbhandaricode.github.io`

### Important Notes

- **Never** change the repository name - it must stay `piyushbhandaricode.github.io`
- **Never** add a `base` path to `astro.config.mjs` - user sites use root domain
- The `.claude` directory is gitignored and contains sensitive local settings
- All content updates should go through `src/config.ts` only

## Git Workflow

- Default branch: `main`
- Remote: `git@github.com:piyushbhandaricode/piyushbhandaricode.github.io.git` (SSH)
- Deployment: Automatic on push to main
- Never commit `.claude/` directory (already in .gitignore)

## File Structure

```
├── .github/
│   └── workflows/
│       └── deploy.yml       # GitHub Actions deployment workflow
├── public/
│   └── favicon.svg          # Site favicon
├── src/
│   ├── components/          # Astro components
│   ├── pages/
│   │   └── index.astro      # Main page
│   ├── styles/
│   │   └── global.css       # Global styles
│   └── config.ts            # **SINGLE SOURCE OF TRUTH FOR ALL CONTENT**
├── astro.config.mjs         # Astro & deployment configuration
├── CLAUDE.md                # This file
├── README.md                # User-facing documentation
└── package.json             # Dependencies
```

## Content Updates

**IMPORTANT**: When updating portfolio content:
1. **ONLY** edit `src/config.ts` - never modify components directly for content changes
2. Test locally with `npm run dev` before committing
3. Commit and push to trigger automatic deployment
4. Verify changes at https://piyushbhandaricode.github.io/

## Current Portfolio Owner

- **Name**: Piyush Bhandari
- **Title**: IT Application Specialist - Developer Tools
- **Focus**: Building and shipping reliable infrastructure for developers
- **Experience**: 5+ years managing projects autonomously