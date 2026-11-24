# Micro Clean Website

The static HTML site for **micro-clean.com**, hosted on Cloudflare (Worker `micro-clean-test`) and edited in Claude Design. Same setup as `Flexo-Concepts/FC-HTML-Website`.

```
public/              The website, exactly as Cloudflare serves it
  index.html         Homepage (copy of flexoconcepts.com/microclean_support/)
  assets/            Images, styles, fonts and scripts the page uses
  404.html           "Page not found" page
  robots.txt         Allows all crawlers
  _headers           noindex on *.workers.dev preview addresses only
docs/                Editing workflow and changelog
wrangler.jsonc       Cloudflare config: static files from ./public, no build step
```

## Addresses

| Address | Who can see it |
|---|---|
| `https://<branch>-micro-clean-test.flexo-concepts.workers.dev` | Preview of a branch; @flexoconcepts.com login only, noindexed |
| `https://micro-clean.com` | Everyone, once the domain is attached to the Worker |

How changes get published: **`docs/editing-workflow.md`** (branch → login-protected preview → pull request → merge → live).
