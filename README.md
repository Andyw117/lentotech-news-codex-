# 伦拓科技 Lentotech 官方静态网站

Lentotech 官方站点，面向客户展示综合生命科学服务、行业动态与快速联系入口。网站为零构建静态站，可直接托管在 GitHub Pages。

Official static site for Lentotech, covering integrated life sciences services, news updates, and client contact entry points. The site is build-free and ready for GitHub Pages.

## 文件结构 / File Structure

```text
/
├── index.html
├── news.html
├── news-feed.json
├── og-cover.png
├── CNAME
├── .github/
│   └── workflows/
│       └── deploy.yml
└── README.md
```

## 本地预览 / Local Preview

新闻由 `news-feed.json` 动态加载，建议用本地 HTTP 服务预览。

News is loaded from `news-feed.json`, so preview with a local HTTP server.

```bash
python3 -m http.server 8080
```

访问 / Visit:

```text
http://localhost:8080/
```

## 更新新闻 / Update News

只需要编辑 `news-feed.json`，新增一条对象并推送到 `main` 分支。首页最新动态和新闻归档页会自动读取更新后的数据。

Edit only `news-feed.json`, add one object, and push to `main`. The home page preview and news archive will update automatically.

复制此模板 / Copy this template:

```json
{
  "id": "unique-news-slug-2026-05",
  "title_zh": "中文标题",
  "title_en": "English Title",
  "excerpt_zh": "中文摘要，建议 80-140 字，说明行业变化和客户可能关心的影响。",
  "excerpt_en": "English summary, ideally 80-140 characters, explaining the market signal and client impact.",
  "category": "regulatory",
  "date": "2026-05-13",
  "url": "https://source-article-url.com"
}
```

字段要求 / Field Rules:

| 字段 Field | 说明 Description |
| --- | --- |
| `id` | 唯一短链接标识，建议使用英文小写和连字符。Unique slug using lowercase English and hyphens. |
| `title_zh` | 中文标题。Chinese title. |
| `title_en` | English title. |
| `excerpt_zh` | 中文摘要。Chinese excerpt. |
| `excerpt_en` | English excerpt. |
| `category` | `regulatory`, `market`, `science`, `cdmo`, or `trade`. |
| `date` | ISO 日期，格式为 `YYYY-MM-DD`。ISO date in `YYYY-MM-DD`. |
| `url` | 原文来源链接。Source URL. |

分类说明 / Categories:

| 值 Value | 中文 | English |
| --- | --- | --- |
| `regulatory` | 监管合规 | Regulatory & Compliance |
| `market` | 市场动态 | Market Trends |
| `science` | 科学前沿 | Scientific Advances |
| `cdmo` | CDMO资讯 | CDMO News |
| `trade` | 贸易物流 | Trade & Logistics |

## 发布流程 / Deployment

`.github/workflows/deploy.yml` 会在推送到 `main` 时执行：

The workflow in `.github/workflows/deploy.yml` runs on pushes to `main`:

1. 校验 `news-feed.json` 是否为有效 JSON。
2. 检查每条新闻是否包含必填字段、合法分类、唯一 `id` 和有效 URL。
3. 发布静态文件到 `gh-pages` 分支。

GitHub Pages 设置建议 / Recommended GitHub Pages settings:

```text
Settings → Pages → Source: Deploy from a branch
Branch: gh-pages
Folder: / (root)
```

## 客户联系入口 / Client Contact

站点包含多个快速联系入口：

The site includes multiple client contact paths:

- 首页首屏 CTA / Hero CTA: `info@lentotech.com`
- 结构化询盘邮件 / Structured inquiry email
- 新闻页“咨询影响”入口 / News impact inquiry
- 移动端底部快捷栏 / Mobile sticky action bar
- WhatsApp 分享链接 / WhatsApp sharing link

## 社交分享 / Social Sharing

社交预览图使用 `og-cover.png`。更新品牌视觉时，替换同名文件即可。

Social preview uses `og-cover.png`. Replace that file when the brand visual changes.
