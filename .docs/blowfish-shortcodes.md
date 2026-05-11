# Blowfish Shortcodes Quick Reference

Saved from: https://blowfish.page/docs/shortcodes/

## Alert / Callout
```
{{< alert >}}
**Warning!** This action is destructive!
{{< /alert >}}

{{< alert "twitter" >}}
Don't forget to [follow me](https://twitter.com/nunocoracao).
{{< /alert >}}

{{< alert icon="fire" cardColor="#e63946" iconColor="#1d3557" textColor="#f1faee" >}}
This is an error!
{{< /alert >}}
```
Parameters: `icon` (default: triangle-exclamation), `iconColor`, `cardColor`, `textColor`

## Admonition (Markdown-native)
```markdown
> [!TIP]
> A helpful tip.

> [!WARNING]+ Collapsible Warning
> This folds by default.

> [!NOTE] Custom Title
> Custom title with icon.
{icon="twitter"}
```
Types: NOTE, TIP, IMPORTANT, WARNING, CAUTION, note, abstract, info, todo, tip, success, question, warning, failure, danger, bug, example, quote

## Accordion
```
{{< accordion mode="open" separated=true >}}
  {{< accordionItem title="Section 1" icon="code" open=true >}}
    Content here (renders as Markdown by default).
  {{< /accordionItem >}}
  {{< accordionItem title="Section 2" md=false >}}
    Use md=false for nested shortcodes.
    {{< alert >}}Inline alert!{{< /alert >}}
  {{< /accordionItem >}}
{{< /accordion >}}
```
Parameters: `mode` (collapse/open), `separated` (true/false)
Item params: `title`, `open`, `icon`, `md`

## Badge
```
{{< badge >}}New article!{{< /badge >}}
```

## Button
```
{{< button href="#button" target="_self" >}}Call to action{{< /button >}}
```

## Carousel
```
{{< carousel images="gallery/*" aspectRatio="21-9" interval="2500" >}}
{{< carousel images="gallery/*" captions="{01.jpg:First *caption*,02.jpg:Second [link](https://example.com)}" >}}
```

## Chart
```
{{< chart >}}
type: 'bar',
data: {
  labels: ['A', 'B', 'C'],
  datasets: [{ label: '# of votes', data: [12, 19, 3] }]
}
{{< /chart >}}
```

## Code Importer
```
{{< codeimporter url="https://raw.githubusercontent.com/.../file.go" type="go" startLine="11" endLine="18" >}}
```

## Email (obfuscated)
```
{{< email email="mailto:hello@test.com" text="Email me" subject="Reply to post" >}}
```

## Figure
```
{{< figure
  src="photo.jpg"
  alt="Description"
  caption="Photo by [Author](https://example.com)"
  class="rounded-lg w-full"
  href="https://example.com"
  target="_blank"
  nozoom=true
  figureClass="grid-w50"
>}}
```
Lookup order: page resource → assets/ → static/

## Gallery
```
{{< gallery >}}
  <img src="01.jpg" class="grid-w33" />
  <img src="02.jpg" class="grid-w33" />
  <img src="03.jpg" class="grid-w33" />
  <!-- Responsive: -->
  <img src="04.jpg" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}

<!-- With captions via figure: -->
{{< gallery >}}
  {{< figure src="01.jpg" caption="Caption" figureClass="grid-w50" >}}
  {{< figure src="02.jpg" caption="Caption 2" figureClass="grid-w50" >}}
{{< /gallery >}}
```

## Gist
```
{{< gist "octocat" "6cad326836d38bd3a7ae" >}}
{{< gist "username" "gistID" "filename.md" >}}
```

## GitHub / GitLab / Gitea / Codeberg / Forgejo Cards
```
{{< github repo="nunocoracao/blowfish" showThumbnail=true >}}
{{< gitlab projectID="278964" >}}
{{< gitea server="https://git.fsfe.org" repo="FSFE/fsfe-website" >}}
{{< codeberg repo="forgejo/forgejo" >}}
{{< forgejo server="https://v11.next.forgejo.org" repo="a/mastodon" >}}
```

## Hugging Face Card
```
{{< huggingface model="google-bert/bert-base-uncased" >}}
{{< huggingface dataset="stanfordnlp/imdb" >}}
```

## Icon
```
{{< icon "github" >}}
```
Built-in icons include social platforms and UI elements. Custom icons: add SVGs to `assets/icons/`, reference by filename without `.svg`.

## KaTeX
```
{{< katex >}}
  Inline: \(f(x) = x^2\)
  Block: $$f(x) = x^2$$
{{< /katex >}}
```

## Keyword / KeywordList
```
{{< keyword >}}*Super* skill{{< /keyword >}}

{{< keywordList >}}
  {{< keyword icon="github" >}}Git proficiency{{< /keyword >}}
  {{< keyword icon="code" >}}**Expert** coding{{< /keyword >}}
{{< /keywordList >}}
```

## Lead (intro paragraph)
```
{{< lead >}}
When life gives you lemons, make lemonade.
{{< /lead >}}
```

## List (recent articles)
```
{{< list limit=2 >}}
{{< list title="Samples" cardView=true limit=6 where="Type" value="sample" >}}
```

## LTR / RTL
```
{{% rtl %}}هذه القائمة باللغة العربية{{% /rtl %}}
```

## Markdown Importer
```
{{< mdimporter url="https://raw.githubusercontent.com/.../README.md" >}}
```

## Mermaid
```
{{< mermaid >}}
graph LR;
A[Lemons]-->B[Lemonade];
B-->C[Profit]
{{< /mermaid >}}
```

## Swatches (color palette)
```
{{< swatches "#64748b" "#3b82f6" "#06b6d4" >}}
```

## Tabs
```
{{< tabs group="lang" default="Python" >}}
  {{< tab label="JavaScript" icon="code" >}}
  ```javascript
  console.log("Hello");
  ```
  {{< /tab >}}
  {{< tab label="Python" icon="sun" >}}
  ```python
  print("Hello")
  ```
  {{< /tab >}}
  {{< tab label="Go" icon="moon" md=false >}}
    {{< alert >}}Nested shortcodes need md=false{{< /alert >}}
  {{< /tab >}}
{{< /tabs >}}
```
Params: `group` (sync tabs across groups), `default` (active tab), `label`, `icon`, `md`

## Timeline
```
{{< timeline >}}
  {{< timelineItem icon="github" header="2024" badge="new" subheader="Role" >}}
    Description text with **Markdown**.
  {{< /timelineItem >}}
  {{< timelineItem icon="code" header="2023" badge="date - present" >}}
    Can include other shortcodes:
    {{< github repo="nunocoracao/blowfish" >}}
  {{< /timelineItem >}}
{{< /timeline >}}
```
Item params: `icon`, `header`, `badge`, `subheader`

## TypeIt (typewriter effect)
```
{{< typeit tag="h1" lifeLike=true speed=50 breakLines=false loop=true >}}
First string.
Second string.
Third string.
{{< /typeit >}}
```

## Video
```
{{< video
  src="video.mp4"
  poster="thumb.jpg"
  caption="**Caption** with markdown"
  autoplay=true loop=true muted=true
  start=10 end=30
  ratio="16/9"
  fit="contain"
>}}
```
Params: `src`, `poster`, `caption`, `autoplay`, `loop`, `muted`, `controls` (default: true), `playsinline`, `preload` (metadata/auto/none), `start`, `end`, `ratio` (16/9, 4/3, 1/1, W/H), `fit` (contain/cover/fill)

## YouTube Lite
```
{{< youtubeLite id="SgXhGb-7QbU" label="Blowfish demo" >}}
{{< youtubeLite id="SgXhGb-7QbU" label="Demo" params="start=130&end=10&controls=0" >}}
```
