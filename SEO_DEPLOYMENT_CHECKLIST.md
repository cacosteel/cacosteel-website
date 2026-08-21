# CACO Steel SEO deployment checklist

## Implemented in this package
- Centralized meta descriptions, canonical URLs, robots directives, Open Graph and Twitter metadata.
- Organization, WebSite and WebPage JSON-LD structured data.
- Unique SEO titles and descriptions for Home, About, Products, Services, Resources, Contact and Terms.
- 1200x630 social sharing image at `/public/images/caco-steel-social.jpg`.
- `/legal` mapped to `/terms` in Astro redirects.
- Sitemap integration configured to omit the legacy `/legal` route.
- `robots.txt` points to the canonical `www.cacosteel.com` sitemap.

## Hosting / DNS actions still required
1. Make `https://www.cacosteel.com` the single canonical public host.
2. Configure HTTP -> HTTPS at the hosting/CDN layer.
3. Configure `https://cacosteel.com/*` -> `https://www.cacosteel.com/*` as a permanent 301/308 redirect.
4. Configure `cacogroup.com` and `www.cacogroup.com` to permanently redirect to the matching path on `https://www.cacosteel.com` if both domains are intended to represent the same website.
5. Ensure `/legal` returns a real HTTP 301 to `/terms` at the host/CDN layer. Astro's static fallback can emit an HTML redirect, but the hosting-layer 301 is preferred for a migrated indexed URL.

## Google Search Console after deployment
1. Verify the canonical domain property if not already verified.
2. Submit `https://www.cacosteel.com/sitemap-index.xml`.
3. Inspect and request indexing for `/`, `/about`, `/products`, `/services`, `/resources`, `/contact`, `/terms`.
4. Inspect `/legal` and confirm Google sees the permanent redirect to `/terms`.
5. Check Page indexing, Sitemaps and Core Web Vitals after the new build has been live.

## Build note
The source package was updated and directly reviewed, but dependency installation timed out in the provided execution environment, so `npm run build` could not be completed here. Run `npm ci && npm run build` in the normal deployment environment before publishing.
