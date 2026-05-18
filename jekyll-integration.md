````markdown
# Integrating Jekyll into Your GitHub Pages Resume Site

## Goal

Turn your existing GitHub Pages resume repository into:

- Resume website
- Project showcase
- Technical blog/articles
- Central portfolio hub

---

# Recommended Structure

```text
yourusername.github.io
│
├── _posts/          # Blog articles
├── projects/        # Project pages
├── assets/          # Images, CSS, JS
├── _layouts/
├── _includes/
├── index.md         # Homepage / Resume
├── blog.md
├── projects.md
├── about.md
├── _config.yml
└── Gemfile
````

---

# Step 1 — Install Ruby

Jekyll requires Ruby.

## Windows

Download:
[https://rubyinstaller.org/](https://rubyinstaller.org/)

## macOS/Linux

[https://www.ruby-lang.org/en/downloads/](https://www.ruby-lang.org/en/downloads/)

Verify installation:

```bash
ruby -v
```

---

# Step 2 — Install Jekyll and Bundler

```bash
gem install bundler jekyll
```

Verify:

```bash
jekyll -v
```

---

# Step 3 — Clone Your Existing GitHub Pages Repository

Example:

```bash
git clone https://github.com/yourusername/yourusername.github.io.git
cd yourusername.github.io
```

---

# Step 4 — Initialize Jekyll in the Existing Repo

Run:

```bash
jekyll new . --force
```

This creates:

```text
_layouts/
_posts/
_config.yml
Gemfile
index.md
```

---

# Step 5 — Install Dependencies

```bash
bundle install
```

---

# Step 6 — Run Local Development Server

```bash
bundle exec jekyll serve
```

Open:

```text
http://localhost:4000
```

---

# Step 7 — Create Articles

Create markdown files inside:

```text
_posts/
```

Example:

```text
_posts/2026-05-18-my-first-article.md
```

Example content:

```markdown
---
layout: post
title: "My First Article"
date: 2026-05-18
tags: [jekyll, github-pages]
---

# Introduction

This is my article.
```

Jekyll automatically converts this into a blog page.

---

# Step 8 — Create Blog Index Page

Create:

```text
blog.md
```

Content:

```markdown
---
layout: page
title: Blog
permalink: /blog/
---

# Articles

{% raw %}
{% for post in site.posts %}
- [{{ post.title }}]({{ post.url }})
{% endfor %}
{% endraw %}
```

---

# Step 9 — Create Projects Page

Create:

```text
projects.md
```

Example:

```markdown
---
layout: page
title: Projects
permalink: /projects/
---

# Projects

## AI Agent Framework

GitHub:
https://github.com/yourusername/agent-framework

Related articles:
- /2026/05/18/agent-architecture.html
```

---

# Step 10 — Configure Site

Edit:

```text
_config.yml
```

Example:

```yaml
title: Your Name
description: Resume + Projects + Technical Articles

theme: minima
```

---

# Step 11 — Push Changes to GitHub

```bash
git add .
git commit -m "Convert site to Jekyll"
git push
```

---

# Step 12 — Enable GitHub Pages

GitHub Repository:

Settings → Pages

Under:

```text
Build and deployment
```

Choose:

```text
Deploy from branch
```

Settings:

* Branch: `main`
* Folder: `/root`

Save.

GitHub will automatically build the Jekyll site.

---

# Recommended Themes

## Minima (Simple)

```yaml
theme: minima
```

---

## Minimal Mistakes

[https://mmistakes.github.io/minimal-mistakes/](https://mmistakes.github.io/minimal-mistakes/)

Good for:

* Portfolio
* Blog
* Resume hybrid

---

## Chirpy

[https://chirpy.cotes.page/](https://chirpy.cotes.page/)

Good for:

* Developer blogs
* Syntax highlighting
* Modern UI

---

# Suggested Navigation Structure

```text
Home
├── Resume
├── Projects
├── Articles
└── Contact
```

---

# Suggested Workflow

## When Working on a Project

1. Create GitHub repository
2. Add project page on website
3. Write technical article explaining:

   * architecture
   * lessons learned
   * implementation details
4. Link article to repository

This creates a strong engineering portfolio.

---

# Useful Jekyll Commands

## Create and serve locally

```bash
bundle exec jekyll serve
```

---

## Build static site

```bash
bundle exec jekyll build
```

---

## Clean generated files

```bash
bundle exec jekyll clean
```

---

# Future Improvements

## Add Categories and Tags

Example:

```markdown
---
tags: [ai, rust]
categories: [engineering]
---
```

---

# Add Syntax Highlighting

Jekyll supports fenced markdown code blocks automatically.

Example:

````markdown
```python
print("hello")
```
````

---

# Add Dark Mode

Possible via:

* custom CSS
* themes
* JavaScript toggle

---

# Add Search

Recommended:

## Pagefind

[https://pagefind.app/](https://pagefind.app/)

## Lunr.js

[https://lunrjs.com/](https://lunrjs.com/)

---

# Add Custom Domain

Example:

```text
yourname.dev
```

GitHub Pages supports custom domains.

---

# Optional Alternative: Astro

Instead of Jekyll, you can later migrate to Astro if you want:

* modern frontend stack
* React/Vue support
* excellent markdown support
* better performance
* modern developer experience

[https://astro.build/](https://astro.build/)

---

# Final Recommended Architecture

```text
Resume
   ↓
Projects
   ↓
Technical Articles
   ↓
GitHub Repositories
```

This becomes:

* Resume
* Technical blog
* Knowledge base
* Project portfolio
* Personal engineering brand

all from a single GitHub Pages repository.

```
```
