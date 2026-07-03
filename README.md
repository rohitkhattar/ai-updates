# ai-updates — Daily AI Trends site

Auto-published daily digest of tech/AI trends. See `use-case.md` for the full problem statement.

## How it works

```
scheduled task "tech-ai-trends" (daily, evening)
        │  curates 5–8 trend items via web search
        ▼
_posts/YYYY-MM-DD-tech-ai-trends.md   (Jekyll post, front matter below)
        │  git commit + git push origin main
        ▼
GitHub Pages (Jekyll build)  →  site updates automatically
```

No manual index upkeep: Jekyll generates the paginated homepage, `/archive/` (grouped by year → month), RSS feed, and sitemap from the `_posts/` filenames alone.

## Post format the scheduled task must write

File: `_posts/YYYY-MM-DD-tech-ai-trends.md`

```markdown
---
title: "Tech & AI Trends — D Month YYYY"
date: YYYY-MM-DD 20:00:00 +0530
---

## 1. <Trend title>

<3–5 sentence description — detailed, technical, and written to make the reader want to click through>

[Source](<link>)

---

## 2. ...
```

`layout: post` and `author` are applied automatically via defaults in `_config.yml` — the front matter above is all a daily file needs.

## Publishing step (appended to the scheduled task)

After writing the day's post into `_posts/`:

```bash
cd "<this repo>"
git add _posts/
git commit -m "digest: YYYY-MM-DD tech/ai trends"
git push origin main
```

GitHub Pages rebuilds on push (typically live within ~1 minute).

## Local preview (optional)

```bash
bundle install
bundle exec jekyll serve   # http://localhost:4000
```
