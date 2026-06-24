# Agent Guide — Ashish Mishra AI Engineer Blog

Hugo static site using the PaperMod theme, deployed free via GitHub Pages + GitHub Actions, at https://aashishh1.github.io/Blogs/

## Rules
- Never hand-edit `public/` — it's generated output (gitignored). Edit `content/`, `layouts/`, `static/`, or `hugo.toml`, then rebuild.
- `themes/PaperMod` is a Git submodule — don't edit files inside it directly. Use `layouts/` overrides instead.
- Keep `baseURL` in `hugo.toml` (`https://aashishh1.github.io/Blogs/`) stable once posts are published; don't change post slugs/URLs after publishing.
- Cover images and inline images live in `static/images/` and are referenced as `/images/filename.jpg` — never with a `static/` prefix in markdown.
- Every post needs front matter: `title`, `date`, `draft`, `description` (<160 chars), `tags`, `cover.image`.
- Deployment is via `.github/workflows/deploy.yml`, triggered on push to `main`. Don't introduce a paid hosting step — the goal is zero recurring cost.

## Common Tasks
- **New post**: `hugo new posts/slug-name.md`, edit in `content/posts/`, set `draft = false` to publish.
- **Local preview**: `hugo server -D` → http://localhost:1313/Blogs/
- **Production build (manual check)**: `hugo --gc --minify`
- **Theme update**: `git submodule update --remote themes/PaperMod`

## Identity / Consistency
Author: Ashish Mishra. Social links: GitHub `aashishh1`, LinkedIn `aashishh1`, X `imAMishra1`. Keep these consistent across `hugo.toml` and `content/about.md` — update both together if any one changes.
