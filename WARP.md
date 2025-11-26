# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a Next.js 16 application using the App Router architecture with TypeScript, React 19, and Tailwind CSS v4. The project uses Turbopack for development with file system caching enabled.

## Development Commands

### Running the Development Server
```bash
npm run dev
```
Starts the Next.js development server with Turbopack enabled (configured in `next.config.ts`).

### Building for Production
```bash
npm run build
```
Creates an optimized production build.

### Starting Production Server
```bash
npm start
```
Runs the production build locally.

### Linting
```bash
npm run lint
```
Runs ESLint with Next.js configuration. The project uses ESLint 9 with flat config format (`eslint.config.mjs`).

## Architecture

### Next.js App Router Structure
- **`app/layout.tsx`**: Root layout defining HTML structure, metadata, and Google Fonts (Geist Sans and Geist Mono)
- **`app/page.tsx`**: Home page component
- **`app/globals.css`**: Global styles with Tailwind CSS v4 import and CSS custom properties for theming

### TypeScript Configuration
- Path alias: `@/*` maps to the project root (`./`)
- Strict mode enabled
- Target: ES2017
- Uses `react-jsx` for JSX transformation

### Styling Approach
- Tailwind CSS v4 via PostCSS plugin (`@tailwindcss/postcss`)
- CSS custom properties defined in `globals.css` for theme variables
- Dark mode support using `prefers-color-scheme` media query
- Custom theme configuration using `@theme inline` directive in CSS

### Key Dependencies
- **Next.js 16.0.4**: Latest Next.js with App Router
- **React 19.2.0**: Latest React with new features
- **Tailwind CSS v4**: Using the new PostCSS-only architecture (no `tailwind.config.js` needed)

## Working with This Codebase

### Adding New Pages
Create new route files in the `app/` directory following Next.js App Router conventions:
- `app/about/page.tsx` for `/about` route
- `app/blog/[slug]/page.tsx` for dynamic routes

### Adding Components
Since there's no dedicated components directory yet, create one when needed:
- Shared components should go in a `components/` or `app/components/` directory
- Use TypeScript and React 19 conventions

### Styling Guidelines
- Use Tailwind utility classes directly in components
- Custom theme values are defined as CSS variables in `app/globals.css`
- Access theme colors via Tailwind: `bg-background`, `text-foreground`
- Font variables are set up: `font-sans` (Geist) and `font-mono` (Geist Mono)

### Static Assets
Place static files in the `public/` directory. They're accessible from the root URL path (e.g., `public/next.svg` → `/next.svg`).

### TypeScript Best Practices
- Use the `@/` alias for imports from the project root
- Leverage Next.js types: `Metadata`, `NextConfig`, etc.
- Strict mode is enabled, so handle null/undefined properly

### ESLint Configuration
The project uses ESLint 9's flat config with:
- `eslint-config-next/core-web-vitals`: Web vitals rules
- `eslint-config-next/typescript`: TypeScript-specific rules
- Custom ignores for build directories (`.next`, `out`, `build`)
