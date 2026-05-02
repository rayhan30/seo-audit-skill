---
name: seo-audit
description: >
  Perform a comprehensive SEO audit of any website and generate a structured branded report.
  Use this skill whenever the user mentions auditing a website, checking SEO health,
  finding SEO problems, reviewing on-page SEO, or asking why a site ranks poorly.
  Also trigger for requests like "check my site's SEO", "what's wrong with my website SEO",
  "run an SEO report", or "audit this URL". Covers technical SEO, on-page elements,
  structured data, page speed, local SEO, internal linking, plugin audit, and keyword targeting.
  Always use this skill for any SEO-related website review, even if the user doesn't
  say "audit" explicitly.
---

# SEO Audit Skill

Perform a thorough, structured SEO audit of a given URL and produce a clear branded HTML
report with findings, severity ratings, and actionable fix instructions.

---

## Inputs

- **URL** (required): The page or site to audit. Ask if not provided.
- **Client Name** (required): Ask if not provided.
- **City / Location** (required): Ask if not provided.
- **Date** (required): Ask if not provided. Default to current month and year.
- **Agency Name** (optional): The "Prepared by" name on the cover page. Default to blank if not provided.
- **Agency Tagline** (optional): One-line description shown under the agency name.
- **Scope** (optional): Single page vs. site-wide. Default to single page unless told otherwise.

---

## Audit Checklist

Use `web_fetch` to retrieve the page HTML, then inspect the source.
Also fetch `/robots.txt` and `/sitemap.xml` from the root domain.
Crawl 3–5 key internal pages if accessible (About, main service page, Contact, Blog).
For items you cannot verify programmatically, note as "Manual check recommended".

---

### 1. Title Tag
- [ ] `<title>` present on every key page
- [ ] Title is unique per page (not duplicated across pages)
- [ ] Length is 50–60 characters — flag if over 60 (Google truncates)
- [ ] Format check: brand name + primary keyword + location modifier
- [ ] Title leads with brand or primary keyword — not a generic descriptor
- [ ] Flag if title is generic (e.g. "Home", "Welcome", or just the domain name)

---

### 2. Meta Descriptions
- [ ] `<meta name="description">` present on the homepage
- [ ] Check all key pages — About, Services, Blog, Team, Contact, FAQ, individual service pages
- [ ] List every page that is missing a meta description (by name/URL)
- [ ] Length 130–160 characters
- [ ] Contains primary keyword and a clear call to action
- [ ] Unique per page — not duplicated

---

### 3. Heading Structure
- [ ] Exactly **one** `<h1>` tag per page — flag duplicates
- [ ] Flag pages with **no H1** at all
- [ ] `<h1>` contains the primary keyword for that page
- [ ] Heading hierarchy is logical: H1 → H2 → H3 (no skipped levels)
- [ ] H2s and H3s use relevant secondary keywords

---

### 4. Keyword Targeting
- [ ] Primary keyword present in: `<title>`, `<h1>`, first paragraph, image alt text
- [ ] Location modifier present where relevant (city/region for local businesses)
- [ ] No keyword stuffing
- [ ] Service pages target specific keywords (e.g. "Invisalign Winnipeg" not just "Invisalign")
- [ ] Flag pages where keyword targeting is weak or generic

---

### 5. Image Optimisation
- [ ] All `<img>` tags have non-empty, descriptive `alt` attributes
- [ ] Alt text includes keyword + brand/location where natural
- [ ] No generic alt text like "image1.jpg" or empty `alt=""`
- [ ] Images have `width` and `height` attributes (prevents layout shift)
- [ ] Flag large unoptimised images — recommend WebP conversion

---

### 6. Internal Linking
- [ ] Key service/product pages linked from homepage and nav
- [ ] Anchor text is descriptive and keyword-rich
- [ ] Flag generic anchor text: "click here", "learn more", "read more"
- [ ] Count and list pages with non-descriptive anchor text
- [ ] No orphan pages (important pages with no internal links pointing to them)
- [ ] Internal links use HTTPS

---

### 7. Structured Data / Schema
- [ ] Check for `<script type="application/ld+json">` blocks
- [ ] Identify schema types present
- [ ] For local businesses: flag if LocalBusiness schema is missing — should include name, address, phone, coordinates, opening hours, price range
- [ ] For service pages: flag missing FAQPage schema (targets "People Also Ask")
- [ ] For blogs: Article schema
- [ ] For products/services: Product + Offer schema
- [ ] Validate JSON-LD is well-formed
- [ ] Recommend: https://search.google.com/test/rich-results

---

### 8. Content Quality & Thin Content
- [ ] Word count per page — flag thin content under 300 words
- [ ] Text-to-HTML ratio: flag pages where code significantly outweighs readable content (common with Elementor, Divi, WPBakery)
- [ ] Service pages should have minimum 400–600 words with FAQs and details
- [ ] Clear call-to-action present on each key page
- [ ] Flag pages that would benefit from FAQ sections

---

### 9. Links
- [ ] No broken or malformed `href` values
- [ ] External links to low-authority or spammy domains (flag if suspicious)
- [ ] All links use HTTPS

---

### 10. URL & Canonicalisation
- [ ] URLs are clean, lowercase, use hyphens not underscores
- [ ] Canonical tag (`<link rel="canonical">`) present on all pages
- [ ] No duplicate content from query strings or pagination
- [ ] HTTPS in use site-wide
- [ ] No trailing slash inconsistency

---

### 11. Technical SEO
- [ ] `robots.txt` accessible — review for accidental disallows
- [ ] `sitemap.xml` accessible
- [ ] `<meta name="robots">` — check for accidental `noindex` or `nofollow`
- [ ] `<html lang="...">` attribute set correctly
- [ ] No render-blocking scripts in `<head>`
- [ ] Favicon present
- [ ] `<meta charset>` and `<meta name="viewport">` present
- [ ] Open Graph tags: `og:title`, `og:description`, `og:image`, `og:url`
- [ ] Twitter Card tags present
- [ ] Note: Check Google Search Console for crawl errors (manual check — advise client)

---

### 12. Page Speed & Performance
- [ ] Flag large or unoptimised images — recommend WebP format
- [ ] Check for heavy page builder markup causing bloated HTML
- [ ] Flag excessive plugins and third-party scripts
- [ ] Recommend: compress images, reduce plugins, implement caching
- [ ] Recommend CDN integration
- [ ] Always link to: https://pagespeed.web.dev/
- [ ] Note: Core Web Vitals (LCP, CLS, FID) require manual tool check

---

### 13. Local SEO Signals
- [ ] NAP (Name, Address, Phone) consistent and present on homepage and contact page
- [ ] Google Business Profile linked or referenced
- [ ] Local keywords used in title, H1, and copy (city + service)
- [ ] Recommend local citations: Yelp, industry directories, local business listings
- [ ] Note star rating and review count if visible in schema or page
- [ ] Recommend prompting customers to leave reviews mentioning specific services and location

---

### 14. WordPress-Specific (if detected)
- [ ] SEO plugin active — Yoast SEO or Rank Math
- [ ] Plugin audit: identify unnecessary plugins adding overhead or script bloat
  - Flag backup plugins if a better solution exists
  - Flag unused tracking/form plugins (recommend GTM instead)
  - Flag RSS feeds if not needed
  - Flag unused activity log plugins
- [ ] Default `?p=123` permalinks in use? (should use post name)
- [ ] Check for duplicate meta tags from theme + plugin conflicts
- [ ] xmlrpc.php exposure (crawl budget + security concern)

---

### 15. Shopify-Specific (if detected)
- [ ] Collection and product pages have unique meta descriptions
- [ ] `/collections/all` — check if indexed (often thin content, consider noindex)
- [ ] Canonical tags on paginated collection pages (`?page=2`)
- [ ] Product image alt text populated
- [ ] Duplicate content between `/products/X` and `/collections/Y/products/X`

---

## Severity Ratings

| Severity | Meaning |
|---|---|
| 🔴 Critical | Directly hurts rankings or blocks indexing |
| 🟠 High | Significant missed opportunity |
| 🟡 Medium | Should fix, moderate impact |
| 🟢 Low | Minor impact |
| ✅ Pass | Working correctly |

---

## Output Format

Always produce the report as a **branded HTML widget** with two sections:

### Cover Page
- "SEO AUDIT REPORT" heading on dark teal (#005F7F) background with cyan (#3AC1CD) diagonal accent
- Client name, website URL, city/location, date
- "Prepared by" footer: show Agency Name and Agency Tagline if provided; leave blank if not

### Report Page
- Score ring out of 100
- Stat grid: Critical / High / Medium / Passing counts
- Summary paragraph (2–3 sentences, most critical issues upfront)
- Findings grouped by severity with colour-coded badges
- Each finding includes: issue name, what was found, why it matters, exact fix instruction
- List affected pages by name/URL where multiple pages share the same issue
- Recommended next steps (phased, max 5–6 steps) on dark teal background footer

### Design Tokens
- Brand colours: `#005F7F` dark teal, `#3AC1CD` cyan, `#EA661B` orange
- Font: Montserrat (Bold 700 headings, 500 subheadings, 400 body)
- Import from Google Fonts

### Report Sections (always include all)
1. Technical SEO Findings
2. Content & Keyword Opportunities
3. Website Speed & Performance
4. Local SEO Signals
5. Plugin Audit (if WordPress/CMS detected)
6. Recommended Next Steps

---

## Execution Steps

1. Ask for URL, client name, city, and date if not provided.
2. Use `web_fetch` to retrieve the full HTML of the homepage.
3. Fetch `/robots.txt` and `/sitemap.xml`.
4. Crawl 3–5 key internal pages if accessible.
5. Work through all 15 checklist sections systematically.
6. Detect CMS from HTML clues (WordPress: `wp-content`, `wp-json`; Shopify: `cdn.shopify.com`).
7. Apply CMS-specific checks.
8. Compile all findings with severity ratings.
9. Produce the branded HTML report.
10. Offer to export as `.docx` or PDF if the user wants to send to the client.

---

## Notes

- Always be specific — quote the exact tag, value, or page name that has a problem.
- List every affected page by name/URL where multiple pages share the same issue.
- Keep tone professional and plain-English — the client may not be technical.
- If a page blocks fetching (403, JS-rendered SPA), note this and advise browser-based tools.
- Always include actionable fix instructions, not just observations.
