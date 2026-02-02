# CLAUDE.md - AI Assistant Guide for Wyzurd Hugo Website

This document provides guidance for AI assistants working with this Hugo-based static website repository.

## Project Overview

**Wyzurd** is a professional portfolio website for a Digital Imaging Technician (DIT) built with Hugo. The site showcases services (DIT work, color grading, display calibration, live VFX), a blog, and a resume.

- **URL**: https://wyzurd.com
- **Framework**: Hugo (static site generator)
- **Theme**: PaperMod with hugo-shortcode-gallery
- **Content Management**: Frontmatter CMS compatible

## Directory Structure

```
wyzurd-hugo/
├── archetypes/           # Templates for new content (hugo new)
├── assets/               # Hugo asset pipeline (SCSS, JS processing)
├── content/              # Markdown content files
│   ├── blog/             # Blog posts
│   ├── home/             # Homepage content
│   ├── resume/           # Resume page
│   ├── services/         # Service pages (dit, color, calibration, livevfx)
│   └── about/            # About page
├── layouts/              # Custom Hugo templates
│   └── shortcodes/       # Custom shortcodes
├── public/               # Generated static output (git submodule)
├── resources/            # Hugo-generated cache (_gen/)
├── static/               # Static assets served directly
│   ├── blog/             # Blog images
│   ├── calibration/      # Calibration service images
│   ├── color/            # Color service images
│   ├── dit/              # DIT service portfolio images
│   ├── livevfx/          # Live VFX images
│   └── profile/          # Profile pictures
├── themes/               # Theme submodules (PaperMod, hugo-shortcode-gallery)
├── hugo.yaml             # Main Hugo configuration
├── frontmatter.json      # Frontmatter CMS configuration
└── .gitmodules           # Git submodule definitions
```

## Hugo Configuration

The main configuration file is `hugo.yaml`:

- **baseURL**: `https://wyzurd.com`
- **Themes**: PaperMod (primary), hugo-shortcode-gallery (for galleries)
- **Profile Mode**: Enabled - displays personal branding on homepage
- **Menu Items**: Home, Blog, Resume (Services buttons on profile)

## Content Management

### Creating New Content

**Blog Posts:**
```bash
hugo new content/blog/YYYY-MM-DD-post-title.md
```

**Service Pages:**
```bash
hugo new content/services/service-name.md
```

### Frontmatter Template

All content files use this standard frontmatter:

```yaml
---
draft: false          # Set to true to hide from published site
title: "Post Title"
description: "Brief description for SEO"
date: 2025-01-29T12:00:00.000Z
preview: "Preview text shown in listings"
tags: ["tag1", "tag2"]
categories: []
---
```

### Content Naming Conventions

- **Blog posts**: `YYYY-MM-DD-title-slug.md` or use page bundles for posts with local images
- **Page bundles**: `YYYY-MM-DD-title/index.md` with `images/` subdirectory
- **Static pages**: `section/index.md`

### Draft Management

- Set `draft: true` in frontmatter to hide content from production
- Drafts are visible in development with `hugo server -D`

## Shortcodes

### Custom: sidebyside

Display multiple images in a flexible row layout:

```markdown
{{< sidebyside
    src1="/dit/image1.jpg" alt1="Description 1"
    src2="/dit/image2.jpg" alt2="Description 2"
    src3="/dit/image3.jpg" alt3="Description 3"
    width="250px"
>}}
```

Parameters:
- `src1` through `src6`: Image paths (from /static/)
- `alt1` through `alt6`: Alt text for accessibility
- `width`: Image width (default: 200px)

### Built-in: figure

Single image with optional caption:

```markdown
{{< figure src="/path/image.jpg" alt="Description" width="300px" >}}
```

### Gallery Shortcode (from theme)

For lightbox galleries with thumbnails:

```markdown
{{< gallery match="images/*" sortOrder="desc" rowHeight="150" margins="5"
    thumbnailResizeOptions="600x600 q90 Lanczos" showExif=true
    previewType="blur" embedPreview=true loadJQuery=true >}}
```

## Development Workflow

### Running Locally

```bash
# Start development server (default port 1313)
hugo server

# Include draft content
hugo server -D

# Build for production
hugo
```

### Common Tasks

**Add a new blog post:**
1. Create file in `content/blog/` with proper naming
2. Add frontmatter with required fields
3. Write content in Markdown
4. Add images to `/static/blog/` and reference as `/blog/image.jpg`

**Add images to a service page:**
1. Place images in `/static/<service>/`
2. Use `sidebyside` shortcode or `figure` shortcode in the markdown

**Update profile:**
- Edit `hugo.yaml` under `params.profileMode`

### Building for Production

```bash
hugo --minify
```

Output goes to `/public/` directory.

## Static Assets

### Image Organization

Images are stored in `/static/` with this structure:
- `/static/blog/` - Blog post images
- `/static/dit/` - DIT portfolio images
- `/static/color/` - Color grading examples
- `/static/calibration/` - Calibration work samples
- `/static/livevfx/` - Live VFX examples
- `/static/profile/` - Profile pictures

### Referencing Images in Content

Always use absolute paths from the static root:
```markdown
![Alt text](/blog/my-image.jpg)
{{< figure src="/dit/project.jpg" alt="Project name" >}}
```

### Supported Formats

- JPEG/JPG - primary format for photos
- PNG - for graphics with transparency
- WEBP - for optimized web images

## Git Submodules

This repository uses git submodules for themes:

```bash
# Clone with submodules
git clone --recurse-submodules <repo-url>

# Update submodules
git submodule update --init --recursive

# Update themes to latest
git submodule update --remote themes/PaperMod
git submodule update --remote themes/hugo-shortcode-gallery
```

## Frontmatter CMS

The project is configured for Frontmatter CMS (VS Code extension):

- **Content folders**: Blog Posts, Services
- **Preview host**: http://localhost:1313
- **Public folder**: `/static/`

Snippets available:
- "Resize Image" - Figure shortcode
- "Gallery" - Multiple gallery items
- "GPT Gallery" - Side-by-side images
- "Lightbox Gallery" - Advanced gallery with EXIF

## Key Conventions for AI Assistants

### Do:
- Use proper date format (YYYY-MM-DD) in filenames
- Include complete frontmatter on all new content
- Place images in the appropriate `/static/` subdirectory
- Use shortcodes for image layouts (sidebyside, figure, gallery)
- Keep draft: false when content is ready to publish
- Use descriptive alt text for accessibility

### Don't:
- Create new content types without updating frontmatter.json
- Put images directly in /content/ (use /static/ instead)
- Modify theme files directly (they're submodules)
- Remove the .gitmodules file or break submodule references
- Use relative paths for images in content files

### When Editing Service Pages:
- Service pages heavily use the `sidebyside` shortcode for portfolios
- Images should be consistently sized (width parameter)
- Maintain the existing visual style

### When Adding Blog Posts:
- Follow the date-title naming pattern
- Use page bundles for posts with many local images
- Add appropriate tags for categorization

## Troubleshooting

**Hugo not finding themes:**
```bash
git submodule update --init --recursive
```

**Images not showing:**
- Verify image is in `/static/`
- Check path starts with `/` (absolute from static root)
- Confirm file extension matches exactly (case-sensitive)

**Draft content missing:**
- Check `draft: true/false` in frontmatter
- Use `hugo server -D` to see drafts locally
