# Micro Clean Website — CLAUDE.md

## What this is

The static HTML site for **micro-clean.com**, hosted on **Cloudflare Workers static assets** (Worker name `micro-clean-test`) and edited with Claude and Claude Design. It works the same way as `Flexo-Concepts/FC-HTML-Website` (flexoconcepts.com). Version 1 is the HTML copy of `www.flexoconcepts.com/microclean_support/` from that repo, served as the micro-clean.com homepage.

- **Owner and approver:** Michelle McGuire (marketing). Repo admin: Anna Tedeschi.
- **Path to production:** feature branch → Cloudflare preview → PR → merge into `main` → Cloudflare Workers Builds deploys `main` automatically to micro-clean.com.
- **`main` is protected** by the Flexo-Concepts org rule (one approving review). Michelle merges her own PRs with **"Merge without waiting for requirements to be met (bypass rules)"**, or Anna approves.
- **Key surfaces:** `public/` (the site exactly as served), `public/_headers`, `wrangler.jsonc`, `docs/editing-workflow.md`.

## Ground rules

1. Never change DNS, nameservers, the registrar (Network Solutions) or Cloudflare account settings without saying what will happen and getting Michelle's OK.
2. Preview addresses stay behind Cloudflare Access **and** noindexed. Never put a preview URL in a sitemap, never ship `robots.txt` with `Disallow: /`.
3. Canonical tags on pages copied from flexoconcepts.com point to their `https://www.flexoconcepts.com/...` page, so micro-clean.com never competes with flexoconcepts.com in search. Change a canonical only when Michelle decides a page should rank on micro-clean.com itself.
4. Never ask for or store passwords or API keys.
5. Before anything that publishes, deploys or changes account settings, say what will happen and get Michelle's OK.

## Build & deploy

- No build step. Cloudflare serves `./public` as-is (`html_handling: auto-trailing-slash`, `not_found_handling: 404-page`).
- The `name` in `wrangler.jsonc` must match the Worker name in Cloudflare (`micro-clean-test`), or builds fail.
- `workers_dev` is `false` and `preview_urls` is `true`. Cloudflare Access (Worker Access, scope **"Previews only"**, email domain flexoconcepts.com) protects every preview hostname. Never use scope "All traffic": it also puts the login on micro-clean.com.
- `"previews": {}` must stay in `wrangler.jsonc`: branch builds run `npx wrangler preview`, which fails without it.
- `main` deploys with `npx wrangler deploy`; every other branch gets a preview at `<branch>-micro-clean-test.flexo-concepts.workers.dev`.
- micro-clean.com and www.micro-clean.com are attached to the Worker as Custom Domains in the Cloudflare dashboard (not in `wrangler.jsonc`).

## Conventions

- New pages and redesigns from Claude Design follow the FC fragment contract (Flexo Concepts Design System → *flexoconcepts.com — website patterns*): one wrapper class, one scoped `<style>`, no JS (native `<details>`), one H1, every image `alt`'d.
- Pages are lean, hand-written HTML (no Avada, Fusion Builder, jQuery or WordPress plugins): `public/index.html` (homepage, from the Claude Design "MicroClean Support Page Redesign") and `public/contact-us/index.html` (the Pardot support form). Each page has one inline `<style>`, the shared header (logo + Home / Contact Us), its SEO tags and structured data, GA4 `G-KSGE957FQY`, and the kept tracking (LinkedIn, Meta, Yahoo, Propensity, Pardot, Salesforce chat; Hotjar removed). Keep new pages to the same pattern.
- Links to other Flexo Concepts pages are absolute `https://www.flexoconcepts.com/...` URLs; those pages don't exist on micro-clean.com.
- Images: `public/assets/uploads/YYYY/MM/*.webp`, under 25 MiB per file.
- Commit messages and PR bodies in plain language for a marketing reader.
- Add an entry to `docs/changelog.md` for every merged change.
- Known clutter: the first upload put loose copies of the site's images, fonts and scripts at the repo root. Cloudflare only serves `public/`, so they're harmless; remove them in a cleanup PR.

## Lessons Learned

- GitHub's web upload flattens folders when files are dragged out of an unextracted zip. Extract first and drag the folder itself, then check the file list shows `public/...` before committing.
- Uploading to a protected `main` silently commits to a new `<user>-patch-N` branch. Cloudflare builds only `main`, so open a PR and merge it.
- Transferring a repo into the org disconnects Cloudflare Workers Builds from it. Reconnect in Settings → Build, or merges won't trigger builds.
