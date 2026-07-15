# ti-agent docs

Home for the **ti CLI agent** user-facing docs and changelog, consolidated into
this repo so all TradeInsight docs live in one place. The standalone `ti-agent`
GitHub repo (previously empty) is retired in favour of this folder.

## Layout

- `docs/<slug>.mdx` — ti agent guides (frontmatter: title, date, description, order)
- `changelog/<slug>.mdx` — ti agent changelog (frontmatter: title, date, description)

## Publishing note

`tradeinsight-web` currently compiles the repo-root `docs/` and `changelog/`
folders (see this repo's top-level README). Point the web build at this
subfolder before its content publishes to tradeinsight.info.
