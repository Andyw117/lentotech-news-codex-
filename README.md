# Virdis BioOps Static Site / Virdis 生物运营静态网站

A zero-build, Tailwind CDN static landing site for GitHub Pages. / 这是一个零构建、使用 Tailwind CDN、可部署到 GitHub Pages 的静态落地页。

## Files / 文件

- `index.html` — Main bilingual landing page with SEO and social preview metadata. / 主双语落地页，包含 SEO 与社交预览元数据。
- `news.html` — Date-grouped bilingual news archive. / 按日期分组的双语新闻归档页。
- `news-feed.json` — Shared sample news payload with five entries. / 共享示例新闻数据，包含五条内容。
- `.github/workflows/deploy.yml` — GitHub Actions workflow that publishes the site to the `gh-pages` branch. / 将网站发布到 `gh-pages` 分支的 GitHub Actions 工作流。

## Local Preview / 本地预览

Open `index.html` directly in a browser for a quick visual check. / 可直接在浏览器中打开 `index.html` 进行快速视觉检查。

For the JSON-powered news rendering, run a local static server from the repository root. / 如需检查由 JSON 驱动的新闻渲染，请在仓库根目录启动本地静态服务器。

```bash
python3 -m http.server 8080
```

Then visit `http://localhost:8080/`. / 然后访问 `http://localhost:8080/`。

## Deployment / 部署

Push the files to the default branch of a GitHub repository. / 将这些文件推送到 GitHub 仓库的默认分支。

The workflow runs on pushes to `main` or `master`, creates a static artifact, and force-publishes it to the `gh-pages` branch. / 工作流会在推送到 `main` 或 `master` 时运行，生成静态产物，并强制发布到 `gh-pages` 分支。

In GitHub repository settings, set Pages to serve from the `gh-pages` branch and the repository root. / 在 GitHub 仓库设置中，将 Pages 来源设为 `gh-pages` 分支与仓库根目录。

## Updating News / 更新新闻

Edit `news-feed.json` and keep each entry in this shape. / 编辑 `news-feed.json`，并保持每条内容使用以下结构。

```json
{
  "id": "2026-05-08-quality-rooms",
  "date": "2026-05-08",
  "category": {
    "en": "Platform",
    "zh": "平台"
  },
  "title": {
    "en": "Virdis BioOps introduces audit-ready quality rooms",
    "zh": "Virdis BioOps 发布审计就绪质量空间"
  },
  "summary": {
    "en": "New controls help biotech teams preserve reviewer decisions, evidence lineage, and partner-ready exports.",
    "zh": "新控制能力帮助生物技术团队保留审阅决策、证据血缘与合作方就绪导出。"
  },
  "readTime": {
    "en": "3 min read",
    "zh": "阅读约 3 分钟"
  }
}
```

Use ISO dates in `YYYY-MM-DD` format so `news.html` can group entries by month. / 请使用 `YYYY-MM-DD` 格式的 ISO 日期，以便 `news.html` 按月份分组。

Keep all public-facing news fields bilingual. / 所有面向公众展示的新闻字段都应保持双语。

After editing, push the change and GitHub Actions will redeploy the site. / 编辑完成后推送更改，GitHub Actions 会重新部署网站。
