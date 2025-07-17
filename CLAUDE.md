# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo static site for squaredcow.dev, a personal blog by Luis Vaca. The site uses the PaperMod theme with a sober black/white/gray design aesthetic and JetBrains Mono typography. Content focuses on technical writing, particularly distributed systems and collaborative text editing.

## Development Commands

### Local Development
```bash
# Serve the site locally with live reload
hugo server -D

# Build the site for production
hugo

# Build with drafts included
hugo -D
```

### Content Management
```bash
# Create a new post
hugo new posts/post-name/index.md

# Create a new page
hugo new page-name.md
```

## Architecture and Structure

### Content Organization
- **Posts**: Located in `content/posts/` with each post in its own directory containing `index.md`
- **Pages**: Individual markdown files in `content/` root (e.g., `author.md`, `license.md`)
- **Static Assets**: Images and other static files in `static/images/`

### Theme Customization
- **Base Template**: `layouts/_defaults/baseof.html` - PaperMod-compatible structure with theme toggle support
- **Partials**: `layouts/partials/` contains custom overrides:
  - `head.html` - Custom head template without Google Analytics, includes custom CSS
- **Custom Styling**: `assets/css/extended/custom.css` - Sober color palette and JetBrains Mono typography

### Key Features
- **Typography**: JetBrains Mono font for all text with optimized readability settings
- **Color Palette**: Sober black/white/gray scheme for both light and dark modes
- **Dark Mode**: PaperMod's native dark mode with auto system detection and manual toggle
- **Syntax Highlighting**: Configured with Dracula theme in `config.toml`
- **Privacy-Focused**: All external tracking services disabled in configuration

### Configuration
- **Main Config**: `config.toml` contains all site settings, social links, menu structure, and PaperMod-specific options
- **Theme**: Uses PaperMod theme via git submodule with custom CSS overrides
- **Dark Mode**: Controlled by `defaultTheme = "auto"` and `disableThemeToggle = false`
- **Build Output**: Generated site goes to `public/` directory

### Content Front Matter
Posts use PaperMod-compatible front matter:
```yaml
---
title: "Post Title"
date: 2021-07-31
draft: false
description: "Post description for SEO and summary"
tags: ["tag1", "tag2"]
categories: ["category"]
ShowToc: true
ShowBreadCrumbs: true
---
```

## Development Notes

- The site uses Hugo's built-in syntax highlighting with code fences and Dracula theme
- Custom styling is implemented through `assets/css/extended/custom.css` (PaperMod's extension system)
- Images are stored in `static/images/` and referenced with absolute paths
- Dark mode uses PaperMod's native implementation with system preference detection
- No build tools like npm/yarn are used - pure Hugo static site generation
- Theme installed as git submodule for easy updates

## Deployment

- **CI/CD**: GitHub Actions workflow (`.github/workflows/pipeline.yml`)
- **Hugo Version**: 0.148.1 (extended version required)
- **Target**: Deploys to GitHub Pages with custom domain (squaredcow.dev)
- **Trigger**: Automatic on push to main branch, manual via workflow_dispatch