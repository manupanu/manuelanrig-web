# Blowfish Configuration Reference

Saved from: https://blowfish.page/docs/configuration/

## Site Config (`hugo.toml`)

| Name | Default | Description |
|------|---------|-------------|
| `theme` | `"blowfish"` | Remove for Hugo Modules, must be `blowfish` otherwise |
| `baseURL` | — | Root URL |
| `defaultContentLanguage` | `"en"` | Must match language config filename |
| `enableRobotsTXT` | `true` | Auto-generate robots.txt |
| `summaryLength` | `0` | Words for auto-summary (0 = first sentence) |
| `outputs.home` | `["HTML","RSS","JSON"]` | Required for search to work |
| `taxonomies` | — | Tags, categories, series, authors |

## Language Config (`languages.en.toml`)

| Name | Default | Description |
|------|---------|-------------|
| `languageCode` | `"en"` | Hugo language code |
| `languageName` | `"English"` | Display name |
| `weight` | `1` | Order for multilingual sites |
| `title` | `"Blowfish"` | Site title |
| `params.displayName` | `"EN"` | Short label |
| `params.isoCode` | `"en"` | ISO code for HTML |
| `params.copyright` | — | Footer copyright, use `{year}` for current year |
| `params.dateFormat` | `"2 January 2006"` | Go date format |
| `params.author.name` | — | Author display name |
| `params.author.image` | — | Path in `assets/` |
| `params.author.headline` | — | Short tagline |
| `params.author.bio` | — | Longer bio |
| `params.author.links` | — | Social links array |

## Theme Parameters (`params.toml`)

### Global

| Name | Default | Description |
|------|---------|-------------|
| `colorScheme` | `"blowfish"` | Theme: blowfish, avocado, fire, forest, ocean, princess, neon, bloody, terminal, marvel, noir, autumn, congo, slate, github, one-light |
| `defaultAppearance` | `"light"` | `light` or `dark` |
| `autoSwitchAppearance` | `true` | Follow OS preference |
| `enableSearch` | `false` | Fuse.js search |
| `enableCodeCopy` | `false` | Copy button on code blocks |
| `mainSections` | — | Sections for recent articles |
| `disableImageOptimization` | `false` | Skip Hugo image processing |
| `defaultBackgroundImage` | — | Default background image |
| `defaultFeaturedImage` | — | Default featured image fallback |
| `defaultSocialImage` | — | Default OG/Twitter image |
| `smartTOC` | — | Highlight active TOC items |
| `fingerprintAlgorithm` | `"sha512"` | Asset fingerprinting |

### Header

| Name | Default | Description |
|------|---------|-------------|
| `header.layout` | `"basic"` | basic, fixed, fixed-fill, fixed-fill-blur |

### Footer

| Name | Default | Description |
|------|---------|-------------|
| `footer.showMenu` | `true` | Show footer menu |
| `footer.showCopyright` | `true` | Show copyright |
| `footer.showThemeAttribution` | `true` | "Powered by Hugo & Blowfish" |
| `footer.showAppearanceSwitcher` | `false` | Light/dark toggle |
| `footer.showScrollToTop` | `true` | Back-to-top arrow |

### Homepage

| Name | Default | Description |
|------|---------|-------------|
| `homepage.layout` | `"profile"` | profile, page, hero, card, background, custom |
| `homepage.homepageImage` | — | Image for hero/card layouts |
| `homepage.showRecent` | `false` | Show recent articles |
| `homepage.showRecentItems` | `5` | How many to show |
| `homepage.showMoreLink` | `false` | Show "more" link |
| `homepage.cardView` | `false` | Cards vs list view |
| `homepage.layoutBackgroundBlur` | `false` | Blur background on scroll |

### Article

| Name | Default | Description |
|------|---------|-------------|
| `article.showDate` | `true` | Publication date |
| `article.showDateUpdated` | `false` | Last modified date |
| `article.showAuthor` | `true` | Author box |
| `article.showHero` | `false` | Hero image |
| `article.heroStyle` | — | basic, big, background, thumbAndBackground |
| `article.showBreadcrumbs` | `false` | Breadcrumb trail |
| `article.showDraftLabel` | `true` | "Draft" indicator |
| `article.showEdit` | `false` | Edit link |
| `article.showHeadingAnchors` | `true` | Anchor links on headings |
| `article.showPagination` | `true` | Next/previous article |
| `article.showReadingTime` | `true` | Estimated read time |
| `article.showTableOfContents` | `false` | In-page TOC |
| `article.showRelatedContent` | `false` | Related articles (requires `related` in hugo.toml) |
| `article.showTaxonomies` | `false` | Tags/categories display |
| `article.showWordCount` | `false` | Word count |
| `article.showZenMode` | `false` | Reading mode toggle |
| `article.sharingLinks` | — | Social share buttons: bluesky, email, facebook, line, linkedin, mastodon, pinterest, reddit, telegram, twitter, whatsapp |
| `article.externalLinkForceNewTab` | `true` | External links open in new tab |

### List

| Name | Default | Description |
|------|---------|-------------|
| `list.showHero` | `false` | Hero on list pages |
| `list.showBreadcrumbs` | `false` | Breadcrumbs |
| `list.showSummary` | `false` | Article summaries |
| `list.showCards` | `false` | Card layout |
| `list.groupByYear` | `true` | Group by year |
| `list.orderByWeight` | `false` | Sort by front matter weight |
| `list.cardView` | `false` | Gallery card view |
| `list.constrainItemsWidth` | `false` | Limit width for readability |

### Taxonomy / Term

| Name | Default | Description |
|------|---------|-------------|
| `taxonomy.showTermCount` | `true` | Count by each term |
| `taxonomy.showHero` | `false` | Hero on taxonomy pages |
| `taxonomy.cardView` | `false` | Card gallery view |
| `term.showHero` | `false` | Hero on term pages |
| `term.groupByYear` | `false` | Group by year |
| `term.cardView` | `false` | Card gallery view |

## Homepage Layouts

1. **profile** — Author avatar, bio, social links. Content from `content/_index.md` appears below.
2. **page** — Standard content page. Full Markdown content from `_index.md`.
3. **hero** — Large hero image + author info + content below.
4. **card** — Card image + content from `_index.md`.
5. **background** — Full-width background image with content overlaid.
6. **custom** — Requires `layouts/partials/home/custom.html`. Complete freedom.

## Colour Schemes

```
blowfish (default, blue/purple), avocado (green), fire (red/orange),
forest (green/earth), ocean (blue), princess (pink), neon (bright),
bloody (dark red), terminal (green on black), marvel (red/blue),
noir (black/white), autumn (orange/brown), congo (teal),
slate (cool gray), github (GitHub-style), one-light (Atom One Light)
```
