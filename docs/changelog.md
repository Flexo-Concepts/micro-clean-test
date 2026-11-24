# Changelog

## 2026-11-24 - Faster pages: Avada / Fusion Builder removed
- Both pages are rebuilt as lean, hand-written HTML. They no longer load Avada's stylesheet (about 1.3 MB, 194 KB compressed and render-blocking), the Fusion Builder script bundle (705 KB), jQuery and jQuery Migrate, WP Rocket lazy-loading or the WPML language switcher. The small "English" button at the bottom of the pages is gone with it.
- Each page now loads one inline stylesheet, Open Sans 400/700 once from Google Fonts (with preconnect, instead of twice), GA4, the Yahoo pixel and Pardot tracking, and no other JavaScript. HTML size: homepage 64 KB → 24 KB, Contact Us 57 KB → 12 KB.
- Kept unchanged: page copy and layout, the support form, titles, descriptions, canonicals, structured data, favicons, GA4 `G-KSGE957FQY`, the Yahoo pixel and Pardot tracking.
- **Tracking removed:** Hotjar (site ID 5259572), the LinkedIn Insight Tag (partner 3771722), the Meta pixel (25378122245118744), the Propensity tracker and the Salesforce chat button are taken off both pages, so micro-clean.com visits no longer go into those Flexo Concepts accounts.
- The header is now simple HTML: Flexo Concepts logo + Home / Contact Us, sticky on desktop, with the current page underlined in orange. The MicroClean logo on Contact Us gets alt text.
- The old theme files stay in `public/assets/` for now but are no longer used; they can go in the planned cleanup PR.

## 2026-11-24 - SEO setup: micro-clean.com ranks on its own
- **Canonical:** both pages' canonical and hreflang tags now point to themselves on micro-clean.com (`https://micro-clean.com/` and `https://micro-clean.com/contact-us/`) instead of `https://www.flexoconcepts.com/microclean_support/`, so Google can rank micro-clean.com in its own right (Michelle's decision).
- **Contact Us page details:** new title "Contact MicroClean Support | Flexo Concepts" and description "Submit a MicroClean support request. Including your machine model and serial number will help expedite your request." The WordPress (Yoast) structured data that described the flexoconcepts.com page is replaced with the page's own ContactPage and breadcrumb data.
- **Structured data:** the homepage now describes itself to search engines and AI answer engines as a WebSite + WebPage, with the three "How MicroClean support works" steps as a HowTo. All of it is taken from the page's existing copy. The sitewide Flexo Concepts Organization data gets an `@id` so the two link up.
- **Tidy-up:** removed the duplicate description and social-share tags left over from WordPress on both pages, and set the social-share type to "website".
- **Sitemap:** new `public/sitemap.xml` lists the homepage and Contact Us, and `robots.txt` now points to it.

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
