# Changelog

## 2026-11-23 - Version 1: MicroClean page as the micro-clean.com homepage
- `public/index.html` is the HTML copy of `www.flexoconcepts.com/microclean_support/` from FC-HTML-Website, with the 63 images, styles, fonts and scripts it uses copied into `public/assets/` at the same paths.
- Links to other Flexo Concepts pages now point to `https://www.flexoconcepts.com/...`, because those pages don't exist on micro-clean.com. Links back to the MicroClean page point to `/`.
- Canonical stays `https://www.flexoconcepts.com/microclean_support/`, so the two copies don't compete in search.
- Tracking (GTM, GA4, Pardot, Hotjar, LinkedIn, Meta, Yahoo, Propensity) is ON, exactly as on the live flexoconcepts.com page.
- Cloudflare setup: `wrangler.jsonc` matches FC-HTML-Website (no plain test address, login-protected previews, `_headers` noindex on workers.dev).
