Personal blog by **Ashish Mishra**, AI Engineer — covering AI, Machine Learning, Data Science, MLOps, and Generative AI. Built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme. Deployed **free** on GitHub Pages.

Live at: **https://aashishh1.github.io/Blogs/**

## Tech Stack

- Hugo static site generator
- PaperMod Hugo theme (Git submodule)
- Markdown content in `content/`
- Custom CSS overrides in `assets/css/extended/custom.css` (heading sizes, image styling)
- Free hosting via **GitHub Pages** + GitHub Actions (no AWS, no Netlify, no recurring cost)

## Repository Layout

```
.
├── archetypes/                  # Template for new posts
├── assets/css/extended/
│   └── custom.css               # Heading sizes, image styling overrides
├── content/
│   ├── posts/                   # Blog posts
│   └── about.md                 # About page
├── static/images/                # Cover images and in-post diagrams
├── themes/PaperMod/              # Theme submodule
├── .github/workflows/deploy.yml  # Auto build + deploy on push
├── hugo.toml                     # Site configuration
└── README.md
```

## One-Time Setup (Local Machine)

### 1. Install Hugo Extended

- **Windows**: `winget install Hugo.Hugo.Extended` (open a new terminal afterward so PATH refreshes)
- **macOS**: `brew install hugo`
- **Linux**: download the extended binary from [Hugo Releases](https://github.com/gohugoio/hugo/releases) — the default `apt` package is often not "extended"
  Verify:

```bash
hugo version
```

The output must include the word `extended`.

### 2. Get the theme submodule

If this is a fresh clone of the GitHub repo:

```bash
git clone --recurse-submodules https://github.com/Aashishh1/Blogs.git
cd Blogs
```

If you already have the folder but `themes/PaperMod` is empty:

```bash
git submodule add https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
git submodule update --init --recursive
```

### 3. Preview locally

```bash
hugo server -D
```

Open **http://localhost:1313/Blogs/** — note the `/Blogs/` path, it must match the `baseURL` in `hugo.toml`. The `-D` flag also shows draft posts and future-dated posts while developing.

## Writing New Posts

```bash
hugo new posts/my-new-post-slug.md
```

Edit the generated file in `content/posts/`, then set `draft = false` when ready to publish.

### Front matter format used in this blog

```yaml
---
title: "Post Title"
date: 2026-06-23
draft: false
description: "Under ~160 characters — shows up in search results and social previews."
tags: ["AI", "Machine Learning"]
cover:
  image: "images/your-cover.jpg"
  alt: "Short description of the cover image"
---
```

Cover and in-post images live in `static/images/` and are referenced as `images/filename.jpg` — **never** with a `static/` prefix in the markdown, since Hugo serves the `static/` folder as the site root and the site is deployed under `/Blogs/`.

> **Heads up on dates:** Hugo hides posts whose `date` is in the future relative to your system clock (`buildFuture = false` by default). If a post you just wrote isn't showing up on the homepage, check whether its date is set later than today — either change the date or run `hugo server -D -F` to preview future posts too.

## Styling

Heading sizes, image width/rounding, and spacing are controlled in `assets/css/extended/custom.css`. This file is picked up automatically by PaperMod — no theme files were modified directly, so theme updates won't overwrite your styling.

## Deploying to GitHub Pages (Free)

Already wired up via `.github/workflows/deploy.yml`. One-time setup on GitHub:

1. Push this repo to `https://github.com/Aashishh1/Blogs`.
2. On GitHub: **Settings → Pages → Build and deployment → Source → GitHub Actions**.
3. Push to `main` — the workflow builds and deploys automatically on every push.
   Your site goes live at:

```
https://aashishh1.github.io/Blogs/
```

No server, no AWS, no recurring bill.

> **Custom domain instead of `github.io`?** GitHub Pages supports free custom domains — add a `CNAME` file in `static/` containing your domain, then point your domain's DNS to GitHub. (Registering the domain itself costs money; the _hosting_ stays free.)

## Updating the Theme

```bash
git submodule update --remote themes/PaperMod
git add themes/PaperMod
git commit -m "Update PaperMod theme"
git push
```

## SEO Checklist

- `baseURL` is set and stable — don't change post URLs after publishing
- Every post has: title, description (under 160 characters), tags, cover image with alt text
- Hugo auto-generates RSS (`index.xml`) and sitemap (`sitemap.xml`) — nothing extra needed
- Link related posts to each other where relevant
- Link to authoritative external sources (papers, official docs) when explaining a tool or concept
