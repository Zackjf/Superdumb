# Know Your Enemy

Research real websites before building anything. Visit 15-25 sites in the niche, study what works, and produce a Site Architecture Brief that defines exactly what pages to build, what content to put on them, and what legal/compliance requirements to meet.

**Run this BEFORE SuperDumb.** Know Your Enemy answers "what to build." SuperDumb answers "how to build it."

---

## When To Use This

Use this whenever someone asks you to:
- Build a website for a business ("make me a dental clinic site in Venezuela")
- Plan the page structure for a new site
- Redesign an existing site's architecture
- Figure out what pages/content a site needs
- Understand what competitors are doing

Do NOT skip this for "simple" sites. A "simple" dental clinic site still needs to know: do competitors show prices? Do they blog? Is WhatsApp or email the primary contact? What legal pages does Venezuelan law require? You can't answer these from training data alone.

---

## The Process

### Phase 1: Discover (find sites to study)

Read `skills/discover-competitors/SKILL.md`.

Search for and compile a list of sites to visit:
- **10-15 direct competitors** — same business type, same or similar market/geography
- **3-5 best-in-class** — top-ranking sites globally for this business type
- **5-10 adjacent businesses** — other local service businesses in the same geography (to understand local web patterns)

### Phase 2: Visit & Analyze (go to each site)

Read `skills/visit-and-analyze/SKILL.md`.

Visit each site and take structured notes on:
- Page inventory (what pages exist)
- Navigation structure
- Conversion mechanisms (CTAs, forms, WhatsApp, booking)
- Trust signals (reviews, credentials, photos)
- Content (blog, FAQ, guides, case studies)
- Legal pages (privacy, terms, disclaimers)
- Mobile experience
- Visual patterns (hero, photography, layout)

### Phase 3: Analyze Patterns

Read the following skills based on what you're analyzing:
- `skills/site-architecture/` — page inventory patterns across all visited sites
- `skills/content-strategy/` — blog, FAQ, guides — what content exists and what ranks
- `skills/conversion-patterns/` — CTAs, forms, contact channels, clicks to conversion
- `skills/legal-and-compliance/` — what legal pages are required for this country + industry

### Phase 4: Identify Opportunities

Read `skills/opportunities/SKILL.md`.

Beyond matching competitors, identify what NOBODY is doing:
- Gaps (useful pages/features no competitor has)
- Bad patterns (things every competitor gets wrong — your chance to stand out)
- Underserved audiences (who visits but isn't served?)
- Content gaps (questions people ask that no site answers)
- Feature ideas (filtered by: does it help the user + is it worth the build cost?)

Separate into: build in v1, defer to later, skip entirely.

### Phase 5: Synthesize

Read `skills/synthesize-brief/SKILL.md`.

Produce a **Site Architecture Brief** — the document that gets handed to SuperDumb (or a human) to start building from.

---

## The Output: Site Architecture Brief

The brief must include ALL of these sections:

### 1. Pages Needed
What pages to build, categorized as:
- **Required** — every successful site has this, you must too
- **Recommended** — most successful sites have this, strong evidence it helps
- **Not needed** — evidence says skip this (e.g., "only 2 of 15 have a blog, none rank for blog content")

Each recommendation must cite the evidence: "12 of 15 sites have individual service pages. Sites with individual pages rank 3x higher than those with a single services list."

### 2. Navigation Architecture
- Number of top-level items (with exact labels from the market)
- CTA in nav? What text?
- Mobile pattern
- Footer links

### 3. Content Strategy
- Blog: yes/no, backed by evidence
- FAQ: yes/no, backed by evidence
- Case studies / testimonials: format and placement
- What content ranks for this niche in Google

### 4. Conversion Patterns
- Primary contact channel (WhatsApp, phone, form, booking system, chat)
- CTA text that competitors use
- Number of form fields on contact forms
- Clicks from homepage to conversion
- Floating/sticky elements

### 5. Trust Signals
- What credentials/certifications are displayed
- Review platforms used
- Photo patterns (real vs stock, team vs facility)
- Social proof (years in business, patient count, etc.)
- Industry-specific trust signals

### 6. Legal & Compliance
- Required legal pages for this country
- Industry-specific disclaimers
- Data protection requirements (GDPR, LGPD, local laws)
- Professional licensing display requirements
- Cookie consent requirements
- Accessibility requirements

### 7. SEO Patterns
- What page types rank for key terms
- Structured data used by top-ranking sites
- Individual vs aggregated pages (e.g., one services page vs many)
- Internal linking patterns
- Content length patterns

### 8. Technical & Platform Patterns
- What platforms are these sites built on
- Page speed benchmarks
- Booking/scheduling systems used
- Payment systems (if applicable)
- Mobile experience quality

### 9. Cultural & Geographic Specifics
- Local contact preferences (WhatsApp vs email vs phone)
- Currency and pricing display norms
- Language considerations (formal vs informal)
- Social platforms that matter locally
- Business hours display norms
- Anything specific to this market that a non-local developer would miss
