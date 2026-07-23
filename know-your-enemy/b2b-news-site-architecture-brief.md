# Site Architecture Brief: B2B Industry News Publication

## Business Type
B2B industry news/media publication (online-first)

## Research Summary
- 8 B2B news publications visited and analyzed
- Sites span SEO, ad tech, tech/startup, business news, and European startup verticals
- Each site was analyzed across homepage, article pages, about/trust pages, advertising pages, newsletter pages, events pages, and legal/policy pages

### Sites Analyzed
| # | Site | Vertical | Revenue Model |
|---|------|----------|---------------|
| 1 | Search Engine Land | SEO/Search Marketing | Ads + Events + Sponsored Content |
| 2 | Search Engine Journal | SEO/Digital Marketing | Ads + Sponsored Content + Webinars + Ebooks |
| 3 | TechCrunch | Tech/Startups | Ads + Events + Brand Studio + Newsletters |
| 4 | The Information | Tech (premium) | Subscription-first (hard paywall) |
| 5 | Morning Brew | Business/General | Newsletter-first + Ads + Events |
| 6 | AdExchanger | Ad Tech | Ads + Events (Programmatic I/O) |
| 7 | Digiday | Media/Marketing | Freemium (Digiday+) + Ads + Events + Awards |
| 8 | Sifted | European Startups | Freemium (Sifted Pro) + Ads + Events + Data Products |

---

## 1. Pages Needed

### Required (Table Stakes) — Present on 7-8 of 8 sites

| Page | Evidence | Notes |
|------|----------|-------|
| **Homepage** | 8/8 | Hero/featured story + latest news feed + category navigation + newsletter CTA. All sites lead with news recency. |
| **Article pages** | 8/8 | Author byline + date + share buttons + related articles + newsletter CTA. The core product. |
| **Category/topic archive pages** | 8/8 | Every site organizes content by topic (SEO, AI, Fintech, etc.). These are both navigation hubs and SEO entry points. |
| **About page** | 7/8 (AdExchanger's was thin) | Mission statement, founding story, team/leadership list. This is where editorial credibility lives. |
| **Newsletter signup page** | 8/8 | Dedicated page or prominent inline signup. Every single site makes newsletter acquisition a top priority. |
| **Contact page** | 8/8 | Contact form or email addresses for editorial tips, advertising inquiries, and general questions. |
| **Privacy policy** | 8/8 | Standard legal requirement. All sites have one. |
| **Terms of service/use** | 8/8 | Standard legal page. |
| **Advertising/sponsorship page** | 7/8 | "Advertise with us" page — either a media kit page with audience stats (SEJ) or a lead-gen form (Digiday). Required for ad-supported sites. |
| **Events page** | 7/8 | Conferences, webinars, summits. Events are a major revenue stream for B2B news. |
| **Author/contributor pages** | 7/8 | Individual author bio pages with photo, social links, and article archive. Critical trust signal. |
| **Search** | 8/8 | Site-wide search functionality in the header. |

### Recommended — Present on 4-6 of 8 sites

| Page | Evidence | Notes |
|------|----------|-------|
| **Podcast page/section** | 6/8 (TechCrunch, Morning Brew, Digiday, Sifted, SEJ, AdExchanger) | Dedicated podcast landing with episodes, platforms (Apple, Spotify, YouTube). Growing content format. |
| **Webinar archive/registration** | 5/8 (SEL, SEJ, Digiday, AdExchanger, Sifted) | Webinar pages serve dual purpose: content + lead generation + sponsorship revenue. |
| **Subscription/membership page** | 4/8 (The Information, Digiday, Sifted, TechCrunch) | Premium tier page with pricing, benefits, and CTA. Only needed if using freemium or paywall model. |
| **Awards page** | 3/8 (Digiday, SEL, SEJ) | Industry awards programs are both a trust builder and a revenue line (entry fees, sponsorships). |
| **Careers page** | 5/8 | Signals organizational maturity. Links to open positions. |
| **Editorial guidelines / contributor guidelines** | 4/8 (SEL, SEJ explicitly published) | Guest post policies, content standards, AI content policies. Important for publications accepting contributions. |
| **Masthead page** | 3/8 (Digiday, SEJ, Morning Brew) | Full editorial team listing separate from About page. Shows editorial depth. |
| **Cookie policy** | 5/8 (especially European-facing sites) | Separate from privacy policy. GDPR-required for EU audiences. |
| **Research/reports section** | 4/8 (Digiday, Sifted, SEJ, SEL) | Proprietary data, industry reports, surveys. Can be gated for lead gen or premium. |
| **Job board** | 2/8 | Niche job boards (industry-specific listings). Revenue opportunity but rare. |

### Differentiator Opportunities — Present on 1-3 of 8 sites

| Page | Evidence | Notes |
|------|----------|-------|
| **AI Code of Conduct** | 1/8 (Sifted) | Forward-thinking trust signal. States how publication uses (or doesn't use) AI in editorial. |
| **Data products/trackers** | 1/8 (Sifted: Deals Tracker, Investor Rankings, Market Maps) | Proprietary data tools as premium product. High-value differentiator. |
| **Corrections/transparency page** | 0/8 explicitly | Major gap across all sites. None had a dedicated corrections policy page, though some reference accuracy in About pages. Opportunity. |
| **Glossary/WTF explainers** | 1/8 (Digiday "WTF Series") | Accessible explainer content for newcomers. SEO gold + audience builder. |
| **Interactive games** | 1/8 (Morning Brew) | Engagement/retention tool. Novel for B2B but drives daily visits. |
| **Community (Slack/Discord)** | 0/8 visible | No site had a visible community platform. All are one-to-many broadcast. Potential differentiation. |
| **Sister publication cross-links** | 3/8 (Digiday/Glossy/ModernRetail, Morning Brew's 9+ newsletters, SEL/MarTech) | Portfolio approach: multiple verticals under one media company. |

### Not Needed — Skip These

| Page | Evidence | Why Skip |
|------|----------|---------|
| **Comments/forum system** | 0/8 have active comments | Every site has disabled or never built comments. Comments on B2B news are dead. Social media is where discussion happens. |
| **User registration (non-premium)** | 1/8 | Only needed if you have a paywall. Free-access sites don't require registration. |
| **Photo galleries** | 0/8 | Not relevant for B2B news. |
| **E-commerce/shop** | 0/8 (Morning Brew has minor merch) | Not a revenue line for B2B news sites. |

---

## 2. Navigation Architecture

### Primary Navigation Structure

**Evidence-based pattern (averaged across 8 sites):**

| Position | Label Pattern | Evidence |
|----------|--------------|---------|
| 1 | Latest / News / Home | 7/8 lead with recency |
| 2-5 | Topic categories (2-4 items) | 8/8 organize by topic. Examples: "SEO, PPC, AI" or "Media, Marketing, Ad Tech" |
| 6 | Content formats link | 5/8 have "Podcasts" or "Resources" in nav |
| 7 | Events | 7/8 have events in primary nav |
| 8 | Premium/Subscribe | 4/8 (those with paywall: "Digiday+", "Sifted Pro") |
| CTA button | Subscribe / Newsletter | 7/8 have a subscribe CTA in the header |

**Average top-level nav items: 6-8**

### Recommended Navigation

```
[Logo] News | [Topic 1] | [Topic 2] | [Topic 3] | Podcasts | Events | [Subscribe Button]
```

**Mega menu / dropdown pattern:** 6/8 sites use dropdown menus revealing subcategories. Search Engine Journal has the most extensive with subcategories under each topic (e.g., under SEO: Enterprise, Local, Technical, Link Building). TechCrunch uses a mega menu with 30+ categories. Recommendation: use dropdowns with 4-8 subcategories per topic.

**Utility nav (secondary bar):** 4/8 have a secondary nav bar above or below the primary with: Search, Login/Account, Newsletter link, Social icons.

**Mobile:** 8/8 use hamburger menu. No site uses bottom nav.

### Footer Structure

Every site's footer contains (8/8):
- Company links: About, Careers, Contact, Advertise
- Legal links: Privacy Policy, Terms of Service, Cookie Policy
- Social media icons (LinkedIn, X/Twitter, Facebook, YouTube, Instagram — LinkedIn and X most common)
- Newsletter signup (repeated from header/body)
- Sister publication links (if applicable)
- Copyright notice

---

## 3. Content Strategy

### Content Types (by prevalence)

| Content Type | Prevalence | Notes |
|-------------|------------|-------|
| **Breaking news** | 8/8 | Short-form, timestamped, rapid publication. The bread and butter. |
| **Analysis/deep dives** | 8/8 | Longer-form pieces interpreting what news means. Higher value. |
| **How-to/tactical guides** | 5/8 (SEL, SEJ, Digiday, Sifted, Morning Brew) | Evergreen instructional content. Strong SEO performer. |
| **Opinion/columns** | 6/8 | Named columns with regular contributors (e.g., "Data-Driven Thinking" on AdExchanger, "Ask an SEO" on SEJ). |
| **Interviews** | 5/8 | Q&A format with industry leaders. |
| **Sponsored content** | 7/8 | Clearly labeled. Separate from editorial. Major revenue stream. |
| **Podcast episodes** | 6/8 | Audio content with show notes and transcript links. |
| **Webinar recordings** | 5/8 | Gated or open webinar replays. |
| **Research/data reports** | 4/8 | Proprietary surveys, data analysis. Can be premium-gated. |
| **Newsletters (web archive)** | 4/8 | Morning Brew and TechCrunch archive newsletter editions as web content. |
| **Event coverage** | 5/8 | Recaps, live blogs, interviews from industry events. |
| **Explainers/glossary** | 2/8 | "WTF is..." series (Digiday), "What is SEO" guides (SEL). |

### Content Organization

**Primary axis: Topic/vertical (8/8)**
Every site organizes first by topic — SEO, AI, Fintech, Media, Marketing, etc. This is the dominant navigation paradigm.

**Secondary axis: Recency (8/8)**
Within topics, content is sorted newest-first. "Latest" is always the default view.

**Tertiary axis: Format (4/8)**
Some sites allow filtering by content format (news, analysis, guides, podcasts). This is less common but growing.

**Tagging system:** 7/8 use tags/categories for cross-referencing. Articles typically have 1 primary category and 1-3 tags.

### Article Page Structure (Standard Components)

Based on analysis of article pages across all sites:

| Component | Prevalence | Position |
|-----------|------------|----------|
| Headline (H1) | 8/8 | Top |
| Author name + photo | 8/8 | Below headline |
| Publication date/time | 8/8 | Below headline |
| Category/topic label | 7/8 | Above or below headline |
| Share buttons (LinkedIn, X, Facebook, Reddit) | 7/8 | Below headline and/or floating sidebar |
| Article body | 8/8 | Main column |
| In-article newsletter CTA | 7/8 | Mid-article or end-of-article |
| Related articles | 8/8 | Below article |
| Author bio box | 6/8 | End of article |
| Ad placements | 7/8 | Leaderboard top, sidebar, mid-article |
| "Trending" or "Most Read" sidebar | 5/8 | Right sidebar |
| Read time estimate | 3/8 (SEJ, others) | Below headline |
| Paywall gate | 3/8 | Mid-article cutoff |

---

## 4. Monetization / Revenue Pages

### Revenue Streams (by prevalence)

| Revenue Stream | Prevalence | Implementation |
|----------------|------------|----------------|
| **Display advertising** | 7/8 | Google Ad Manager / programmatic ads. Multiple placements: leaderboard (728x90), sidebar (300x250), mid-article, sticky footer. Heavy ad load. |
| **Sponsored content** | 7/8 | Clearly labeled "Sponsored" articles. Separate from editorial. Some have a "Brand Studio" (TechCrunch) or "Sponsored" section. |
| **Events (conferences/summits)** | 7/8 | Major revenue line. Digiday runs 9+ events/year. AdExchanger runs Programmatic I/O. SEL runs SMX. Registration fees + sponsor packages. |
| **Newsletter sponsorship** | 6/8 | Monetizing newsletter via sponsored slots within emails. |
| **Webinar sponsorship** | 5/8 | Co-branded webinars with sponsors. Lead gen for sponsors. |
| **Premium subscription** | 4/8 | The Information (hard paywall ~$400/yr), Digiday+ (membership), Sifted Pro (premium tier), TechCrunch (partial). |
| **Research/reports (gated)** | 4/8 | Proprietary research sold or used for lead gen. |
| **Awards programs** | 3/8 | Entry fees from nominees + event sponsorship. |
| **Data products** | 1/8 | Sifted's trackers (Deals, Investor, M&A, Market Maps). Emerging model. |
| **Job board** | 1/8 | Niche industry job listings. Low prevalence but potential. |

### Advertising Page Patterns

**SEJ model (most detailed):**
- Audience stats prominently displayed: 1.5M pageviews, 1M sessions, 710K users, 79K newsletter subscribers
- Product menu: Banner ads, sponsored articles, webinars, ebooks, dedicated email, branded categories, hello bar, takeovers
- "Plan My Campaign" CTA with form
- Case study results from past campaigns
- Media kit available on request

**Digiday model (lead-gen form):**
- Simple form asking: company type, advertising goals (brand awareness, lead gen, networking), industry
- No public pricing, no traffic stats
- Sales team follows up

**Recommendation:** Build an advertising page with audience stats, product descriptions, and a "Download Media Kit" or "Get in Touch" CTA. Don't publish pricing (no site does).

---

## 5. Newsletter Strategy

### Newsletter Prominence (critical pattern)

Newsletter signup is the single most promoted conversion action across all 8 sites. Every site treats email acquisition as a primary business objective.

| Placement | Prevalence |
|-----------|------------|
| Header/nav bar signup link or button | 7/8 |
| Dedicated newsletter landing page | 8/8 |
| In-article inline CTA (mid or end of article) | 7/8 |
| Homepage prominent section | 6/8 |
| Footer signup | 6/8 |
| Popup/modal | 2/8 (less common now) |

### Newsletter Offerings

| Pattern | Example | Prevalence |
|---------|---------|------------|
| **Daily digest** | Morning Brew Daily, Digiday daily, SEJ Today | 7/8 |
| **Topic-specific newsletters** | TechCrunch Mobility, TechCrunch Startups Weekly, Sifted sector newsletters | 4/8 |
| **Weekly roundup** | TechCrunch Week in Review | 4/8 |
| **Multiple newsletters** | TechCrunch offers 8, Morning Brew has 9+ brands, Sifted offers sector-specific | 5/8 |

### What They Promise

Common value propositions:
- "Become smarter in just 5 minutes" (Morning Brew)
- "Get the news that impacts your business, delivered weekday mornings" (SEJ)
- "Get Digiday's top stories every morning in your email inbox" (Digiday)

**Pattern:** Time-efficient + daily + professionally relevant. Always emphasize brevity and business value.

### Recommendation

1. Launch with one daily newsletter
2. Place signup in: header, mid-article, end-of-article, dedicated page, and footer
3. Promise a specific time commitment ("3-minute read") and frequency ("every weekday morning")
4. Show subscriber count once it's meaningful (SEJ shows "75,000+ subscribers")
5. Expand to topic-specific newsletters once audience is large enough

---

## 6. Trust & Editorial Pages

### Trust Signals (by prevalence)

| Signal | Prevalence | Notes |
|--------|------------|-------|
| **Author bylines with photos** | 8/8 | Non-negotiable. Every article has a named author with headshot. |
| **Author bio pages** | 7/8 | Individual pages listing author's role, bio, social links, and article archive. |
| **Publication age/founding year** | 6/8 | SEL shows "20 years" badge. SEJ founded 2003. AdExchanger founded 2008. Longevity = trust. |
| **About page with mission** | 7/8 | Mission statement, editorial values, team listing. |
| **Social media presence links** | 8/8 | LinkedIn and X/Twitter universal. Also: YouTube, Facebook, Instagram, Mastodon, Bluesky, Threads. |
| **Parent company disclosure** | 6/8 | SEL owned by Semrush/Third Door Media, SEJ by Alpha Brand Media, TechCrunch by Yahoo. |
| **Sponsored content labeling** | 7/8 | All sites that run sponsored content clearly label it "Sponsored" or "Partner Content". |
| **Editorial guidelines** | 4/8 (SEL, SEJ explicitly) | Guest post guidelines, content quality standards, AI content policies. |
| **Corrections policy** | 1/8 (SEL mentions accuracy commitment in About) | Major gap industry-wide. Opportunity for differentiation. |
| **Editorial independence statement** | 2/8 (SEL, SEJ in About pages) | Stating editorial is independent from advertising/ownership. Rare but valuable. |
| **AI usage policy** | 1/8 (Sifted: "AI Code of Conduct") | Emerging trust signal. States how AI is/isn't used in editorial. |

### Recommended Trust Pages

Build these in order of priority:

1. **About page** — Mission, founding story, editorial values, team photos and bios, parent company disclosure
2. **Author pages** — Individual bio pages with article archive, social links, credentials
3. **Editorial policy** — Corrections process, sponsored content disclosure, editorial independence statement, AI policy
4. **Masthead** — Full team listing with titles and contact info
5. **Advertising disclosure** — How sponsored content is labeled, separation of editorial and advertising

---

## 7. Legal & Compliance Pages

### Required Legal Pages

| Page | Prevalence | Requirement Level |
|------|------------|------------------|
| **Privacy Policy** | 8/8 | Legally required in virtually all jurisdictions |
| **Terms of Service / Terms of Use** | 8/8 | Standard for any website |
| **Cookie Policy** | 5/8 | Required for EU audiences (GDPR). Can be section within Privacy Policy. |
| **Cookie consent banner** | 6/8 | Required under GDPR for EU visitors. Sifted implements detailed GDPR-first consent with default "denied" for ad personalization. |
| **CCPA/CPRA notice** | 5/8 | Required for California users. "Do Not Sell My Personal Information" link. |
| **Advertising/sponsorship disclosure** | 3/8 explicit | FTC requires disclosure for sponsored content. Usually handled via "Sponsored" labels on articles rather than a separate page. |
| **RSS Terms** | 1/8 (TechCrunch) | Niche. Only needed if RSS is a significant distribution channel. |

### Privacy Policy Structure (based on SEJ's comprehensive example)

1. Introduction — what data is collected
2. Data collection methods — automatic (cookies, analytics) and voluntary (forms, signups)
3. Usage purposes — content delivery, marketing, analytics
4. Third-party sharing — ad networks, analytics providers, identity partners
5. Cookie classifications — required, performance, functionality, targeting
6. User rights — access, deletion, modification, opt-out
7. Regional compliance — GDPR section, CCPA section
8. Contact information — privacy inquiries

### GDPR Considerations (especially for EU-facing publications)

Sifted (EU-based) implements:
- Default denied consent for ad personalization and storage
- Detailed cookie consent management
- OneTrust-style consent management platform
- Separate cookie policy page

**Recommendation:** Implement cookie consent management (OneTrust, Cookiebot, or similar) with granular consent options. EU audiences expect this.

---

## 8. Events & Community

### Events (Major Revenue Stream)

| Aspect | Pattern |
|--------|---------|
| **Event types** | Conferences (multi-day), summits (1-2 days), webinars (virtual, 1 hour), workshops/masterclasses |
| **Frequency** | Major conferences: 1-3/year. Webinars: monthly or more. Digiday runs 9+ events/year. |
| **Revenue model** | Attendee tickets + sponsor packages. Webinars often free (sponsor-funded, lead gen). |
| **Promotion** | Dedicated nav item, homepage banners, newsletter promotion, article-adjacent CTAs |
| **Brands** | Named event series: SMX (SEL), Programmatic I/O (AdExchanger), Publishing Summit (Digiday), Sifted Summit |

### Community Features

| Feature | Prevalence | Notes |
|---------|------------|-------|
| Active comments | 0/8 | Every site has either disabled or never built comments. B2B news discussion has moved entirely to LinkedIn and X. |
| Social sharing | 7/8 | Share buttons on articles (LinkedIn, X, Facebook, Reddit most common) |
| Push notifications | 2/8 | OneSignal or similar for breaking news alerts |
| Community platform (Slack/Discord) | 0/8 | No site has a visible owned community. Potential opportunity but resource-intensive. |
| Member-exclusive events | 2/8 (Digiday, Sifted) | Premium subscribers get access to exclusive networking events |

---

## 9. SEO & Technical Patterns

### Structured Data

| Schema Type | Prevalence |
|-------------|------------|
| Article schema | 8/8 |
| Organization schema | 8/8 |
| BreadcrumbList | 5/8 |
| CollectionPage (for archives) | 4/8 |
| Person (for authors) | 3/8 |

### URL Patterns

- Article URLs: `/topic/article-slug` or `/article-slug-12345` (with numeric ID)
- Category URLs: `/category/topic-name/` or `/topic/`
- Author URLs: `/author/author-name/`
- Tag URLs: `/tag/tag-name/`

### Content Organization for SEO

- Individual topic/category archive pages act as SEO hubs
- Evergreen guides rank for high-volume informational queries
- News articles capture trending/breaking queries
- Author pages build E-E-A-T signals

### Platform Distribution

| Platform | Count |
|----------|-------|
| WordPress | 5/8 (SEL, SEJ, AdExchanger, Digiday + variant, TechCrunch) |
| Custom CMS | 2/8 (The Information, Morning Brew) |
| Headless/Next.js | 1/8 (Sifted) |

WordPress dominates B2B news publishing. Most use heavily customized themes with enterprise-grade plugins for advertising, membership, and newsletter management.

---

## 10. Key Patterns & Opportunities

### What ALL successful B2B news sites share (do these first)

1. **News-first homepage** — latest stories front and center, organized by topic
2. **Named authors on every piece** — byline + photo + bio page
3. **Newsletter as primary conversion** — multiple placements, clear value prop, daily frequency
4. **Topic-based navigation** — organize by industry vertical, not by content format
5. **Advertising as core revenue** — display ads + sponsored content + newsletter sponsorship
6. **Events section** — conferences and/or webinars as second revenue stream
7. **Clear sponsored content labeling** — trust depends on editorial/commercial separation
8. **Social distribution** — LinkedIn and X/Twitter as primary channels

### Gaps and Opportunities (what nobody does well)

1. **Corrections/transparency page** — 0/8 have a dedicated corrections policy. Building one signals editorial integrity.
2. **AI editorial policy** — Only 1/8 (Sifted) has an AI Code of Conduct. As AI becomes standard tooling, this will become expected.
3. **Owned community** — 0/8 have Slack/Discord communities. Discussion happens on LinkedIn/X instead. An owned community could be a membership differentiator.
4. **Accessible content formats** — Few sites offer audio versions of articles, dark mode, or adjustable text sizes. Accessibility as a feature.
5. **Data products** — Only 1/8 (Sifted) offers proprietary data trackers. Original data is a high-value premium product.
6. **Interactive/calculator tools** — 0/8 offer interactive tools beyond Sifted's trackers. Industry-specific calculators or benchmarking tools could drive recurring visits.
7. **Journalist credential verification** — No site visibly verifies or badges journalist credentials. In an era of content farms, verified expertise is a trust signal.
8. **Reader advisory board** — No site advertises a reader advisory board or reader ombudsman. Opportunity for trust differentiation.

---

## Recommended Build Order

### V1 (Launch)
- Homepage (latest news + featured + topic sections + newsletter CTA)
- Article page template (byline, date, share, related, newsletter CTA, ads)
- 3-5 topic category pages
- About page (mission, team, values)
- Author bio pages
- Newsletter signup (dedicated page + inline components)
- Contact page
- Privacy policy
- Terms of service
- Advertising inquiry page ("Advertise with Us")

### V2 (Month 2-3)
- Events page
- Podcast page
- Editorial policy / corrections page
- Cookie policy + consent management
- Search functionality
- Sponsored content template (labeled, separated from editorial)
- Webinar registration pages

### V3 (Month 4-6)
- Premium/membership tier (if pursuing freemium model)
- Research/reports section
- Awards program page
- AI editorial policy
- Multiple topic-specific newsletters
- Job board (if industry demand exists)
- Data products/trackers (if proprietary data is available)

---

## Summary Table

| Category | Table Stakes (build now) | Recommended (build soon) | Skip |
|----------|-------------------------|--------------------------|------|
| **Pages** | Homepage, Articles, Categories, About, Contact, Newsletter, Privacy, Terms, Advertise, Author pages | Events, Podcast, Editorial policy, Careers, Cookie policy, Research | Comments, Forums, Photo galleries, E-commerce |
| **Navigation** | 6-8 top items, topic-based, subscribe CTA, hamburger mobile | Mega menu, secondary nav bar, search | Bottom nav |
| **Content** | News, Analysis, Guides | Opinion columns, Interviews, Sponsored, Podcasts, Webinars, Research | User-generated, Forums |
| **Revenue** | Display ads, Sponsored content, Newsletter sponsorship | Events, Webinar sponsorship, Premium subscription | Job board (maybe later), E-commerce |
| **Trust** | Author bylines, About page, Sponsored labeling | Editorial policy, Corrections process, AI policy | User reviews, Third-party badges |
| **Legal** | Privacy policy, Terms of service | Cookie policy, CCPA notice, Ad disclosure | RSS terms |
| **Newsletter** | Daily digest, Header/footer/inline CTAs | Topic-specific newsletters, Subscriber count social proof | Popup modals (declining pattern) |

---

## Next Steps

Hand this brief to a developer or site builder to:
1. Build page templates for the V1 page list
2. Implement the navigation architecture
3. Set up newsletter infrastructure (email service provider + signup forms)
4. Configure ad placements (leaderboard, sidebar, mid-article)
5. Create the editorial workflow for article publishing
6. Implement the article page template with all standard components
