---
title: "getting started with hugo - part 2"
date: 2024-02-08
tags: ["hugo", "tutorial"]
series:
  - hugo tutorial
---

this is the second part of our hugo tutorial series.

## creating a new site

to create a new hugo site, run:

```bash
hugo new site mysite
cd mysite
```

## adding a theme

you can add a theme as a git submodule:

```bash
git submodule add https://github.com/user/theme.git themes/theme
```

then update your `hugo.toml`:

```toml
theme = 'theme'
```

## creating your first post

```bash
hugo new posts/my-first-post.md
```

in the next part, we'll cover customization and deployment.
