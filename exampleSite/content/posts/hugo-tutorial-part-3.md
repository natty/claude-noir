---
title: "getting started with hugo - part 3"
date: 2024-02-15
tags: ["hugo", "tutorial"]
series:
  - hugo tutorial
---

this is the final part of our hugo tutorial series.

## customizing your site

edit `hugo.toml` to customize your site:

```toml
baseURL = 'https://example.com/'
languageCode = 'en-us'
title = 'my blog'

[params]
  description = 'my personal blog'
  author = 'your name'
```

## building your site

to build your site for production:

```bash
hugo --minify
```

your site will be generated in the `public/` directory.

## deploying

you can deploy your hugo site to:

- github pages
- netlify
- vercel
- cloudflare pages

most of these services can automatically build and deploy your site when you push to your repository.

that's it! you now have a working hugo blog.
