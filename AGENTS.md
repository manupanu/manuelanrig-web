# AGENTS.md

Instructions for working on this project — the personal website of Manuel Anrig.

## Project Overview

- **Live site:** [manuelanrig.ch](https://manuelanrig.ch/)
- **Stack:** Hugo (extended) 0.161.1+ with the [Blowfish](https://blowfish.page/) theme
- **Deployment:** Cloudflare Pages — auto-build on push to `main` branch
- **Domain:** manuelanrig.ch
- **Appearance:** Dark only, Forest colour scheme, profile homepage layout
- **Language:** English only (`content/en/`)

## Commands

```bash
# Dev server (drafts visible, auto-reload at http://localhost:1313)
hugo server --buildDrafts

# Production build → public/
hugo --minify

# New blog post
hugo new content blog/<slug>.md

# New section
hugo new content <section>/_index.md
```

## Directory Structure

```
.
├── config/_default/
│   ├── hugo.toml              # Site-level settings (baseURL, taxonomies, pagination, related)
│   ├── params.toml            # Blowfish theme parameters (colors, layouts, toggles)
│   ├── menus.en.toml          # Main nav: Blog, Racing, Resume
│   ├── markup.toml            # Goldmark, highlight, KaTeX delimiters
│   └── languages.en.toml      # Language/i18n + author info (name, bio, social links)
├── content/en/                # All English content
│   ├── _index.md              # Homepage — profile layout, intro bio
│   ├── blog/
│   │   ├── _index.md          # Blog section index (cascade: showDate, showAuthor, etc.)
│   │   ├── tech-project-training-dashboard.md
│   │   ├── bike-build-wheelset.md
│   │   └── my-first-race-report.md
│   ├── racing/_index.md       # Racing results table + 2026 ambitions
│   └── resume/_index.md       # Placeholder ("Coming soon")
├── assets/img/avatar.png      # Author avatar (referenced in languages.en.toml)
├── static/
│   ├── img/                   # Static images (racing photos etc.)
│   │   ├── revelstoke.jpeg
│   │   └── verbier-ebike.jpeg
│   ├── _headers               # Cloudflare security + caching headers
│   └── _redirects             # Cloudflare redirect rules
├── archetypes/default.md      # Template for new content
├── themes/blowfish/           # Blowfish theme (tracked directly — NOT a submodule)
├── cloudflare.toml            # Build config: Hugo 0.161.1, command: hugo --minify → public/
└── README.md
```

## Adding & Editing Content

### Creating a new article

```bash
hugo new content blog/<slug>.md
```

The archetype generates:

```yaml
---
date: '2026-XX-XX'
draft: true
title: 'Your Title Here'
tags: ["add", "tags", "here"]
description: 'Brief description for SEO and cards'
---
```

Set `draft: false` when ready to publish (drafts excluded from production build).

### Content conventions (from existing articles)

- **Tone:** Casual, first-person, by Manuel Anrig
- **Topics:** Bike builds, race reports, tech side projects
- **Image shortcode:** `{{< figure src="/img/filename.jpg" alt="..." caption="..." class="rounded-lg w-full" >}}`
- **Tables:** Standard Markdown tables (see racing page for formatting)

### Existing tags

`tech`, `projects`, `go`, `bike-build`, `wheels`, `racing`, `road`

Tags drive the taxonomy pages at `/tags/<tag>/`.

## Blowfish Features in Use

### Current config highlights (params.toml)

| Setting | Value | Notes |
|---------|-------|-------|
| `colorScheme` | `forest` | Also available: blowfish, avocado, fire, ocean, princess, neon, bloody, terminal, marvel, noir, autumn, congo, slate, github, one-light |
| `defaultAppearance` | `dark` | No light mode switcher |
| `homepage.layout` | `profile` | Author avatar + bio from `languages.en.toml` |
| `homepage.showRecent` | `false` | No recent articles on homepage |
| `article.showHero` | `true` | Full-width hero images on articles |
| `article.heroStyle` | `background` | Uses `background*` named images from page bundle |
| `article.showRelatedContent` | `true` | Related articles at bottom of posts |
| `enableCodeCopy` | `true` | Copy button on code blocks |
| `enableSearch` | `true` | Site search via Fuse.js |
| `article.sharingLinks` | 10 services | LinkedIn, Twitter, Bluesky, Reddit, WhatsApp, Telegram, Pinterest, Facebook, Email, Line |

### Available Blowfish shortcodes

| Shortcode | Purpose | Example |
|-----------|---------|---------|
| `figure` | Optimised images with zoom | `{{< figure src="/img/photo.jpg" alt="..." caption="..." >}}` |
| `alert` | Callout boxes | `{{< alert "twitter" >}}**Note:** Something important{{< /alert >}}` |
| `badge` | Styled badges | `{{< badge >}}New!{{< /badge >}}` |
| `button` | CTA links | `{{< button href="/blog/" >}}Read more{{< /button >}}` |
| `video` | Local/external video player | `{{< video src="video.mp4" poster="thumb.jpg" >}}` |
| `youtubeLite` | Lightweight YouTube embed | `{{< youtubeLite id="videoID" label="Title" >}}` |
| `gallery` | Responsive image grid | `{{< gallery >}}<img src="01.jpg" class="grid-w33" />{{< /gallery >}}` |
| `carousel` | Image slideshow | `{{< carousel images="gallery/*" >}}` |
| `tabs` / `tab` | Tabbed content | `{{< tabs >}}{{< tab label="One" >}}...{{< /tab >}}{{< /tabs >}}` |
| `accordion` / `accordionItem` | Collapsible sections | `{{< accordion >}}{{< accordionItem title="..." >}}...{{< /accordionItem >}}{{< /accordion >}}` |
| `timeline` / `timelineItem` | Visual timeline | `{{< timeline >}}{{< timelineItem icon="code" header="..." >}}...{{< /timelineItem >}}{{< /timeline >}}` |
| `chart` | Chart.js diagrams | `{{< chart >}}type: 'bar', data: {...}{{< /chart >}}` |
| `mermaid` | Mermaid diagrams | `{{< mermaid >}}graph LR; A-->B;{{< /mermaid >}}` |
| `katex` | Math typesetting | `{{< katex >}}\(E=mc^2\){{< /katex >}}` |
| `lead` | Styled intro paragraph | `{{< lead >}}Opening statement...{{< /lead >}}` |
| `keyword` / `keywordList` | Highlighted skill keywords | `{{< keyword icon="code" >}}**Skill**{{< /keyword >}}` |
| `icon` | Inline SVG icon | `{{< icon "github" >}}` |
| `github` / `gitlab` / `gitea` / `codeberg` / `forgejo` | Repo cards | `{{< github repo="owner/repo" >}}` |
| `typeit` | Typewriter text effect | `{{< typeit >}}Text to type...{{< /typeit >}}` |
| `ltr` / `rtl` | Directional text blocks | `{{% rtl %}}Arabic text{{% /rtl %}}` |
| `codeimporter` | Import code from URL | `{{< codeimporter url="..." type="go" >}}` |
| `mdimporter` | Import Markdown from URL | `{{< mdimporter url="..." >}}` |

### Admonitions (Markdown-native callouts)

Blowfish supports Obsidian/GitHub-style admonitions using blockquote syntax:

```markdown
> [!TIP]
> A helpful tip.

> [!WARNING]+ Collapsible Warning
> This folds by default.

> [!NOTE] Custom Title
> A note with a custom title.
{icon="twitter"}
```

Supported types: `NOTE`, `TIP`, `IMPORTANT`, `WARNING`, `CAUTION`, `note`, `abstract`, `info`, `todo`, `tip`, `success`, `question`, `warning`, `failure`, `danger`, `bug`, `example`, `quote`.

### Image handling

- **Local images in `static/img/`:** Reference as `/img/filename.jpg`
- **Page bundles:** Put `index.md` + images in a subdirectory (e.g. `content/en/blog/my-post/index.md` + `feature.jpg`). Blowfish auto-detects `feature*` for thumbnails and `background*` for hero backgrounds.
- **Markdown images:** `![Alt](image.jpg "Caption")` — Blowfish auto-converts these to optimised figures
- **Author avatar:** `assets/img/avatar.png` (1:1 ratio, referenced in `languages.en.toml`)
- **Zoom:** Enabled by default on figures. Add `nozoom=true` to disable.
- **The `figure` shortcode** auto-resizes page resource images to 800w/1280w with srcset.

### Key Blowfish front matter fields

| Field | Description |
|-------|-------------|
| `title` | Article title |
| `description` | SEO description / card text |
| `date` | Publication date |
| `draft` | `true` = hidden from production builds |
| `tags` | Array of tags (e.g. `["racing", "road"]`) |
| `externalUrl` | Makes this an external link card (no page generated) |
| `showDate`, `showAuthor`, `showReadingTime`, `showTableOfContents` | Per-article display toggles |
| `showHero` | Show/hide hero image on article |
| `heroStyle` | `basic`, `big`, `background`, `thumbAndBackground` |
| `layout` | Set to `"simple"` for full-width minimalist pages |
| `series` / `series_order` | Group related articles |
| `summary` | Override auto-generated summary |
| `cascade` | On `_index.md` — set defaults for all child pages |

### Menus

Configured in `config/_default/menus.en.toml`. Current structure:

- **Blog** → `/blog/` (weight 10)
- **Racing** → `/racing/` (weight 20)
- **Resume** → `/resume/` (weight 30)

Menu entries support: `name`, `url` / `pageRef`, `weight`, `pre` (icon name), `parent` (for nested dropdowns). The footer menu is configured here as well.

### KaTeX / Math

KaTeX is pre-configured. Inline: `\(formula\)`. Block: `\[formula\]` or `$$formula$$`. Insert `{{< katex >}}` once per page to load the library.

## Hugo Conventions

### Page types

| Type | File | URL |
|------|------|-----|
| Section index | `_index.md` | `/blog/`, `/racing/`, etc. |
| Leaf (single) page | `<name>.md` | `/blog/post-slug/` |
| Page bundle (with images) | `<name>/index.md` | `/blog/post-slug/` |
| External link | Uses `externalUrl` front matter | Links off-site |

### Drafts

- Draft posts (`draft: true`) are hidden from `hugo --minify` builds
- Visible locally with `hugo server --buildDrafts`

## Deployment

Every push to `main` triggers Cloudflare Pages:
- **Build command:** `hugo --minify`
- **Output:** `public/`
- **Hugo version:** 0.161.1 (set in `cloudflare.toml`)
- **Headers:** Security headers + 1-year caching on static assets (CSS, JS, images, fonts)
- **Redirects:** Minimal — root serves the site directly

## Git Workflow

- **Branch:** `main`
- No pull request workflow, no CI beyond Cloudflare auto-deploy
- The Blowfish theme is tracked directly (not a submodule) — update manually by pulling from upstream
- Commits are descriptive: e.g. "Restructure site: blog, racing, resume sections"

## Common Tasks

### Add a new blog post
```bash
hugo new content blog/<slug>.md
# Edit file → set draft: false when ready → git commit → git push
```

### Add a new top-level section
```bash
hugo new content <section>/_index.md
# Add to config/_default/menus.en.toml
```

### Update racing results
Edit `content/en/racing/_index.md` — update the Markdown table and ambition text.

### Change colour scheme
Edit `config/_default/params.toml` → `colorScheme = "neon"` (see full list above).

### Add author social links
Edit `config/_default/languages.en.toml` → `[Author] links` array. Icon SVGs in `assets/icons/`.

### Switch homepage layout
Edit `config/_default/params.toml` → `[homepage] layout`. Options: `profile`, `page`, `hero`, `card`, `background`, `custom`.

### Enable recent articles on homepage
Set `homepage.showRecent = true` and `homepage.showRecentItems = N` in `params.toml`. Ensure `mainSections = ["blog"]` is set.
