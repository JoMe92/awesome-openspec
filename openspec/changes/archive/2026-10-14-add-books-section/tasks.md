# Add a Books section and move the existing book into it

Schema: `tinychange`, from https://github.com/speclib/openspec-tinychange-schema
(install it with the guide in that repo's AGENT_INSTALL.md).

Bean: awesome-openspec-0u7g (01 List curation and growth).

The list now has two books, so they get their own section instead of sitting
among articles. `Spec-Driven Development (book)` arrived in PR #12 and landed in
Articles & Tutorials, which is the only place a book could go at the time.

The new entry is the Kindle edition of "Non-Deterministic Spec-Driven
Development: Enterprise Edition" by Enrico Papalini. It uses the short
`https://www.amazon.com/dp/B0GZPNCGR1` form of the Amazon URL: the full slug URL
is 106 characters, which cannot fit under the 150 character line limit at any
description length. Amazon returns HTTP 500 to automated fetches, so the title
and author were confirmed through search results rather than by reading the page.

Section placement is editorial, not alphabetical: the README's `## ` sections do
not read alphabetically, so Books goes next to the other media sections, between
GitHub Actions and Videos. Entries inside Books are alphabetical as everywhere
else, which puts Non-Deterministic before Spec-Driven.

## 1. Implementation

- [x] 1.1 In `README.md`, add a `## Books` section between `## GitHub Actions` and `## Videos`.
- [x] 1.2 Move `- [Spec-Driven Development (book)](https://github.com/felipefontoura/spec-driven-development-book) - Open SDD book with a Claude Code kit.` out of `## Articles & Tutorials` and into `## Books`, leaving the line itself unchanged.
- [x] 1.3 Add `- [Non-Deterministic Spec-Driven Development: Enterprise Edition](https://www.amazon.com/dp/B0GZPNCGR1) - From frameworks to enterprise practice.` to `## Books`, before the Spec-Driven Development entry (145 characters, within the 150 limit).
- [x] 1.4 Add `- [Books](#books)` to the `## Contents` list between the GitHub Actions and Videos entries, so the TOC order matches the heading order that awesome-lint's toc rule checks.
- [x] 1.5 In `CONTRIBUTING.md`, add books to the "What to Add" list.

## 2. Verification

- [x] 2.1 Capture the `npm run lint` baseline first, then run it again after the edit and confirm no NEW warnings. Remark exits 0 on warnings, so read the output rather than trusting the exit code. The 4 pre-existing warnings (TOC "Related Projects", two over-length lines, one ordering violation in Related Awesome Lists) are not part of this change.
- [x] 2.2 Run `node scripts/fetch-entries.js` and confirm `data/entries.json` gains a section titled "Books" holding exactly the two entries, and that neither still appears under "Articles & Tutorials".
- [x] 2.3 Run `npm --prefix site run build` and confirm the site builds with a Books group.
- [x] 2.4 Run `nix flake check`.
