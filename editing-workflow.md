# Editing micro-clean.com: design → branch → preview → PR → merge

The same flow as flexoconcepts.com (FC-HTML-Website), with Michelle as the approver.

1. **Design or ask.** For a new page or a visual change, design it in **Claude Design** on the Flexo Concepts Design System. For copy changes, just tell Claude what to change.
2. **Claude puts it on a branch.** It never edits `main` directly, so micro-clean.com keeps running unchanged.
3. **Cloudflare builds a preview** about 2–3 minutes after the branch is pushed:
   `https://<branch-name>-micro-clean-website.flexo-concepts.workers.dev`
   It's behind the @flexoconcepts.com login (one-time code by email) and noindexed. Claude sends you the link.
4. **Review.** Click around, check your phone, ask for fixes. Each fix refreshes the same link.
5. **Pull request.** When you're happy, Claude opens a pull request into `main` with the preview link.
6. **Merge.** You merge it on GitHub. Cloudflare deploys `main` to micro-clean.com in about 1–2 minutes.
7. **Undo.** Cloudflare → Workers & Pages → micro-clean-website → Deployments → previous version → *Rollback*, or revert the pull request on GitHub.

## Rules every change follows

- Canonical tags stay pointed at the matching flexoconcepts.com page unless you decide otherwise.
- New-look pages follow the fragment contract: one wrapper, scoped CSS, no JavaScript, one H1, every image `alt`'d.
- Images go in `public/assets/uploads/YYYY/MM/` as `.webp`, about twice their display width, each under 25 MB.
- Approved copy only: sanctioned CTAs, exact market names, verified stats, approved customer quotes.
