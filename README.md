# marklechner's Website

[![Deploy Hugo site to Pages](https://github.com/marklechner/marklechner.github.io/actions/workflows/hugo.yaml/badge.svg)](https://github.com/marklechner/marklechner.github.io/actions/workflows/hugo.yaml)

Mark's personal website built with Hugo and deployed to GitHub Pages.

## Quick Start Guide

### Prerequisites
- [Hugo Extended](https://gohugo.io/installation/) (v0.137.1 or later)
- Git
- Text editor (VS Code recommended)

### Local Development

#### 1. Clone and Setup
```bash
git clone git@github.com:marklechner/marklechner.github.io.git
cd marklechner.github.io
```

#### 2. Start Local Development Server
```bash
hugo server -D
```
- Opens at `http://localhost:1313`
- Auto-reloads when you make changes
- The `-D` flag includes draft content

#### 3. Create New Content

**For a new blog post:**
```bash
hugo new posts/my-new-post.md
```

**For a new project:**
```bash
hugo new projects/my-new-project.md
```

**Manual creation:** Create files directly in `content/posts/` or `content/projects/`

#### 4. Content Structure

All content files need front matter at the top:

```toml
+++
draft = false
date = '2025-01-15T14:00:00+01:00'
title = 'My Post Title'
+++

Your content goes here...
```

**Important:** 
- Set `draft = false` when ready to publish
- Use past dates (not future dates) or the content won't appear on the live site
- For projects, you can include categories and tags if needed

### Testing and Deployment

#### 1. Test Locally
```bash
# Clean build (removes public/ directory)
rm -rf public/

# Build for production (same as GitHub Actions)
hugo --gc --minify --baseURL "https://marklechner.github.io/"

# Verify the build worked
ls public/  # Should see your content
```

#### 2. Deploy to Production
```bash
# Add your changes
git add .

# Commit with a descriptive message
git commit -m "Add new post about XYZ"

# Push to trigger deployment
git push
```

**Deployment Process:**
1. Push triggers GitHub Actions workflow
2. Hugo builds the site automatically
3. Site deploys to GitHub Pages
4. Usually takes 2-3 minutes to go live

### Content Management Tips

#### Writing Posts
- Use Markdown for formatting
- Add images to `static/images/` and reference as `/images/filename.png`
- For code blocks, use triple backticks with language: ````markdown ```python````

#### Mermaid Diagrams
The site supports Mermaid diagrams:
````markdown
```mermaid
flowchart LR
    A[Start] --> B[Process] --> C[End]
```
````

#### Front Matter Options
```toml
+++
draft = false                    # Set to true to hide from production
date = '2025-01-15T14:00:00+01:00'  # Publication date (use past dates!)
title = 'Post Title'             # Required
categories = ["tech", "security"] # Optional
tags = ["hugo", "web"]           # Optional
+++
```

### Troubleshooting

#### Content Not Appearing?
1. Check the date isn't in the future
2. Ensure `draft = false`
3. Verify the file is in the correct directory (`content/posts/` or `content/projects/`)
4. Test locally first with `hugo server -D`

#### Build Failures?
1. Check GitHub Actions tab for error details
2. Test the build locally: `hugo --gc --minify --baseURL "https://marklechner.github.io/"`
3. Common issues:
   - Invalid front matter syntax
   - Missing closing `+++` markers
   - Future dates in content

#### Local Development Issues?
```bash
# Clean everything and restart
rm -rf public/ resources/
hugo server -D
```

### Site Structure
```
├── content/
│   ├── posts/          # Blog posts
│   ├── projects/       # Project pages
│   └── about.md        # About page
├── static/
│   └── images/         # Images and static files
├── themes/hugo-coder/  # Theme (don't modify directly)
├── layouts/            # Custom layout overrides
└── hugo.toml          # Site configuration
```

### Useful Commands
```bash
# Start development server
hugo server -D

# Build for production
hugo --gc --minify --baseURL "https://marklechner.github.io/"

# Create new content
hugo new posts/filename.md
hugo new projects/filename.md

# Check Hugo version
hugo version

# Clean build artifacts
rm -rf public/ resources/
```

### GitHub Actions Workflow
The site automatically deploys when you push to the `main` branch. The workflow:
1. Installs Hugo v0.137.1
2. Builds the site with production settings
3. Deploys to GitHub Pages

No manual intervention needed - just push your changes!

---

**Live Site:** https://marklechner.github.io/
