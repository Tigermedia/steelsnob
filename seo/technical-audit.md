# Technical SEO Audit Checklist - Steel Snob

## Pre-Audit (Need Access)
- [ ] WordPress admin login
- [ ] Google Search Console access
- [ ] Google Analytics access
- [ ] Hosting provider details (for speed optimization)

## Core Web Vitals
- [ ] Run PageSpeed Insights on homepage + 3 article pages
- [ ] LCP (Largest Contentful Paint) < 2.5s
- [ ] FID (First Input Delay) < 100ms
- [ ] CLS (Cumulative Layout Shift) < 0.1
- [ ] Check image sizes - compress oversized images
- [ ] Enable lazy loading for images
- [ ] Check theme/plugin bloat

## Crawlability & Indexing
- [ ] Verify robots.txt is not blocking anything important
- [ ] Check sitemap.xml is submitted to GSC (confirmed: sitemaps exist)
- [ ] Verify all posts are returning 200 status
- [ ] Check for duplicate content / canonical tags
- [ ] Check for orphan pages (no internal links pointing to them)
- [ ] Verify SSL certificate is valid

## On-Page SEO (Rank Math)
- [ ] Verify Rank Math global settings:
  - Title separator: |
  - Homepage title optimized
  - Schema type: Article for posts
  - Breadcrumbs enabled
  - Redirections module active
- [ ] Check all posts have:
  - Focus keyword set
  - Meta description written
  - SEO score 80+
- [ ] Enable FAQ schema on relevant posts
- [ ] Enable HowTo schema on tutorial posts

## Site Structure
- [ ] Clean URL structure (/category/post-name/ or /post-name/)
- [ ] Categories have descriptions and aren't thin
- [ ] No excessive tag pages (thin content trap)
- [ ] 404 page is helpful (suggests popular content)

## Speed Optimization
- [ ] Install/configure caching plugin (WP Super Cache, W3 Total Cache, or LiteSpeed)
- [ ] Enable GZIP compression
- [ ] Minify CSS/JS
- [ ] Use CDN (Cloudflare free tier)
- [ ] Optimize/compress all images (ShortPixel or Imagify)
- [ ] Remove unused plugins
- [ ] Check database for bloat

## Mobile
- [ ] Verify mobile responsiveness (Google Mobile-Friendly Test)
- [ ] Check font sizes readable on mobile
- [ ] Check tap targets are properly spaced
- [ ] No horizontal scrolling
- [ ] Tables are responsive

## Link Health
- [ ] Run broken link checker on all pages
- [ ] Fix or redirect broken outbound links
- [ ] Fix or redirect broken internal links
- [ ] Check Amazon affiliate links still work
- [ ] Verify no affiliate links are cloaked (Amazon TOS)

## Schema Markup
- [ ] Article schema on all posts (Rank Math auto-generates)
- [ ] FAQ schema on FAQ sections
- [ ] Product schema on review articles
- [ ] Breadcrumb schema
- [ ] Site logo + organization schema
