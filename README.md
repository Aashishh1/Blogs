# Ashish Mishra | AI Engineer — Blog

Personal blog by **Ashish Mishra**, AI Engineer — covering AI, Machine Learning, Data Science, MLOps, and Generative AI. Built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme. Deployed **free** on GitHub Pages.

Live at: **https://aashishh1.github.io/Blogs/**

## Tech Stack
- Hugo static site generator
- PaperMod Hugo theme (Git submodule)
- Markdown content in `content/`
- Free hosting via **GitHub Pages** + GitHub Actions (no AWS, no Netlify, no recurring cost)

## Repository Layout
```
.
├── archetypes/          # Template for new posts
├── content/
│   ├── posts/           # Blog posts
│   └── about.md         # About page
├── layouts/partials/    # Local theme overrides (optional)
├── static/images/       # Cover images and diagrams
├── themes/PaperMod/     # Theme submodule
├── .github/workflows/   # Auto build + deploy on push
├── hugo.toml            # Site configuration
└── README.md
```

## One-Time Setup (Local Machine)

### 1. Install Hugo Extended
- **Windows**: `winget install Hugo.Hugo.Extended`
- **macOS**: `brew install hugo`
- **Linux**: download the extended binary from [Hugo Releases](https://github.com/gohugoio/hugo/releases) (the apt package is often not "extended")

Verify:
```bash
hugo version
```
The output must say `extended`.

### 2. Clone this repo with the theme submodule
```bash
git clone --recurse-submodules https://github.com/Aashishh1/Blogs.git
cd Blogs
```
If you already cloned without `--recurse-submodules`:
```bash
git submodule update --init --recursive
```

### 3. Preview locally
```bash
hugo server -D
```
Open **http://localhost:1313/Blogs/** (note the `/Blogs/` path — it matches your `baseURL`). The `-D` flag also shows draft posts.

## Writing New Posts
```bash
hugo new posts/my-new-post-slug.md
```
Edit the generated file in `content/posts/`, then set `draft = false` when ready to publish.

### Front matter used in this blog
```toml
+++
title = "Post Title"
date = 2026-06-23
draft = false
description = "Under ~160 characters — shows up in search results and social previews."
tags = ["AI", "Machine Learning"]
cover:
  image: "/images/your-cover.jpg"
+++
```
Cover images go in `static/images/` and are referenced as `/images/filename.jpg` (no `static/` prefix — Hugo serves `static/` as the site root).

## Deploying to GitHub Pages (Free)

This repo is already wired for it via `.github/workflows/deploy.yml`. One-time setup on GitHub:

1. Push this repo to `https://github.com/Aashishh1/Blogs` (already done if you're reading this from there).
2. On GitHub: **Settings → Pages → Build and deployment → Source → GitHub Actions**.
3. Push to `main` — the workflow builds and deploys automatically.

Your site goes live at:
```
https://aashishh1.github.io/Blogs/
```

No server, no AWS, no recurring bill.

> **Custom domain instead of `github.io`?** GitHub Pages supports free custom domains — add a `CNAME` file in `static/` with your domain, then point your domain's DNS to GitHub. (The domain itself costs money to register; the *hosting* stays free.)

## Updating the Theme
```bash
git submodule update --remote themes/PaperMod
git add themes/PaperMod
git commit -m "Update PaperMod theme"
git push
```

## SEO Checklist
- `baseURL` is set and stable — don't change post URLs after publishing
- Every post has: title, description (<160 chars), tags, cover image
- Hugo auto-generates RSS (`index.xml`) and sitemap (`sitemap.xml`)
- Link related posts to each other
- Link to authoritative external sources (papers, docs) when explaining a tool or concept
