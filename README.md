# tarek-elzoghby-hub

The source for my personal website: https://tarek-elzoghby.github.io/tarek-elzoghby-hub/

It is a small static site built with [Eleventy](https://www.11ty.dev/) (Liquid templates). The output is plain HTML and CSS with no client-side framework, and every page keeps its own `.html` URL.

## Structure

```
src/
  *.html            pages (index, about, projects, contact)
  projects/         one detail page per project
  _includes/        base.html (head, SEO, JSON-LD), nav.html, footer.html
  _data/accounts.json   platform accounts, the single source for the
                        footer links, rel="me" links and JSON-LD sameAs
  assets/           css, fonts, images
.github/workflows/deploy.yml   build and deploy
```

## Run it locally

```
npm ci
npx @11ty/eleventy --serve
```

The preview is at http://localhost:8080/tarek-elzoghby-hub/. A one-off build is `npx @11ty/eleventy`, which writes to `_site/`.

## Deploy

Pushing to `main` runs a GitHub Actions workflow that builds the site and publishes it to GitHub Pages. Pushing any other branch runs the build only, so a broken build shows up without touching the live site.

## Adding things

- **A platform account:** add one `{ "name": ..., "url": ... }` entry to `src/_data/accounts.json`. The footer, `rel="me"` links and structured data all update.
- **A page:** create `src/<name>.html` with front matter (`layout`, `title`, `description`, `canonical`), its own `<header>` with one `<h1>`, then `<main id="main-content">`. Add it to `nav.html` if it belongs in the navigation.

## Notes

- Colors are named by role (not by value), and CSS uses logical properties, so an Arabic (RTL) version can be added later without rewriting the styles.
- GitHub Pages is case-sensitive. Windows is not, so file names are lowercase.