# Know Your Enemy — Brainstorm

## What This Is

A plugin that researches real websites in your niche BEFORE any spec or build. When someone says "build me a dental clinic site in Venezuela," the agent visits 10-15 real dental clinic sites (local + international), 5-10 other local business sites (lawyers, salons, doctors), studies what works, and produces a site architecture brief.

The output answers: What pages should this site have? What content goes on each page? Should we have a blog? What CTAs convert? What's the navigation? What trust signals do similar sites use? What does Google reward for this type of site?

## The Core Insight

AI agents build websites from their training data — a fuzzy average of every website they've seen. But the RIGHT website for a dental clinic in Caracas is different from a dental clinic in London. The local market, the platforms people use (WhatsApp vs email), the trust signals that matter (credentials vs reviews), the content that ranks — these are all specific to the niche AND the geography.

Know Your Enemy makes the agent do what a good web designer does: look at 15 real examples before drawing a single wireframe.

## What It Produces

A **Site Architecture Brief** that covers:

### 1. Page Inventory
What pages do successful sites in this niche have?

- Homepage (always)
- Service pages (individual or one list?)
- About page (team bios or company story?)
- Contact page (form, map, WhatsApp, phone?)
- Blog (do sites in this niche blog? What about?)
- FAQ page (do competitors have one? Is it useful?)
- Testimonials/reviews (separate page or embedded?)
- Gallery/portfolio/before-after (relevant for this industry?)
- Location pages (single location or multi-location?)
- Pricing page (do competitors show prices? Should we?)
- Legal pages (privacy, terms — what's required in this market?)
- Landing pages (do competitors have campaign-specific pages?)

The output is: "Based on 15 sites analyzed, here are the pages you need and why."

### 2. Navigation Architecture
How do successful sites organize their nav?

- How many top-level items?
- What are they called? (exact vocabulary from the market)
- Do they use dropdowns/mega-menus or flat nav?
- Is there a CTA in the nav? What does it say?
- Mobile: hamburger, bottom nav, or sticky CTA?
- Footer: what links do they all include?

### 3. Content Strategy
What content do successful sites have beyond their core pages?

- Do they blog? How often? What topics?
- Do they have guides/resources?
- Do they have case studies/success stories?
- Do they have video content?
- Do they have a newsletter?
- What content seems to rank in Google for this niche?
- What questions do people ask (People Also Ask, forums)?

### 4. Conversion Patterns
How do successful sites convert visitors?

- Primary CTA: what is it? Where does it appear?
- Do they use WhatsApp, phone, forms, booking systems, or chat?
- How many clicks from homepage to conversion?
- What trust signals appear near the CTA?
- Is there a floating/sticky CTA?
- Do they gate content or is everything open?

### 5. Trust Signals
What makes visitors trust a site in this niche?

- Credentials/certifications displayed?
- Google reviews embedded?
- Before/after photos?
- Team photos and bios?
- Social proof (patient count, years in business)?
- Professional associations/badges?
- What's culturally specific? (Venezuela: WhatsApp presence matters. US: HIPAA badges matter.)

### 6. SEO Patterns
What does Google reward for this type of site?

- What pages rank for the key terms?
- Do service pages rank individually or does the homepage rank for everything?
- Is there structured data (LocalBusiness, MedicalBusiness, FAQPage)?
- Do sites with blogs rank better than those without?
- What's the typical domain authority range?
- What keywords do the top sites target on each page?

### 7. Visual & Layout Patterns
What do successful sites look like?

- Hero section: image, video, or text-only?
- Color schemes common in this industry
- Photography style (stock vs real, clinical vs warm)
- Page length (short and punchy or long and detailed?)
- Mobile experience quality

### 8. Platform & Tech Patterns
What are these sites built on?

- WordPress, Shopify, Wix, custom?
- Do they use booking systems? Which ones?
- Do they have patient portals?
- What forms/chat widgets do they use?
- What's the page speed like?

---

## Skill Structure

### Phase 1: Discover (find the sites to study)
- Search for "[business type] in [location]"
- Search for "best [business type] website [country]"
- Search for "[business type] near me" from the target location
- Find 10-15 direct competitors (same business type, same/similar market)
- Find 5-10 adjacent businesses (other local service businesses in the same market)
- Find 3-5 "best in class" (the sites that rank #1 globally for this type)

### Phase 2: Visit & Analyze (go to each site)
- Visit homepage — note: hero, nav, CTA, trust signals, page sections
- Visit service/product pages — note: individual vs list, pricing shown?
- Visit about page — note: team bios, credentials, story
- Visit contact page — note: form fields, map, channels
- Check for blog — note: exists? active? topics?
- Check for FAQ — note: exists? useful?
- Check mobile experience
- Note the overall page count and navigation structure

### Phase 3: Synthesize (produce the brief)
- What do ALL successful sites have in common? (table stakes)
- What do the BEST sites do that others don't? (differentiators)
- What do the BAD sites get wrong? (avoid)
- What's specific to this geography/culture?
- Produce the Site Architecture Brief

---

## How It Connects to SuperDumb

```
Know Your Enemy                    SuperDumb
(what pages, what structure)       (how to build each page)

Site Architecture Brief     →     spec-to-ux (wireframe each page)
  - Page inventory          →     know-your-user (confirmed by real sites)
  - Nav architecture        →     manage-cognitive-load (nav structure)
  - Content strategy        →     define-the-task (what each page does)
  - Conversion patterns     →     trust-and-reassurance (CTA placement)
  - Trust signals           →     study-the-landscape (already visited)
  - SEO patterns            →     (feeds keyword/content decisions)
```

Know Your Enemy answers "WHAT to build." SuperDumb answers "HOW to build it."

---

## Example Output (Dental Clinic in Venezuela)

After visiting 15 dental clinic sites + 10 local business sites:

```
SITE ARCHITECTURE BRIEF
Business: Dental clinic in Caracas, Venezuela

PAGES NEEDED (based on 15 sites analyzed):
  Required:
  ✓ Homepage (hero + services preview + trust signals + CTA)
  ✓ Servicios (individual service pages rank better than one list)
  ✓ Nosotros (team with credentials — critical for medical trust)
  ✓ Contacto (WhatsApp primary, form secondary, map, hours)
  ✓ Politica de privacidad (required by Venezuelan law)

  Recommended:
  ◐ Testimonios (8 of 15 sites have them, those 8 rank higher)
  ◐ Preguntas frecuentes (6 of 15 have FAQ, captures long-tail traffic)
  ◐ Galeria antes/despues (5 of 15, high engagement for dental)

  Not needed:
  ✗ Blog (only 3 of 15 have active blogs, none rank for blog content)
  ✗ Patient portal (0 of 15 local clinics have this)
  ✗ Booking calendar (0 of 15 — all use WhatsApp/phone)
  ✗ Newsletter (0 of 15 — nobody subscribes to dental newsletters)

NAVIGATION (consensus from top 5 sites):
  Inicio | Servicios | Nosotros | Contacto | [Agendar cita →]
  5 items max. CTA button in nav. No dropdowns.

CONVERSION (what works):
  - 12 of 15 sites use WhatsApp as primary contact
  - 8 of 15 have a floating WhatsApp button
  - Average clicks to contact: 1.5
  - Top CTA text: "Agendar cita" (7 sites), "Contactanos" (4 sites)
  - Forms that convert: name + phone + service needed (3 fields)

TRUST SIGNALS (what the top-ranking sites show):
  - Doctor credentials + university (15 of 15)
  - Real clinic photos (12 of 15 — stock photos correlate with lower ranking)
  - Years of experience (10 of 15)
  - Google Reviews widget (8 of 15)
  - Before/after photos (5 of 15, all in top half of rankings)
  - Professional association badges (4 of 15)

SEO INSIGHTS:
  - Individual service pages outrank single service lists
  - "dentista en [zona]" is the primary keyword pattern
  - Sites with FAQ pages capture 3x more long-tail keywords
  - Structured data (LocalBusiness + MedicalBusiness) present on top 3
  - Average page speed of top 5: 2.1s. Average of bottom 5: 6.8s.

CULTURAL/LOCAL:
  - Prices shown in USD (12 of 15) — standard in Venezuela
  - WhatsApp is THE contact method, not a secondary option
  - Instagram linked on 14 of 15 (more important than Facebook)
  - Business hours prominently displayed (patients check if open today)
  - "Emergencias" section on 8 of 15 sites (dental emergencies are common)
```

---

## Open Questions

1. How many sites should it visit? 15 direct + 10 adjacent = 25 seems right for thorough research. Too few = not representative. Too many = diminishing returns.

2. Should it use Ahrefs/SEOGets MCP for the SEO analysis, or just observe what ranks?

3. Should it produce the brief as a standalone document, or feed directly into SuperDumb's gates?

4. Should it save the raw research (each site's notes) or just the synthesized brief?

5. Should it look at Google Business profiles too? (Reviews, photos, Q&A — rich source of voice-of-customer data for local businesses)

6. Time budget: a full research pass with 25 site visits could take a while. Should there be a "quick" mode (5 sites, 5 minutes) and "deep" mode (25 sites, full analysis)?
