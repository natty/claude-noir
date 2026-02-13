# claude noir

a minimal, dark-themed hugo blog theme focused on clean typography, fast load times, and simplicity. no javascript required.

## features

- clean, minimal design
- dark theme
- no javascript
- fast load times
- seo-friendly meta tags
- responsive layout
- syntax highlighting for code blocks
- multiple post list styles (flat, grouped by year, grouped by month)
- tag support
- series support (group related posts)
- reading time and word count
- social icons (20 platforms)
- draft indicators

## installation

1. add this theme to your hugo site's `themes` directory as a git submodule:
   ```bash
   cd your-hugo-site
   git submodule add https://github.com/yourusername/claude-noir.git themes/claude-noir
   ```

2. update your `hugo.toml` to use the theme:
   ```toml
   theme = 'claude-noir'
   ```

to update the theme later:
```bash
git submodule update --remote themes/claude-noir
```

## configuration

### basic configuration

add these to your `hugo.toml`:

```toml
baseURL = 'https://example.com/'
languageCode = 'en-us'
title = 'your site title'
theme = 'claude-noir'

# copyright notice in footer (optional)
copyright = 'copyright © 2024 your name'

# pagination settings
[pagination]
  pagerSize = 6

[params]
  # site description for seo
  description = 'a minimal blog about things'
  
  # author name for meta tags
  author = 'your name'
```

### post previews

post previews on the homepage and tag pages are truncated to 500 characters. this is hardcoded in the theme for simplicity and consistency.

### theme parameters

all theme parameters are optional and go under `[params]` in your `hugo.toml`:

```toml
[params]
  # prefix shown before post titles (optional)
  postTitlePrefix = '>'
  
  # site logo image displayed next to site title (optional)
  siteImage = 'images/avatar.png'
  
  # style for all posts page (default: flat)
  # flat: YYYY-MM-DD post title
  # groupedByYear: posts grouped under year headings
  # groupedByMonth: posts grouped under year and month headings
  postsListStyle = 'flat'
  
  # show calendar and tag icons in post meta (default: false)
  showMetaIcons = true
  
  # show reading time and word count (default: false)
  showPostStats = true
  
  # show theme credit in footer (default: false)
  showHugoThemeCredit = true
  
  # enable favicon link tags (default: false)
  faviconEnabled = true
  
  # social icons position in footer (default: right)
  # options: left, right, above, below
  socialPosition = 'right'
  
  # series box position on posts (default: top)
  # options: top, bottom
  seriesPosition = 'top'
```

### social icons

add social media links to your footer with `[[params.social]]` in your `hugo.toml`:

```toml
[[params.social]]
  name = 'github'
  url = 'https://github.com/yourusername'
[[params.social]]
  name = 'bluesky'
  url = 'https://bsky.app/profile/yourusername'
[[params.social]]
  name = 'rss'
  url = '/index.xml'
```

**supported icons:** github, gitlab, codeberg, bluesky, mastodon, threads, instagram, facebook, linkedin, youtube, twitch, discord, reddit, goodreads, steam, buymeacoffee, kofi, patreon, email, rss

**position options:**
- `left`: icons | copyright
- `right` (default): copyright | icons
- `above`: icons on top row, copyright below
- `below`: copyright on top row, icons below

### navigation menu

add menu items to your `hugo.toml`:

```toml
[menus]
  [[menus.main]]
    name = 'posts'
    url = '/posts/'
    weight = 1
  [[menus.main]]
    name = 'tags'
    url = '/tags/'
    weight = 2
  [[menus.main]]
    name = 'about'
    url = '/about/'
    weight = 3
```

## content structure

### posts

create posts in `content/posts/`:

```
content/
└── posts/
    ├── my-first-post.md
    └── another-post.md
```

### post front matter

```yaml
---
title: 'my post title'
date: 2024-01-15
draft: false
tags: ['hugo', 'tutorial']
description: 'optional description for seo'
series: ['my series name']
---

your post content here...
```

### series

to group related posts into a series, add the same series name to each post's front matter:

```yaml
series: ['learning hugo']
```

posts in a series display a navigation box showing all posts in the series with prev/next indicators.

### pages (non-posts)

create standalone pages in `content/` with `type: "page"` in front matter:

```
content/
├── about.md
├── contact.md
└── posts/
    └── ...
```

page front matter:

```yaml
---
title: 'about'
type: 'page'
lastmod: 2024-01-15
---
```

pages with `type: "page"` use a simpler template with no date, tags, or prev/next navigation. the `lastmod` field is optional and displays "last updated" at the bottom of the page.

### tag descriptions

to add a description to a tag page, create a file at `content/tags/tagname/_index.md`:

```yaml
---
title: 'hugo'
---

posts about the hugo static site generator.
```

## customization

### colors

edit the css variables at the top of `static/css/style.css`:

```css
:root {
    --color-background: #252d33;
    --color-text: #C0C0C6;
    --color-link: #C0C0C6;
    --color-link-hover-bg: #384955;
    --color-text-muted: #787881;
    --color-tag: #6A7781;
    --color-prefix: #71899B;
}
```

### typography

the theme uses system serif fonts by default:

```css
:root {
    --font-family: ui-serif, Georgia, Cambria, 'Times New Roman', Times, serif;
    --font-size-base: 14px;
    --font-size-title: 18px;
}
```

#### using a custom font

1. place your font file in `static/fonts/`
2. create `static/css/custom.css`:
   ```css
   @font-face {
       font-family: 'YourFont';
       src: url('/fonts/YourFont.woff2') format('woff2');
       font-display: swap;
   }
   
   :root {
       --font-family: 'YourFont', sans-serif;
   }
   ```
3. create `layouts/partials/head.html` that includes your custom.css after the theme's style.css

### syntax highlighting

configure hugo's syntax highlighting in `hugo.toml`:

```toml
[markup]
  [markup.highlight]
    style = 'solarized-dark256'
```

### favicons

to enable favicon support:

```toml
[params]
  faviconEnabled = true
```

then place your favicon files in your site's `static/` folder:

```
static/
├── favicon.ico
├── favicon.svg
├── favicon-96x96.png
└── apple-touch-icon.png
```

## license

MIT
