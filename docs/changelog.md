# Changelog

## 2026-11-24 - SEO setup: micro-clean.com ranks on its own
- **Canonical:** the homepage's canonical and hreflang tags now point to `https://micro-clean.com/` instead of `https://www.flexoconcepts.com/microclean_support/`, so Google can rank micro-clean.com in its own right (Michelle's decision). The Contact Us page still points to flexoconcepts.com, because it is a copy of that page.
- **Structured data:** the homepage now describes itself to search engines and AI answer engines as a WebSite + WebPage, with the three "How MicroClean support works" steps as a HowTo. All of it is taken from the page's existing copy. The sitewide Flexo Concepts Organization data gets an `@id` so the two link up.
- **Tidy-up:** removed the duplicate description and social-share tags left over from WordPress, and set the social-share type to "website".
- **Sitemap:** new `public/sitemap.xml` lists the homepage, and `robots.txt` now points to it. Contact Us is left out of the sitemap, because its canonical is on flexoconcepts.com.

## 2026-11-24 - New MicroClean Support homepage; support form moves to Contact Us
- The micro-clean.com homepage (`public/index.html`) is now the Claude Design "MicroClean Support Page Redesign": hero, "How MicroClean support works" in three steps, the anilox cleaning supplies / accessories callout and a closing call to action. It keeps the site's existing header.
- Both "Submit a support request" buttons go to the support-form page at `/contact-us/` (same tab). "See accessories" links to `https://www.flexoconcepts.com/accessories/`.
- The design's "Since January 2022, every MicroClean support request starts with this web form." line was left out, to match the support-form page.
- The previous homepage, the page with the embedded support form, moves unchanged to `/contact-us/` (`public/contact-us/index.html`).
- The menu on both pages is now **Home** (links to `/`) + **Contact Us** (links to `/contact-us/`).
- Canonical tags on both pages still point to `https://www.flexoconcepts.com/microclean_support/`, so micro-clean.com doesn't compete with flexoconcepts.com in search.
- **Google Analytics removed:** Google Tag Manager (GTM-5JTCPFW), the GA4 tag (G-BFKJFN3MY9) and the GTM-for-WordPress helper scripts are removed from both pages, so micro-clean.com is no longer tracked in Flexo Concepts' Google Analytics. micro-clean.com now has its own GA4 property instead (measurement ID `G-KSGE957FQY`), added as a plain Google tag (gtag.js) at the top of both pages. HotJar, LinkedIn, Meta, Propensity, Pardot and the Service Cloud chat snippets are unchanged.

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
