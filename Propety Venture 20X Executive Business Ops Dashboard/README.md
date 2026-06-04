# Global Facilities Operating-Analytics — Executive Pack

A static, single-page website: the facilities-operations and capital-delivery executive dashboards plus the governing metric-definition standard. No build step, no backend, no database — GitHub Pages serves these files as-is.

## Files in this repository

| File | Purpose |
|---|---|
| `index.html` | The dashboard site — the page GitHub Pages serves at the root URL. |
| `404.html` | Branded "page not found" page. |
| `.nojekyll` | Tells GitHub Pages to skip the Jekyll build and serve the files directly. |
| `robots.txt` | Asks search engines not to crawl the site (reinforces the page's `noindex`; this is not an access control). |
| `LICENSE` | Proprietary / internal-use notice. |
| `README.md` | This file. |

## Deploy to GitHub Pages

1. Create a repository (see **Visibility** below) and upload all of these files to the repository **root**.
   - Web: the repo's **Add file → Upload files**, then drag the files in and **Commit**.
   - Git: `git add . && git commit -m "Add analytics site" && git push`.
2. In the repo: **Settings → Pages → Build and deployment**. Set **Source** to *Deploy from a branch*, then in the **Branch** row choose `main` in the first dropdown and `/ (root)` in the second, and **Save**.
3. The site goes live in about a minute at `https://<owner>.github.io/<repository>/`.
4. *(Optional)* Custom domain: add a `CNAME` file containing your domain, create a DNS `CNAME` record pointing to `<owner>.github.io`, set it under Settings → Pages → Custom domain, and keep **Enforce HTTPS** on.

## Visibility / confidentiality — read before publishing

The published page (HTML, CSS, JS) is readable by **anyone who can reach the URL**, even when the source repository is private.

| Setup | Source code | Published site |
|---|---|---|
| Public repo (GitHub Free) | Public | Public |
| Private repo + public Pages (Pro / Team / Enterprise) | Private | **Public** |
| Access-controlled site (GitHub Enterprise Cloud) | Private / internal | Restricted to people with repo read access |

For an internal, confidential standard, use **GitHub Enterprise Cloud with private Pages** (Settings → Pages → Visibility → *Private*) or host on an internal / SSO-gated server. All figures here are **illustrative placeholders** — do not stand up a publicly reachable site once real figures are in place unless the content has been cleared for public release.

## Updating the content

- **Current values, targets, insights** are inline in `index.html` — search the metric label (e.g. "Facility condition index").
- **Trend data** for each chart is the comma-separated `data-values` attribute on its `<svg class="spark">`.
- **X-axis month labels** are the `MONTHS` array near the top of the `<script>` at the bottom of `index.html` (`["Dec","Jan","Feb","Mar","Apr","May"]`). If you change the reporting window or the number of data points, update this array to match.
- **Status pills** are the `status ok` (green) or `status watch` (amber) class on each card.

## Network note

Fonts (Google Fonts) and icons (Tabler, via cdnjs) load from public CDNs with graceful fallback to system fonts. On locked-down corporate networks that block those CDNs, self-host the assets in an `assets/` folder and repoint the `<link>` tags to relative paths (e.g. `./assets/...`).
