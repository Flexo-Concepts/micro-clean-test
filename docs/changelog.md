# Changelog

## 2026-11-24 - New MicroClean Support homepage; support form moves to Contact Us
- The micro-clean.com homepage (`public/index.html`) is now the Claude Design "MicroClean Support Page Redesign": hero, "How MicroClean support works" in three steps, the anilox cleaning supplies / accessories callout and a closing call to action. It keeps the site's existing header and tracking.
- Both "Submit a support request" buttons open the MicroClean support form (`https://go.flexo.biz/l/199862/2022-01-27/fh2xmm`) in a new tab. "See accessories" links to `https://www.flexoconcepts.com/accessories/`.
- The design's "Since January 2022, every MicroClean support request starts with this web form." line was left out, to match the support-form page.
- The previous homepage, the page with the embedded support form, moves unchanged to `/contact-us/` (`public/contact-us/index.html`).
- The menu on both pages is now **Home** (links to `/`) + **Contact Us** (links to `/contact-us/`).
- Canonical tags on both pages still point to `https://www.flexoconcepts.com/microclean_support/`, so micro-clean.com doesn't compete with flexoconcepts.com in search.

## 2026-11-24 - Simpler menu, no search, no footer
- The top menu (desktop, sticky and mobile) now has only **Home**, which still links to `https://www.flexoconcepts.com/`, with no search icon or search box. Applications, Products, Resources, About Us, MicroClean, Contact Us and Order Online were removed, along with the search icon and the three search boxes (desktop, sticky and mobile).
- The site footer was removed entirely, including the "High Performance Doctor Blades" tagline, the Markets / TruPoint / Company link columns, Order Online and the "© 2026 Flexo Concepts | All Rights Reserved" line.

## 2026-11-24 - Homepage search uses flexoconcepts.com
- The three search boxes on the homepage now send searches to `https://www.flexoconcepts.com/`, because micro-clean.com has no search of its own (PR #6).

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
