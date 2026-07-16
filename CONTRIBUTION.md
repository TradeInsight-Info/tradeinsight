# Contributing

Thanks for improving the TradeInsight docs! This repo is **plain MDX** — if you
can write Markdown, you can contribute. No build tools, no framework knowledge
required. The public site ([tradeinsight.info](https://tradeinsight.info))
compiles this content when it deploys.

## Quick start

1. Fork or branch, then edit the Markdown.
2. Open a pull request.
3. Once it's merged to `master`, the site rebuilds and your change goes live
   automatically — usually within a few minutes.

You can edit a file straight from the GitHub UI (pencil icon) for small fixes.

## Where things live

Content is **product-scoped** — each product has its own folder:

```
<product>/
  docs/<slug>.mdx        # guides (required)
  changelog/<slug>.mdx   # release notes (optional)
```

Products: `data-api`, `timely-alert`, `ti-agent`. The **file name is the URL
slug** — `data-api/docs/first-query.mdx` publishes at `/docs/data-api/first-query`.
Use lowercase, hyphenated names (`getting-started`, not `Getting Started`).

## Add or edit a doc

Create `<product>/docs/<slug>.mdx` with this frontmatter, then write the guide
below it:

```mdx
---
title: First query
date: 2026-07-16
description: Run your first request against the Data API.
order: 2
---

Your content here. Standard Markdown works: headings, lists, code blocks,
tables, links, and images.
```

| Field         | Required | Notes                                             |
| ------------- | -------- | ------------------------------------------------- |
| `title`       | yes      | Shown as the page `<h1>` and in the sidebar.      |
| `date`        | yes      | `YYYY-MM-DD`. Last meaningful update.              |
| `description` | yes      | One line; used in listings and `<meta>` tags.     |
| `order`       | yes      | Sidebar position, ascending (1, 2, 3…).           |

## Add a changelog entry

Changelog files are a **timeline**: one file per product, newest date at the
top. Add a dated `####` section with bullet points:

```mdx
---
title: Insight and Timely Alert
date: 2026-07-09
description: A timeline of product updates.
---

#### 2026-07-09

- Short, user-facing summary of what shipped.
- One bullet per change; lead with the benefit, not the internals.

#### 2026-04-25

- …older entries stay below…
```

When you add a new dated section, **update the frontmatter `date` to match the
newest section** — it drives the "latest" shown on the `/docs` index and the
`/docs/changelog` hub. Changelog files are sorted newest-first by `date`.

## Writing style

- **Voice:** sharp, precise, trustworthy. Say what the product does; skip the hype.
- **Be concise.** Short sentences and lists beat long paragraphs.
- **Dates** are always `YYYY-MM-DD`.
- **Links** need a full URL for external targets (`https://app.tradeinsight.info`),
  or a site-relative path for internal ones (`/pricing`).
- **Images** go under `/static/...` and are referenced with normal Markdown:
  `![Alt text](/static/2026/my-screenshot.webp)`. Always write real alt text.
- **Code blocks** use fenced blocks with a language tag (```` ```bash ````).

## Preview locally (optional)

You don't need to run anything to contribute. If you want to preview, run the
`tradeinsight-web` app (in the TradeInsight monorepo) with a fresh content fetch:

```bash
# from apps/tradeinsight-web
FORCE_CONTENT_FETCH=1 ./scripts/fetch-content.sh
bun run dev   # http://localhost:5173/docs
```

## PR checklist

- [ ] File is in the right `<product>/{docs,changelog}/` folder.
- [ ] Frontmatter is complete and valid (see tables above).
- [ ] `date` is `YYYY-MM-DD`; changelog frontmatter `date` matches the newest section.
- [ ] Links resolve; images have alt text.
- [ ] Read it once more for clarity and tone.
