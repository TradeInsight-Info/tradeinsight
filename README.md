# docs-content

Docs and changelog source for tradeinsight.info. Plain MDX only — no build
toolchain here; `tradeinsight-web` compiles this content at its build time.

Content is **product-scoped**. Each product owns a folder:

- `<product>/docs/<slug>.mdx` — frontmatter: title, date, description, order (sidebar position)
- `<product>/changelog/<slug>.mdx` — frontmatter: title, date, description

Products: `data-api`, `timely-alert`, `ti-agent`. A product may launch without a
changelog (docs are required, changelog is optional).

Pushing to main triggers a site rebuild (see tradeinsight-web web-deploy.yml).
