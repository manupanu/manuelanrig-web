# manuelanrig.ch

Personal website built with [Hugo](https://gohugo.io/) and the [Blowfish](https://blowfish.page/) theme, deployed on [Cloudflare Pages](https://pages.cloudflare.com/).

## Tech Stack

- **Static Site Generator:** Hugo (extended version)
- **Theme:** Blowfish (v2)
- **Hosting:** Cloudflare Pages
- **Domain:** manuelanrig.ch

## Local Development

### Prerequisites

- [Hugo extended](https://gohugo.io/installation/) v0.161.1 or later

### Commands

```bash
# Start dev server with draft content visible
hugo server --buildDrafts

# Build site for production
hugo --minify

# Build the site for preview (output in public/)
hugo
```

The dev server runs at `http://localhost:1313/` by default and auto-reloads on changes.

## Project Structure

```
.
├── config/
│   └── _default/           # Hugo configuration files
│       ├── hugo.toml        # Site settings
│       ├── params.toml      # Blowfish theme parameters
│       ├── markup.toml      # Markdown rendering settings
│       ├── menus.en.toml    # Navigation menu
│       └── languages.en.toml # Language/i18n config
├── content/
│   └── en/                  # English content
│       ├── _index.md        # Homepage
│       └── docs/            # Documentation/articles section
├── static/
│   ├── _headers             # Cloudflare security & caching headers
│   └── _redirects           # Cloudflare redirect rules
├── themes/
│   └── blowfish/            # Blowfish theme (tracked directly)
├── cloudflare.toml          # Cloudflare Pages build configuration
└── README.md
```

## Adding Content

```bash
# Create a new page in the docs section
hugo new content docs/my-new-article.md

# Create a new section
hugo new content projects/_index.md
```

## Deployment

The site is deployed on Cloudflare Pages. Every push to the `main` branch triggers an automatic build and deployment.

### Build Settings

- **Build command:** `hugo --minify`
- **Output directory:** `public`
- **Hugo version:** 0.161.1

These are configured in `cloudflare.toml` and are automatically detected by Cloudflare Pages.

## Domain

The site is hosted at [manuelanrig.ch](https://manuelanrig.ch/).

## License

The content of this project is proprietary. The Blowfish theme is MIT licensed (see `themes/blowfish/LICENSE`).
