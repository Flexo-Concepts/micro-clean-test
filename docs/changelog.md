# Changelog

## 2026-11-24 - Support intro updated
- Removed the outdated sentence "Due to our hybrid work environment, as of January 2022 all MicroClean support requests must be initiated through this web form." from the paragraph under "Support". The paragraph now starts with "Please provide the required information below."
- The page's search description, social-share description and structured data used the same sentence, so they now use the remaining paragraph text instead.

## 2026-11-24 - Setup fixes
- Worker name in `wrangler.jsonc` set to `micro-clean-test` to match Cloudflare (PR #2).
- Cloudflare reconnected to the repo after it moved into the Flexo-Concepts org, and Cloudflare's GitHub app given access to micro-clean-test so merges trigger builds.
- Docs moved into `docs/` and updated for the `micro-clean-test` preview addresses and the review rule on `main` (PR #4).

## 2026-11-23 - Version 1: MicroClean page as the micro-clean.com homepage
- `public/index.html` is the HTML copy of `www.flexoconcepts.com/microclean_support/` from FC-HTML-Website, with the 63 images, styles, fonts and scripts it uses copied into `public/assets/` at the same paths (PR #1).
- Links to other Flexo Concepts pages now point to `https://www.flexoconcepts.com/...`, because those pages don't exist on micro-clean.com. Links back to the MicroClean page point to `/`.
- Canonical stays `https://www.flexoconcepts.com/microclean_support/`, so the two copies don't compete in search.
- Tracking (GTM, GA4, Pardot, Hotjar, LinkedIn, Meta, Yahoo, Propensity) is ON, exactly as on the live flexoconcepts.com page.
- Cloudflare setup: `wrangler.jsonc` matches FC-HTML-Website (no plain test address, login-protected previews, `_headers` noindex on workers.dev).
