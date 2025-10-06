# Copilot Instructions for Giuseppe La Tona's Academic Website

## Project Overview
This is a Jekyll-based academic website for Giuseppe La Tona, a researcher at CNR-INM, hosted on GitHub Pages. The site uses the **Minimal Mistakes** remote theme and follows Jekyll conventions for academic portfolios.

## Architecture & Key Components

### Core Structure
- **Jekyll + Minimal Mistakes Theme**: Uses `remote_theme: "mmistakes/minimal-mistakes@4.26.2"` 
- **GitHub Pages Deployment**: Configured via `github-pages` gem, auto-deploys from `main` branch
- **Content Organization**: Academic sections (about, research, publications, CV) as top-level markdown files
- **Navigation**: Controlled via `_data/navigation.yml` for main menu structure
- **Home Page**: Uses `layout: home` in `index.md` with news updates and construction notice

### Critical Configuration Files
- `_config.yml`: Contains complete site configuration, author profile, social links, and theme settings
- `Gemfile`: Uses `github-pages` gem group for GitHub Pages compatibility
- `_data/navigation.yml`: Defines main navigation menu structure (About, Research, Publications, CV)

### Content Pattern
Each main section (about, research, publications, cv) follows this pattern:
```yaml
---
layout: single
title: "Page Title"
permalink: /section/
author_profile: true
---
```

## Development Workflow

### Local Development
```bash
# Install dependencies
bundle install

# Serve locally (auto-rebuilds on changes)
bundle exec jekyll serve

# Alternative with live reload
bundle exec jekyll serve --livereload
```

### Content Management
- **Academic Profile**: Edit `author` section in `_config.yml` for bio, links, and profile image
- **Site Metadata**: Update `title`, `description`, `url` in `_config.yml`
- **Navigation**: Modify `_data/navigation.yml` to add/remove menu items
- **News Updates**: Edit `index.md` for latest news section
- **Academic Content**: Uses figure elements with captions for images (see `about.markdown` for pattern)

### Asset Management
- **Images**: Store in `assets/images/` (bio-photo.jpeg, about-page-photo.jpeg)
- **Social Icons**: Uses Font Awesome and Academicons (configured in author profile)
- **Image Pattern**: Use Jekyll figure syntax with align-center class and figcaptions

## Project-Specific Conventions

### Academic Content Structure
- Use `layout: single` with `author_profile: true` for main content pages
- Include `permalink` for clean URLs (e.g., `/about/`, `/research/`)
- News updates go in `index.md` with construction notice pattern

### Profile Configuration
The site heavily relies on the `author` section in `_config.yml`:
- `avatar`: Path to profile image (`/assets/images/bio-photo.jpeg`)
- `bio`: Short researcher description with CNR-INM affiliation
- `links`: Array of professional links including CNR page, LinkedIn, ORCID, Google Scholar
- Academic icons: Uses both Font Awesome (`fab`) and Academicons (`ai`) for academic profiles

### Theme & Analytics Configuration
- Skin: Uses `"default"` minimal mistakes skin
- Analytics: Google Analytics configured via `analytics.provider: "google-gtag"` with tracking ID
- SEO: Includes Jekyll plugins for sitemap and feeds
- Footer: Contains social links and privacy policy link

## Integration Points

### GitHub Pages
- Deploys automatically from `main` branch
- Uses `github-pages` gem for compatibility
- Excluded files defined in `_config.yml` exclude list

### Dev Container Support
- Configured for Jekyll development in `.devcontainer/devcontainer.json`
- Includes Copilot and GitHub extensions
- Uses Microsoft's Jekyll dev container image

### External Dependencies
- **Minimal Mistakes Theme**: All styling and layouts come from remote theme
- **Font Awesome & Academicons**: For social/academic icons
- **Jekyll Plugins**: Feed, sitemap, include-cache for enhanced functionality

## Common Tasks
- **Adding new pages**: Create markdown file with proper frontmatter, add to navigation.yml
- **Updating profile**: Modify `author` section in `_config.yml`
- **News updates**: Edit latest news section in `index.md`
- **Theme updates**: Update version in `remote_theme` line in `_config.yml`