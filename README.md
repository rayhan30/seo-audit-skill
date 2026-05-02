# seo-audit-skill

A comprehensive Claude AI skill for auditing websites and generating structured, branded SEO reports.

Built for digital marketing agencies and freelancers who do SEO audits for clients.

---

## What It Does

When installed, this skill allows Claude to:

- Crawl any website URL and audit it across 15 SEO categories
- Produce a fully branded HTML report with cover page, score, findings, and next steps
- Detect CMS automatically (WordPress, Shopify, or generic)
- Identify issues across technical SEO, content, speed, local SEO, schema, and plugins
- List specific affected pages by name/URL — not just generic observations
- Provide exact fix instructions for every issue found

---

## Audit Coverage

| Category | What's Checked |
|---|---|
| Title Tags | Format, length, uniqueness, keyword + location |
| Meta Descriptions | All key pages, length, CTA, uniqueness |
| Heading Structure | H1 count, missing H1, hierarchy |
| Keyword Targeting | Primary keyword in title/H1/alt/copy, location modifiers |
| Image Optimisation | Alt text, descriptiveness, WebP recommendation |
| Internal Linking | Anchor text quality, orphan pages |
| Structured Data | LocalBusiness, FAQPage, Article, Product schema |
| Content Quality | Thin content, text-to-HTML ratio, CTAs |
| Technical SEO | robots.txt, sitemap, canonical, OG tags, viewport |
| Page Speed | Image optimisation, plugin bloat, caching, CDN |
| Local SEO | NAP consistency, citations, reviews |
| WordPress Audit | Plugin audit, SEO plugin, permalink structure |
| Shopify Audit | Collections, product pages, pagination canonicals |

---

## Report Design

The report is generated as a branded HTML widget with:

- **Cover page** — client name, URL, location, date, "Prepared by" (customisable)
- **Score ring** — overall SEO health score out of 100
- **Stat grid** — count of Critical / High / Medium / Passing findings
- **Findings** — colour-coded by severity with fix instructions
- **Next steps** — phased action plan

Brand colours used: `#005F7F` (dark teal), `#3AC1CD` (cyan), `#EA661B` (orange)
Font: Montserrat

---

## Installation

### Claude.ai (Personal Skills)

1. Go to `claude.ai/customize/skills`
2. Click `+` to add a new skill
3. Paste the contents of `seo-audit/SKILL.md`
4. Save — the skill triggers automatically on any SEO audit request

### Claude Code

```bash
# Clone the repo
git clone https://github.com/rayhan30/seo-audit-skill.git

# Copy to your Claude skills directory
cp -r seo-audit-skill/seo-audit ~/.claude/skills/
```

---

## How to Use

Once installed, trigger the skill by saying:

```
Audit this site for SEO: example.com
```

```
Run an SEO report for [Client Name], [URL], [City], [Date]
```

```
/seo-audit
```

Claude will ask for any missing details (client name, location, date) and produce the full branded report.

### Customising the "Prepared by" Section

When running an audit, you can specify your agency:

```
SEO audit for Aura Dental Centre, auradentalcentre.com, Winnipeg MB, April 2026.
Prepared by: Your Agency Name — Your Agency Tagline
```

---

## File Structure

```
seo-audit-skill/
├── README.md
├── LICENSE
└── seo-audit/
    └── SKILL.md
```

---

## Contributing

Pull requests are welcome. If you find a missing SEO check or want to add support for a new CMS, open an issue or submit a PR.

Please keep additions focused — one category per PR where possible.

---

## License

MIT License — see [LICENSE](LICENSE) for details.

---

## Author

Built by [@rayhan30](https://github.com/rayhan30)
