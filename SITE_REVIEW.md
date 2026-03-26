# Website Review & GitHub Pages Deployment Plan

## Content Review

### Home Page (`content/_index.md`)
- **OK** — Intro, bio, and job status are clear and up to date.
- **OK** — Avatar image, social icons, and custom shortcode work correctly.
- **OK** — Selected Publications and Selected Projects sections are well structured.
- **OK** — News section is present with recent entries.

### Projects Page (`content/projects.md`)
- **OK** — Four projects with descriptions, keywords, and links.
- **OK** — Images added for each project with responsive flex layouts (rows collapse to columns on mobile).

### Publications Page (`content/publications.md`)
- **OK** — Single publication entry with abstract, arXiv link, and Google Scholar link.

### CV Page (`content/cv.md`)
- **OK** — Comprehensive: work experience, education, skills, languages, certifications.

### Contact Page (`content/contact.md`)
- **OK** — Obfuscated email, GitHub, LinkedIn links. Job-seeking status highlighted in bold.

### Blog (`content/blog/`)
- **OK** — Placeholder post removed. Empty list with a "stay tuned" message.

---

## Configuration Review (`hugo.toml`)

- **Critical** — `baseURL = 'https://example.org/'` must be updated to the actual GitHub Pages URL (e.g. `https://vicltz.github.io/` for a user page, or `https://vicltz.github.io/<repo-name>/` for a project page).
- **OK** — Theme set to `PaperMod`, which is present as a git submodule.
- **OK** — Navigation menu is complete (About, Projects, Publications, CV, Blog, Contact).
- **OK** — Social icons configured (GitHub, LinkedIn, Google Scholar).
- **OK** — `markup.goldmark.renderer.unsafe = true` is required for the raw HTML used in image layouts.

---

## Static Assets Review (`static/`)

- **OK** — Profile photo (`static/picture.jpeg`) is in the correct location.
- **OK** — Project media (`static/pics/`) contains all relevant GIFs and PNGs.
- **OK** — Root `pics/` directory removed; `static/pics/` is the single source of truth.
- **OK** — `cv.pdf` and `paper.pdf` removed from root.
- **Note** — `totorobo.png` is in `static/` but not referenced anywhere. Keep if planned for future use, otherwise remove to save space.
- **Issue** — The `public/` directory (generated build output) should not be committed. Covered by `.gitignore`.

---

## Theme Review (`themes/PaperMod`)

- **OK** — PaperMod configured as a git submodule pointing to the official upstream repo.
- **OK** — Submodule is initialized and pinned to a specific commit.
- **OK** — Custom shortcode `layouts/shortcodes/social_icons.html` correctly extends the theme.
- **OK** — Custom CSS at `assets/css/extended/custom.css` adds responsive image gallery classes.

---

## Git / Repository Status

- **Issue** — No commits have been made yet.
- **Issue** — No GitHub remote is configured.
- **OK** — `.gitignore` created.
- **Issue** — No GitHub Actions workflow exists for automated deployment.

---

## Steps to Deploy to GitHub Pages

### Step 1 — Create a GitHub repository

- Go to [github.com/new](https://github.com/new).
- For a **user page** (served at `https://vicltz.github.io/`), name the repo `vicltz.github.io`.
- For a **project page** (served at `https://vicltz.github.io/<repo-name>/`), use any repo name (e.g. `website`) and update `baseURL` accordingly.

### Step 2 — Update `baseURL` in `hugo.toml`

```toml
# For a user page:
baseURL = 'https://vicltz.github.io/'

# For a project page (e.g. repo named "website"):
baseURL = 'https://vicltz.github.io/website/'
```

### Step 3 — Create the GitHub Actions workflow

Create `.github/workflows/hugo.yml`:

```yaml
name: Deploy Hugo site to GitHub Pages

on:
  push:
    branches: [master]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          submodules: recursive

      - name: Setup Pages
        uses: actions/configure-pages@v5

      - name: Install Hugo
        run: |
          wget -O hugo.deb https://github.com/gohugoio/hugo/releases/download/v0.146.0/hugo_extended_0.146.0_linux-amd64.deb
          sudo dpkg -i hugo.deb

      - name: Build
        run: hugo --minify

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./public

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Step 4 — Initial commit and push

```bash
git add .gitignore .github/ hugo.toml content/ layouts/ assets/ static/ archetypes/ .gitmodules themes/
git commit -m "Initial commit: Hugo personal website"
git remote add origin https://github.com/vicltz/<repo-name>.git
git push -u origin master
```

### Step 5 — Enable GitHub Pages in repository settings

1. Go to the repository on GitHub → **Settings** → **Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.
3. The workflow will trigger on the next push and deploy the site automatically.

---

## Summary

| Area | Status |
|------|--------|
| Home page content | Ready |
| Projects page + images | Ready |
| Publications, CV, Contact | Ready |
| Blog | Ready (empty with message) |
| `baseURL` in hugo.toml | Needs update |
| Static assets | Ready |
| Responsive image layouts | Ready |
| `.gitignore` | Done |
| GitHub Actions workflow | Missing — create |
| GitHub remote | Not configured yet |
| Initial commit | Not made yet |
