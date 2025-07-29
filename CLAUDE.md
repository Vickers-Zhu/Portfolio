# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a React-based portfolio website built with Vite, Bootstrap 5, and SCSS. It's a data-driven portfolio template that supports multiple languages and themes, with content stored in JSON files rather than hardcoded in components.

## Development Commands

```bash
# Start development server
npm run dev

# Build for production  
npm run build

# Run linting
npm run lint

# Preview production build
npm run preview
```

## Architecture

### Core Structure
- **Data-driven**: All content (text, images, configuration) lives in `public/data/` as JSON files
- **Provider pattern**: Uses multiple React context providers for state management (DataProvider, LanguageProvider, ThemeProvider, etc.)
- **Component architecture**: Modular components organized by purpose in `src/components/`

### Key Directories
- `public/data/` - All portfolio content and configuration (sections/, settings.json, strings.json, structure.json)
- `public/images/` - All assets (pictures, flags, svg icons)
- `src/components/` - React components organized by type:
  - `articles/` - Content components (ArticleCards, ArticleTimeline, etc.)
  - `generic/` - Reusable UI components (InfoCard, ProjectCard, etc.)
  - `nav/` - Navigation components (desktop/mobile)
  - `modals/` - Modal components
  - `providers/` - React context providers
- `src/styles/` - SCSS files with Bootstrap customization

### Configuration System
- `public/data/settings.json` - Main configuration (profile, preloader, EmailJS setup, supported languages)
- `public/data/structure.json` - Defines sections and categories for navigation
- `public/data/strings.json` - Global text translations
- Individual section JSON files in `public/data/sections/` define content for each portfolio section

### Styling
- Uses Bootstrap 5 with SCSS customization
- Theme variables in `src/styles/_variables.scss`
- Component-specific SCSS files co-located with JSX files

### Internationalization
- Multi-language support via LanguageProvider
- Translations stored in JSON files with locale objects
- Helper functions: `getString()` for global strings, `getTranslation()` for section-specific content

### Build Configuration
- Vite config at root with React plugin and SCSS preprocessing
- Base path configurable for different deployment scenarios
- Production builds output to `dist/` folder

## Important Notes

- Content changes only require editing JSON files in `public/data/`, not React components
- EmailJS integration for contact form (requires API keys in settings.json)
- Responsive design with mobile/desktop navigation variants
- Image caching system for performance optimization