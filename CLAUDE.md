# Micro Clean Website — CLAUDE.md

## What this is

The static HTML site for **micro-clean.com**, hosted on **Cloudflare Workers static assets** and edited with Claude and Claude Design. It works the same way as `Flexo-Concepts/FC-HTML-Website` (flexoconcepts.com). Version 1 is the HTML copy of `www.flexoconcepts.com/microclean_support/` from that repo, served as the micro-clean.com homepage.

- **Owner and approver:** Michelle McGuire (marketing). Michelle reviews, approves and merges her own pull requests.
- **Path to production:** feature branch → Cloudflare preview → PR → Michelle merges into `main` → Cloudflare Workers Builds deploys `main` automatically to micro-clean.com.
- **Key surfaces:** `public/` (the site exactly as served), `public/_headers`, `wrangler.jsonc`, `docs/editing-workflow.md`.

## Ground rules

1. Never change DNS, nameservers, the registrar (Network Solutions) or Cloudflare account settings without saying what will happen and getting Michelle's OK.
2. Preview addresses stay behind Cloudflare Access **and** noindexed. Never put a preview URL in a sitemap, never ship `robots.txt` with `Disallow: /`.
3. Canonical tags on pages copied from flexoconcepts.com point to their `https://www.flexoconcepts.com/...` page, so micro-clean.com never competes with flexoconcepts.com in search. Change a canonical only when Michelle decides a page should rank on micro-clean.com itself.
4. Never ask for or store passwords or API keys.
5. Before anything that publishes, deploys or changes account settings, say what will happen and get Michelle's OK.

## Build & deploy

- No build step. Cloudflare serves `./public` as-is (`html_handling: auto-trailing-slash`, `not_found_handling: 404-page`).
- `workers_dev` is `false` and `preview_urls` is `true`. Cloudflare Access (Worker Access, scope **"Previews only"**, email domain flexoconcepts.com) protects every preview hostname. Never use scope "All traffic": it also puts the login on micro-clean.com.
- `"previews": {}` must stay in `wrangler.jsonc`: branch builds run `npx wrangler preview`, which fails without it.
- `main` deploys with `npx wrangler deploy`; every other branch gets a preview at `<branch>-micro-clean-website.flexo-concepts.workers.dev`.
- micro-clean.com and www.micro-clean.com are attached to the Worker as Custom Domains in the Cloudflare dashboard (not in `wrangler.jsonc`).

## Conventions

- New pages and redesigns from Claude Design follow the FC fragment contract (Flexo Concepts Design System → *flexoconcepts.com — website patterns*): one wrapper class, one scoped `<style>`, no JS (native `<details>`), one H1, every image `alt`'d.
- `public/index.html` is frozen Avada output copied from FC-HTML-Website. Edit text in place; replace it whole when a Claude Design redesign is approved.
- Links to other Flexo Concepts pages are absolute `https://www.flexoconcepts.com/...` URLs; those pages don't exist on micro-clean.com.
- Images: `public/assets/uploads/YYYY/MM/*.webp`, under 25 MiB per file.
- Commit messages and PR bodies in plain language for a marketing reader.
- Add an entry to `docs/changelog.md` for every merged change.

## Lessons Learned
