# World Energy Atlas

Static site hosted on **Cloudflare Pages** (project: `atlas-energy`).

## Live URLs
- https://www.energystax.com
- https://www.worldenergyatlas.com
- https://atlas-energy.pages.dev

## Files
- `index.html` — main World Energy Atlas encyclopedia page
- `energy-news.html` — Energy News page (data is defined inline in the `<script>` block: `NEWS`, `BREAKING`, `BASE_PRICES`, and the hero `.h-stat` blocks)

## Deploy
Requires a Cloudflare API token with **Pages: Edit** permission in the
`CLOUDFLARE_API_TOKEN` environment variable:

```bash
npx wrangler pages deploy . --project-name atlas-energy --branch main --commit-dirty=true
```

This updates all custom domains at once (they all point at the same project).

## Keeping the news page current
The news content in `energy-news.html` is hardcoded. A scheduled cloud agent
refreshes it daily: it researches the latest energy news/prices, rewrites the
`NEWS`, `BREAKING`, and `BASE_PRICES` arrays (and the hero stat figures + the
`.last-updated` date in the dataset), commits, and redeploys.
