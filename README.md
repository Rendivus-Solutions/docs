# Raddivus docs site (Mintlify)

This folder is the **public help center** for Raddivus, published with [Mintlify](https://mintlify.com) at `docs.raddivus.com`.

It is plain Markdown (`.mdx`) plus one config file (`docs.json`). There is no build step, no React, and no tests. Editing a page is just editing a Markdown file. The rest of the app repo stays private; only this folder is published.

## How it's structured

- `docs.json` — the config: site name, theme color, logo, and the sidebar/navigation tree. Every page must be listed here to appear in the nav.
- `*.mdx` — one file per help article. Frontmatter (`title`, `description`) sits at the top of each file.
- `logo/` and `favicon.svg` — brand assets. Swap these for a designed wordmark anytime.
- `images/` — screenshots (add as needed and reference with `![alt](/images/your-file.png)`).

## One-time setup (owner)

1. Create a free account at [mintlify.com](https://mintlify.com) (Hobby plan).
2. Connect this **private** GitHub repo via the Mintlify GitHub App. When prompted, set the docs directory to **`docs-site/`** (the monorepo / subdirectory option).
3. In the Mintlify dashboard, add the custom domain `docs.raddivus.com`, then add the **CNAME** DNS record Mintlify gives you at your domain registrar.

After that, every push to `main` auto-publishes.

## Editing docs

Two ways, both fine to mix:

- **No-code:** use the Mintlify web editor (1 free seat). Changes commit back to this folder.
- **In the repo:** edit the `.mdx` files directly (or ask Claude to). When a feature ships, the docs update in the same commit as the code.

## Preview locally (optional)

```bash
npm i -g mint
cd docs-site
mint dev          # serves the site at http://localhost:3000
mint broken-links # checks internal links
```

## SEO / AEO

Mintlify auto-generates `sitemap.xml`, `robots.txt`, and `llms.txt`. The landing-page repo's AI agent can read the live docs for product context at `https://docs.raddivus.com/llms.txt` (or any page as raw markdown by appending `.md` to its URL).

## Keeping it accurate

Pricing, credits, and plan facts come from `docs/product-documentation.md` and `docs/pricing.md` (internal). When those change, update the matching pages here in the same commit. See the "Documentation Sync" rule in the repo's `CLAUDE.md`.
