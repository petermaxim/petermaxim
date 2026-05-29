---
name: seo
description: "Comprehensive SEO analysis for any website or business type. Full site audits, single-page analysis, technical SEO (crawlability, indexability, Core Web Vitals with INP), schema markup, content quality (E-E-A-T), image optimization, sitemap analysis, and GEO for AI Overviews/ChatGPT/Perplexity. Industry detection for SaaS, e-commerce, local, publishers, agencies. Triggers on: SEO, audit, schema, Core Web Vitals, sitemap, E-E-A-T, AI Overviews, GEO, technical SEO, content quality, page speed, structured data."
user-invocable: true
argument-hint: "[command] [url]"
---

# SEO: Universal SEO Analysis Skill

**Invocation:** `/seo [command] [url]`

Comprehensive SEO analysis across all industries (SaaS, local services, e-commerce, publishers, agencies). Orchestrates 13 sub-skills and 8 subagents.

## Quick Reference

| Command | What it does |
|---------|-------------|
| `/seo audit <url>` | Full website audit with parallel subagent delegation |
| `/seo page <url>` | Deep single-page analysis |
| `/seo sitemap <url>` | Analyze or generate XML sitemaps |
| `/seo schema <url>` | Detect, validate, and generate Schema.org markup |
| `/seo content <url>` | E-E-A-T and content quality analysis |
| `/seo content-brief <topic>` | Generate detailed SEO content brief |
| `/seo geo <url>` | AI Overviews / Generative Engine Optimization |
| `/seo plan <business-type>` | Strategic SEO planning |
| `/seo competitor <url>` | Competitor gap analysis |
| `/seo technical <url>` | Technical SEO audit (9 categories) |
| `/seo local <url>` | Local SEO analysis (GBP, citations, reviews, map pack) |

## SEO Health Score (0-100)

Weighted aggregate across 7 categories:

| Category | Weight |
|----------|--------|
| Technical SEO | 22% |
| Content Quality | 23% |
| On-Page SEO | 20% |
| Schema / Structured Data | 10% |
| Performance (CWV) | 10% |
| AI Search Readiness | 10% |
| Images | 5% |

## Priority Levels

- **Critical**: Blocks indexing or causes penalties — fix immediately
- **High**: Significantly impacts rankings — fix within 1 week
- **Medium**: Optimization opportunity — fix within 1 month
- **Low**: Nice to have — backlog

## Orchestration Logic (for `/seo audit`)

1. Detect business type (SaaS, local, ecommerce, publisher, agency)
2. Run parallel analysis:
   - Technical SEO (crawlability, indexability, Core Web Vitals)
   - Content quality (E-E-A-T, readability, thin content)
   - Schema (detection, validation, generation)
   - Sitemap (structure, coverage)
   - Performance (Core Web Vitals with INP)
   - GEO (AI crawler access, citability, brand signals)
3. If local business detected → add Local SEO analysis
4. Collect results → unified SEO Health Score (0-100)
5. Generate prioritized action plan

## Industry Detection

- **SaaS**: pricing page, /features, /integrations, "free trial", "sign up"
- **Local Service**: phone number, address, service area, "serving [city]"
- **E-commerce**: /products, /cart, "add to cart", product schema
- **Publisher**: /blog, /articles, author pages, publication dates
- **Agency**: /case-studies, /portfolio, client logos

## Technical SEO Checklist

### Crawlability & Indexability
- [ ] robots.txt exists and is correct
- [ ] XML sitemap present and submitted to Search Console
- [ ] No accidental noindex on key pages
- [ ] Canonical tags correct (no self-referential canonicals pointing elsewhere)
- [ ] Redirect chains ≤ 2 hops
- [ ] No broken internal links (4xx)

### Core Web Vitals (INP, not FID)
- [ ] LCP < 2.5s
- [ ] INP < 200ms (Interaction to Next Paint — replaces FID)
- [ ] CLS < 0.1
- [ ] TTFB < 800ms

### On-Page SEO
- [ ] Title tag: 50-60 characters, keyword near front
- [ ] Meta description: 150-160 characters, compelling CTA
- [ ] H1: one per page, matches search intent
- [ ] Heading hierarchy logical (H1 → H2 → H3)
- [ ] Images: descriptive alt text, WebP format, explicit width/height

## Schema.org Quick Reference

| Schema Type | Use Case |
|------------|----------|
| Organization | Brand identity, logo, social profiles |
| WebSite | Sitelinks search box |
| Article / BlogPosting | Blog content, news |
| Product | E-commerce items |
| LocalBusiness | Physical locations |
| BreadcrumbList | Navigation path |
| FAQPage | Government and healthcare only (Aug 2023) |

**Never use HowTo schema** — deprecated September 2023.

## E-E-A-T Scoring

Score content on:
- **Experience**: First-hand use, case studies, real examples
- **Expertise**: Author credentials, depth of coverage, accuracy
- **Authoritativeness**: Backlinks from authoritative sources, citations
- **Trustworthiness**: Accuracy, transparency, security (HTTPS)

## GEO: AI Overview Optimization

For AI Overviews, ChatGPT citations, and Perplexity visibility:
- [ ] llms.txt present and comprehensive
- [ ] Entity markup complete (Organization, Person, Product)
- [ ] Concise, direct answers to target queries in page content
- [ ] Structured data complete and valid
- [ ] Brand mentioned alongside category keywords
- [ ] Author pages with verifiable credentials

## Content Quality Gates

- Thin content warning: < 300 words for non-listing pages
- Location pages: enforce 60%+ unique content
- HARD STOP at 50+ near-duplicate location pages without justification
- All Core Web Vitals use INP, never FID (deprecated March 2024)

## Error Handling

| Scenario | Action |
|----------|--------|
| Unrecognized command | List available commands, suggest closest match |
| URL unreachable | Report error, ask user to verify URL |
| Ambiguous business type | Present top 2 types with signals, ask user to confirm |
