# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a personal blog built with Jekyll 4.4.1, using the "Journal" theme from JekyllThemes.io. The site is written in French and focuses on personal reflections, LGBT topics, geek culture, and music. It's deployed on Netlify with automated build scheduling based on future-dated posts.

## Essential Commands

### Development
```bash
# Install dependencies
bundle install

# Run local development server
bundle exec jekyll serve

# Build the site
bundle exec jekyll build
```

### Testing Posts
When creating or editing posts, the local development server will regenerate the site automatically. Posts with future dates will only appear once that date is reached (unless running with `--future` flag).

## Architecture

### Core Directory Structure

- **`_posts/`** - Blog posts in Markdown, named `YYYY-MM-DD-slug.md`
- **`_pages/`** - Static pages (About, Contact, etc.)
- **`_projects/`** - Project showcase posts
- **`_layouts/`** - HTML templates (default, post, page, project)
- **`_includes/`** - Reusable HTML components (header, footer, contact-form, socials)
- **`_data/settings.yml`** - All theme configuration (colors, fonts, menus, social links, contact form)
- **`_sass/`** - SCSS stylesheets
  - `_includes/` - Component-specific styles (blog, gallery, header, footer, webmentions, etc.)
- **`css/style.scss`** - Main stylesheet that imports SASS partials and injects variables from settings.yml

### Configuration System

The site uses a dual configuration approach:

1. **`_config.yml`** - Jekyll core configuration (collections, permalinks, plugins, markdown settings)
2. **`_data/settings.yml`** - Theme-specific settings (site title, colors, fonts, menu items, social links)

When modifying theme appearance or behavior, always check `_data/settings.yml` first - it controls most visual and functional aspects through a structured YAML format.

### Collections & Permalinks

- Posts: `/blog/:year/:month/:day/:slug`
- Projects: `/project/:slug`
- Pages: `/:name`

### Scheduled Publishing Workflow

The site implements an automated publishing system for future-dated posts:

**`.github/workflows/next_build_date.yml`**
- Triggers on pushes that modify `_posts/**.md`
- Scans modified post files for future dates
- Stores the earliest future date as a GitHub Actions artifact (`next-build.txt`)
- If no future posts exist, stores "none"

**`.github/workflows/daily.yml`**
- Runs daily at 00:05 UTC via cron schedule
- Downloads the `next-build.txt` artifact
- Compares stored date with current date
- If dates match: triggers Netlify build via webhook (`NETLIFY_BUILD_HOOK` secret)
- If no match: skips build (saves build minutes)

This workflow ensures posts scheduled for future publication automatically go live without manual intervention.

### Front Matter Structure

Standard post front matter:
```yaml
---
title: Post Title
description: SEO description
date: YYYY-MM-DDTHH:MM:SS.SSSZ
featured_image: /images/article_images/path/to/image.jpg
tags: [tag1, tag2]
layout: post
subtitle: Optional subtitle
fmContentType: Post
lastmod: YYYY-MM-DDTHH:MM:SS.SSSZ  # Optional, for tracking modifications
---
```

### Theme Features

- **Ajax Loading**: Can be enabled/disabled in `_data/settings.yml` (`ajax_loading: true/false`)
- **Pagination**: Set to 6 posts per page in `_config.yml`
- **Contact Form**: Uses Formspree integration (configured in `_data/settings.yml`)
- **Image Galleries**: Supports multi-column galleries with `<div class="gallery" data-columns="N">` syntax
- **Social Links**: Managed via `_data/settings.yml` social_settings section
- **Syntax Highlighting**: Uses Rouge with Kramdown markdown processor

## Content Creation Guidelines

### Writing Posts

1. Create new file in `_posts/` with format: `YYYY-MM-DD-slug.md`
2. Use French language for content (site default)
3. Include proper front matter with at least: title, date, layout
4. Featured images go in `/images/article_images/YYYY/MM/`
5. For scheduled publishing, set future date - automated workflow will handle deployment

### Image Galleries

Use this HTML structure within Markdown:
```html
<div class="gallery" data-columns="3">
  <img src="/images/path/to/image1.jpg" alt="Description"/>
  <img src="/images/path/to/image2.jpg" alt="Description"/>
  <img src="/images/path/to/image3.jpg" alt="Description"/>
</div>
```

## Jekyll Plugins

Active plugins (defined in `_config.yml` and `Gemfile`):
- `jekyll-paginate` - Blog post pagination
- `jekyll-sitemap` - Automatic sitemap.xml generation
- `jekyll-youtube` - YouTube video embedding
- `jekyll-feed` - RSS/Atom feed generation (with tag support)

## Deployment

- Platform: Netlify
- Build hook triggered by GitHub Actions daily workflow
- Custom `_redirects` file included for URL redirects
- Ruby version: Specified in `.ruby-version`

## Netlify Image CDN

This site uses Netlify Image CDN for automatic image optimization, resizing, and format conversion (WebP/AVIF).

### How It Works

Images are automatically optimized on-demand and cached at the edge. The site contains large images (some 10-15MB) that are served in optimized sizes based on their usage context.

### Image Transformation Include

Use the `netlify-image.html` include to generate optimized image URLs:

```liquid
{% capture optimized_url %}
  {% include netlify-image.html src="/images/photo.jpg" width=800 height=600 fit="cover" quality=80 %}
{% endcapture %}
<img src="{{ optimized_url | strip }}" alt="Description">
```

**Parameters:**
- `src` (required) - Image source path (relative or absolute URL)
- `width` - Target width in pixels
- `height` - Target height in pixels
- `fit` - Resize mode: `cover` (crop to fit), `contain` (maintain aspect ratio), `fill` (stretch)
- `quality` - Image quality 1-100 (default: 80)

### Current Implementation

**Blog listing (index.html):**
- Featured images: 800px wide, cover fit, quality 80

**Social media meta tags (default.html):**
- Twitter/OpenGraph images: 1200x630px, cover fit, quality 85

**Projects page:**
- Portfolio images: 600x400px, cover fit, quality 80

### URL Shortcuts (netlify.toml)

The following redirect shortcuts are configured for cleaner URLs:

- `/img/thumb/*` → 400x300px, quality 75
- `/img/medium/*` → 800px wide, quality 80
- `/img/large/*` → 1200px wide, quality 80
- `/img/xlarge/*` → 1600px wide, quality 80

Example: `/img/medium/images/photo.jpg` automatically applies medium-size transformation.

### Adding Images to Posts

For featured images in post front matter:
```yaml
featured_image: /images/article_images/2025/01/photo.jpg
```

The template automatically applies appropriate optimizations when displaying the image.

### Local Development

The Image CDN include automatically detects the environment and adapts accordingly:

**Development mode (both methods work identically):**
```bash
# Option 1: Standard Jekyll
bundle exec jekyll serve

# Option 2: Netlify Dev (recommended)
netlify dev
```
- Images use their original paths (no Image CDN transformation)
- Avoids errors when Image CDN is not available locally
- Faster local builds
- `netlify dev` provides additional Netlify features (redirects, functions, etc.)

**Production mode (for testing Image CDN locally):**
```bash
JEKYLL_ENV=production bundle exec jekyll serve
```
- Images use Image CDN URLs
- Requires `netlify dev` running simultaneously to serve transformed images
- Useful for testing image transformations before deploying

**Environment Detection:**
- The `netlify-image.html` include checks `jekyll.environment`
- Returns original image path if not "production" (default for local dev)
- Returns Image CDN URL if "production" (automatic on Netlify builds)
- Configuration in `netlify.toml`:
  - `[build]` section: Uses `JEKYLL_ENV=production` for Netlify builds
  - `[dev]` section: No JEKYLL_ENV set → defaults to development mode

## Theme Customization

To modify visual appearance, edit `_data/settings.yml` sections:
- `basic_settings` - Site title, tagline, favicon
- `header_settings` - Logo, background image, overlay opacity
- `menu_settings` - Navigation menu items
- `color_settings` - All color values
- `font_settings` - Font families and typographic scales
- `advanced_settings` - Analytics, custom CSS/JS, Ajax loading

Avoid modifying theme files directly unless necessary - most changes can be achieved through settings.yml configuration.
