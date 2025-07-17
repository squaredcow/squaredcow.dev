# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Hugo static site for squaredcow.dev, a personal blog by Luis Vaca. The site uses the Cactus theme and focuses on technical writing, particularly distributed systems and collaborative text editing.

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
- **Base Template**: `layouts/_defaults/baseof.html` - Main HTML structure
- **Partials**: `layouts/partials/` contains reusable components:
  - `darkmode.html` - Dark mode toggle implementation with localStorage and system preference detection
  - `head.html` - Document head with meta tags and styling
  - `footer.html` - Site footer
  - `scripts.html` - JavaScript includes

### Key Features
- **Dark Mode**: Custom implementation with system preference detection and localStorage persistence
- **Syntax Highlighting**: Configured with Dracula theme in `config.toml`
- **Privacy-Focused**: All external tracking services disabled in configuration
- **Responsive Design**: Uses maxWidthclass and mobile-first approach

### Configuration
- **Main Config**: `config.toml` contains all site settings, social links, menu structure
- **Theme**: Uses Cactus theme with custom overrides in `layouts/`
- **Build Output**: Generated site goes to `public/` directory

### Content Front Matter
Posts use standard Hugo front matter:
```yaml
---
title: "Post Title"
date: 2021-07-31
description: "Optional description"
---
```

## Development Notes

- The site uses Hugo's built-in syntax highlighting with code fences
- Custom CSS/JS modifications are done through layout overrides, not theme modification
- Images are stored in `static/images/` and referenced with absolute paths
- The dark mode implementation is custom JavaScript that respects system preferences
- No build tools like npm/yarn are used - pure Hugo static site generation