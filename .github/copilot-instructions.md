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

## Blog & Tutorial Content Structure

### Blog Post Guidelines
Blog posts capture time-sensitive updates, conference experiences, and tutorial announcements. All blog posts use the same consistent structure:

**Required Frontmatter:**
```yaml
---
layout: single
title: "Descriptive Title (50-70 chars)"
date: YYYY-MM-DD
categories: [category1, category2]
tags: [tag1, tag2, tag3]
author_profile: true
excerpt: "150-200 character preview text for listings and social sharing"
header:
  teaser: /assets/images/optional-teaser.jpg
---
```

**File Naming:** `_posts/YYYY-MM-DD-slug-title.md` (hyphenated lowercase)

**Common Categories:** `tutorials`, `conferences`, `travel`, `research-updates`, `announcements`

**Tag Conventions:**
- Research areas: `deep-learning`, `forecasting`, `energy-systems`, `machine-learning`, `optimization`
- Event types: `conference-report`, `tutorial`, `workshop`, `seminar`
- Institutions: `CNR-INM`, `IECON`, `Electrimacs`, `IEEE`
- Topics: `time-series`, `reproducibility`, `hyperparameter-tuning`

### Blog Post Structure Pattern
```markdown
---
layout: single
title: "Tutorial: [Topic]"
date: 2025-10-11
categories: [tutorials, conferences]
tags: [deep-learning, forecasting, energy-systems]
author_profile: true
excerpt: "[Brief summary for preview]"
---

## Overview
[2-3 sentence context or announcement]

## Details/Sections
- Key information organized in logical sections
- Include dates, locations, and important links
- Emphasize your role or contribution

## Links & Resources
- [Link to resources/slides/materials](url)
- [External reference](url)
```

## Content Type Decision Guide

**Use Blog Posts (`_posts/`) for:**
- Conference attendance reports and takeaways
- Tutorial or workshop announcements with dates
- Research project kickoffs or milestones
- Time-sensitive announcements or news
- Reflection pieces on academic work

**Use Main Pages for:**
- Static professional content (About, CV, Research overview)
- Complete publication listings (Publications)
- Ongoing research areas and projects
- Permanent academic biography

**Update `index.md` Latest News for:**
- Significant achievements (paper accepted, promotion, award)
- Major conference participations
- Deadline extensions or call announcements
- Professional milestones (track chair roles, etc.)

## Content Patterns & Best Practices

### Figure & Image Usage
Academic content uses figure elements with captions for clarity:
```markdown
{% include figure image_path="/assets/images/example.jpg" alt="Description" caption="Figure caption text" %}
```

Or with alignment:
```markdown
{% include figure image_path="/assets/images/example.jpg" alt="Description" caption="Caption" class="align-center" %}
```

**Image Storage:** All images go in `assets/images/`. Use descriptive filenames: `iecon2025-tutorial-teaser.jpg`, not `image1.jpg`

### Publication & Research Links
Link to multiple academic platforms consistently:
- ORCID: `https://orcid.org/XXXX-XXXX-XXXX-XXXX`
- Google Scholar: Researcher profile URL
- ResearchGate: Personal profile URL
- Institution repository: CNR profile or department page
- DOI: Use `https://doi.org/` for papers

### Internal Linking
Improve site navigation by linking related content:
- Link from publications to research areas that generated them
- Link from blog posts to relevant publications
- Link from research page to blog tutorials on that topic

### Excerpt Writing
Excerpts appear in listings and social sharing. Make them discoverable:
- Summarize the main point in 1 sentence
- Use keywords relevant to academic search (researcher name, method name, domain)
- Avoid generic phrases; be specific about contribution

Example: ❌ "An interesting paper" → ✅ "NCD-Pred forecasts multichannel ship electrical power demand using neighborhood-constrained VMD"

## Deployment Workflow & Local Testing

### Before Committing Changes
1. **Run local development server**: `bundle exec jekyll serve`
2. **Test all affected pages** in browser:
   - Check navigation links work
   - Verify images load correctly
   - Test any new URLs return 200 status
   - Validate internal links point to correct pages
3. **Check the `_site/` folder** for generated files:
   - Look for 404.html to catch broken link patterns
   - Verify assets are copied correctly
4. **Run Jekyll diagnostic**: `bundle exec jekyll doctor` to catch config issues

### Deployment Process
- Push to `main` branch → GitHub Pages auto-deploys (~1-2 minutes)
- No manual deployment step required
- Changes automatically reflected at `https://giulatona.github.io`

### Testing URLs After Deployment
```bash
# Test key pages return 200
curl -o /dev/null -w "%{http_code}" https://giulatona.github.io/
curl -o /dev/null -w "%{http_code}" https://giulatona.github.io/about/
curl -o /dev/null -w "%{http_code}" https://giulatona.github.io/research/
curl -o /dev/null -w "%{http_code}" https://giulatona.github.io/publications/
```

## SEO & Academic Discoverability

### Metadata Best Practices
- **Every page needs an excerpt** (120-160 characters): Auto-used as meta description
- **Strategic tags**: Help both internal search (Lunr.js) and academic discoverability
- **Descriptive titles**: Include key terms, avoid clickbait (academic audience expects clarity)
- **Keywords in content**: Mention your domain, methods, and research areas naturally in first paragraph

### Schema.org & Structured Data
The Minimal Mistakes theme includes microdata for:
- Author information (uses `author_profile` frontmatter)
- Publication metadata (when using correct frontmatter structure)
- Article dates and categories

No additional configuration needed—ensure frontmatter is complete for theme to generate proper schema.

### Internal Search Optimization
Lunr.js indexes all content for site-wide search:
- Search indexes page titles, tags, excerpts, and body text
- Use consistent terminology across pages (standardize: "energy management" vs "energy optimization")
- Link-rich content ranks higher in internal search results

## Common Pitfalls & Troubleshooting

### Build & Serving Issues
| Problem | Solution |
|---------|----------|
| **Jekyll serve fails or pages 404** | Run `bundle update` and `bundle install` to sync Gemfile.lock, then try again |
| **Changes not appearing locally** | Restart `jekyll serve` (Ctrl+C, then `bundle exec jekyll serve`) |
| **CSS/JS not loading** | Clear browser cache (Cmd+Shift+R or Ctrl+Shift+R) or use incognito window |

### Content & Links
| Problem | Solution |
|---------|----------|
| **Images don't show on live site** | Verify path starts with `/assets/images/`, not relative paths |
| **Links appear broken** | Test locally first; if working there, push and wait 1-2 min for GitHub Pages rebuild |
| **Navigation menu doesn't update** | Restart `jekyll serve` after editing `_data/navigation.yml` |

### Configuration Issues
| Problem | Solution |
|---------|----------|
| **Author profile missing from posts** | Ensure `author_profile: true` in frontmatter |
| **Social icons not showing** | Check `author.links` section in `_config.yml`; icons use Font Awesome (`fab:`) or Academicons (`ai:`) |
| **Analytics not tracking** | Verify `analytics.provider: "google-gtag"` and tracking ID in `_config.yml` are set |

### Date & Timezone Issues
- Use `YYYY-MM-DD` date format in all frontmatter (Jekyll default)
- Posts with future dates won't publish; ensure date is today or earlier
- GitHub Pages rebuilds from main branch; no manual publish step

## Quick Reference: File Locations

| Purpose | File | What to Edit |
|---------|------|--------------|
| Site title, author bio, social links | `_config.yml` | `title`, `author` section |
| Main navigation menu | `_data/navigation.yml` | `main:` array |
| Homepage & latest news | `index.md` | Latest news section in body |
| Main content pages | `about.markdown`, `research.md`, etc. | Page body content, permalink |
| Blog posts | `_posts/YYYY-MM-DD-slug.md` | Create new file with date prefix |
| Profile image | `assets/images/bio-photo.jpeg` | Replace existing image file |
| CSS/Theme settings | (Minimal Mistakes remote theme) | Override in `_config.yml` if needed |

## Updating the Site

### Typical Update Frequency
- **Homepage news** (`index.md`): Updated monthly or for major announcements
- **Publications** (`publications.md`): Updated when papers are published/accepted
- **Research** (`research.md`): Updated when starting new projects or pivots
- **About** (`about.markdown`): Rarely changed; static biographical content
- **Blog posts**: Added for conferences, tutorials, reflections (varies)
- **CV** (`cv.md`): Updated when significant milestones occur

### Version Updates
- **Theme**: Update `remote_theme: "mmistakes/minimal-mistakes@X.XX.X"` in `_config.yml` quarterly
- **Ruby gems**: Run `bundle update` every few months to stay current with security patches
- **GitHub Pages gem**: Auto-managed; no manual update needed

## Integration with GitHub

### Branch Strategy
- `main`: Production branch, auto-deploys to GitHub Pages
- Always edit on `main` (single-branch workflow for this small site)
- No pull request review needed for personal site, but encouraged for major changes

### Git Workflow
```bash
# Make changes locally
# Test with: bundle exec jekyll serve

# Commit (Copilot will add Co-authored-by trailer)
git add .
git commit -m "Update: [Brief description]"
git push origin main

# Verify deployment at https://giulatona.github.io (1-2 min)
```

## Resources & Documentation

- **Minimal Mistakes Theme**: [mmistakes.github.io/minimal-mistakes/](https://mmistakes.github.io/minimal-mistakes/) - Full layout and component docs
- **Jekyll Documentation**: [jekyllrb.com/docs/](https://jekyllrb.com/docs/) - Template syntax, filters, plugins
- **GitHub Pages**: [pages.github.com/](https://pages.github.com/) - Hosting features and limitations
- **Liquid Template Language**: [shopify.github.io/liquid/](https://shopify.github.io/liquid/) - Template syntax reference