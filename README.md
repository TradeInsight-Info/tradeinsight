# TradeInsight Docs & Changelog

The content source for the **docs** and **changelog** on
[tradeinsight.info](https://tradeinsight.info). Plain MDX — there is no build
step in this repo; the public site (`tradeinsight-web`, a Remix app on
Cloudflare Workers) compiles this content at its own build time.

Edit Markdown here, open a PR, and once merged the site rebuilds and publishes
automatically. See **[CONTRIBUTION.md](./CONTRIBUTION.md)** for the how-to.

## Layout

Content is **product-scoped** — each product owns a folder with `docs/` (guides)
and an optional `changelog/` (release notes):

```
<product>/
  docs/<slug>.mdx        # guides — required
  changelog/<slug>.mdx   # release notes — optional
```

| Product        | Folder          | Published at                 |
| -------------- | --------------- | ---------------------------- |
| Data API       | `data-api/`     | `/docs/data-api`             |
| Timely Alert   | `timely-alert/` | `/docs/timely-alert`         |
| Finance Agent  | `ti-agent/`     | `/docs/ti-agent` *(flagged)* |

Every product's docs live at `/docs/<product>/<slug>`, its changelog at
`/docs/<product>/changelog`, and all changelogs are indexed together at
`/docs/changelog`. Finance Agent (`ti-agent`) is currently hidden from the docs
tabs behind a feature flag but stays reachable by URL.

## Frontmatter

Every file starts with YAML frontmatter.

**Docs** (`<product>/docs/*.mdx`) — sorted by `order`, ascending:

```yaml
---
title: Getting started
date: 2026-07-16
description: One-line summary shown in listings and meta tags.
order: 1
---
```

**Changelog** (`<product>/changelog/*.mdx`) — sorted by `date`, newest first:

```yaml
---
title: Insight and Timely Alert
date: 2026-07-09
description: One-line summary of the timeline.
---
```

## How it publishes

```
edit MDX → PR → merge to master
       → notify-site workflow fires a repository_dispatch (content-updated)
       → tradeinsight-web rebuilds and deploys to Cloudflare Workers
```

The `date` on the newest changelog entry drives the "latest" shown on the
`/docs` index and the `/docs/changelog` hub — keep it current when you add an
entry.
