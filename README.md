# Developer Profile

A high-performance, responsive developer portfolio and blog built with **Hugo** (hugo-profile theme). It serves as a centralized, static-site-generated hub showcasing professional experience, technical skills, and a diverse portfolio of projects.

## Features

- **Static Site Generator**: Built with Hugo (v0.87.0+) for fast, secure deployments.
- **Data-Driven Content**: Profile, experience, projects, and blog content configured via `hugo.yaml` (YAML) and Markdown files.
- **Theme**: [hugo-profile](https://github.com/gurusabarish/hugo-profile) — Bootstrap-based, mobile-first, with dark mode support.
- **Responsive Design**: Fully responsive layout with animated hero section and glassmorphism aesthetics.
- **Contact Integration**: Direct email CTA and social network links (GitHub, LinkedIn).

## Project Structure

| Path | Purpose |
|------|---------|
| `hugo.yaml` | Primary source of truth — site config, sections, social links, feature toggles |
| `content/` | Markdown-based pages (e.g., `blogs/` for long-form content) |
| `static/` | Static assets — images (`/images/`), icons, favicons |
| `layouts/` | Template overrides — local custom partials overriding the theme |
| `themes/hugo-profile/` | Core theme — **do not modify directly** |
| `data/` | Data files for custom templates |
| `profile-data.json` / `projects.json` | Portable JSON snapshots of profile and project data |

## Getting Started

### Prerequisites

- [Hugo](https://gohugo.io/installation/) — **Extended** version, v0.87.0 or higher
- Git (for pulling the theme submodule)

### Setup

The theme is included as a Git submodule:

```bash
git submodule update --init --recursive
```

### Development

Start the local development server with live reload:

```bash
hugo server
```

To include draft content:

```bash
hugo server -D
```

Production build (outputs to `public/`):

```bash
hugo
```

Clean production build:

```bash
rm -rf public/ && hugo
```

### Common Hugo Commands

| Command | Description |
|---------|-------------|
| `hugo server` | Start dev server at `http://localhost:1313` with live reload |
| `hugo server -D` | Include draft content in dev server |
| `hugo` | Generate static site to `public/` |
| `hugo --minify` | Generate and minify output |
| `hugo --gc` | Generate and run garbage collection on cache |
| `hugo mod graph` | Print Hugo module graph |
| `hugo mod clean` | Clean Hugo module cache |
| `hugo server --disableLiveReload` | Start server without live reload |
| `hugo server --inspect` | Print graph information about Hugo's cache and pages |

### Content Updates

- **Profile sections** (Hero, About, Experience, Education, Projects, Contact): Edit `hugo.yaml` under the `params` block.
- **Blog posts**: Add `.md` files to `content/blogs/` with YAML frontmatter.
- **Project images**: Place in `static/images/projects/` and reference via root-relative paths (`/images/projects/filename`).
- **Site-wide settings** (colors, fonts, navbar, theme): Configured in `hugo.yaml` under `params`.

## Customization

### Theme Overrides

To customize a theme component, copy the file from `themes/hugo-profile/` to `layouts/` while preserving the directory structure. Hugo's lookup order ensures your local version takes precedence.

### Important Rules

- **DO NOT** modify files in `themes/hugo-profile/` directly.
- **DO NOT** use absolute file system paths for assets — always use root-relative paths (`/images/hero.png`).
- **DO** optimize images before adding them to the repo.

## Deploy

The site outputs a fully static `public/` directory that can be deployed to any hosting provider:

- **Netlify**: Connect the repo, set root to `public/`.
- **Vercel**: Add with static site generation preset.
- **GitHub Pages**: Push to `gh-pages` branch or configure GitHub Actions.
- **AWS S3 + CloudFront**: Upload `public/` contents to an S3 bucket configured for static hosting.
- **Local Self-hosting**: Upload `public/` contents via _scp_ as `scp -r .\public\* ubuntu-server:/home/localadmin/hosting-data/static-file-server/public/www`
