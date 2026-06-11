# docs-content

Docs and changelog source for tradeinsight.info. Plain MDX only — no build
toolchain here; `tradeinsight-web` compiles this content at its build time.

- `docs/<slug>.mdx` — frontmatter: title, date, description, order (sidebar position)
- `changelog/<slug>.mdx` — frontmatter: title, date, description

Pushing to main triggers a site rebuild (see tradeinsight-web web-deploy.yml).
