# Know Your Enemy

Research real websites before building anything.

When someone says "build me a dental clinic site in Venezuela," don't start coding. Start by visiting 15-25 real dental clinic websites — local competitors, international best-in-class, and adjacent local businesses — to understand what works, what's missing, and what pages actually need to exist.

**Run this BEFORE [SuperDumb](https://github.com/Zackjf/Superdumb).** Know Your Enemy answers "what to build." SuperDumb answers "how to build it."

---

## The Problem

AI agents build websites from training data — a fuzzy average of every site they've seen. But the right website for a dental clinic in Caracas is different from one in London. The local contact channels (WhatsApp vs email), trust signals (credentials vs reviews), content that ranks, legal requirements, and cultural norms are all specific to the niche AND geography.

Without research, agents build generic sites that miss what actually works in the market.

## What It Does

Visits 15-25 real websites, takes structured notes, and produces a **Site Architecture Brief** covering:

1. **Pages needed** — what to build, what to skip, backed by evidence ("12 of 15 have individual service pages")
2. **Navigation** — structure, labels (in the local language), CTA placement
3. **Content strategy** — blog or no blog, FAQ, case studies, video — based on what ranks
4. **Conversion patterns** — primary contact channel, CTA copy, form fields, clicks to contact
5. **Trust signals** — credentials, reviews, photos, social proof that matters in this market
6. **Legal & compliance** — required pages by country + industry (privacy, terms, disclaimers, licensing)
7. **SEO patterns** — what page types rank, structured data, keyword patterns
8. **Opportunities** — gaps nobody fills, bad patterns to beat, features worth building
9. **Cultural specifics** — local contact preferences, currency, language, social platforms

## The Flow

```
Know Your Enemy          →  SuperDumb           →  Code
(what pages to build)       (how to build them)    (the product)

Site Architecture Brief  →  spec-to-ux          →  implementation
                         →  simplify-the-spec
                         →  know-your-user
```

## The Process

### Phase 1: Discover
Find 15-25 sites to study — 10-15 direct competitors, 3-5 best-in-class globally, 5-10 adjacent local businesses.

### Phase 2: Visit & Analyze
Visit each site using WebFetch. Take structured notes on pages, nav, CTAs, trust signals, legal pages, content, and mobile experience. 3-5 minutes per site.

### Phase 3: Analyze Patterns
Count everything. "12 of 15 have individual service pages" → table stakes. "3 of 15 have a blog, none rank" → skip the blog. Numbers drive decisions.

### Phase 4: Identify Opportunities
What's missing from ALL competitors? What do they all get wrong? What features would help users that nobody builds? Generate ideas, filter by impact and effort.

### Phase 5: Synthesize
Produce the Site Architecture Brief — the single document that answers every "should we...?" question.

## Installation

```bash
git clone https://github.com/Zackjf/Superdumb.git
```

The `know-your-enemy/` directory is included in the SuperDumb repository.

## Skills (8)

| Skill | Purpose |
|---|---|
| `discover-competitors` | Find 15-25 sites to study (local + global + adjacent) |
| `visit-and-analyze` | Visit each site, take structured notes using the analysis template |
| `site-architecture` | Count page types, determine required vs recommended vs skip |
| `content-strategy` | Blog or no blog, FAQ, guides, video — based on what ranks |
| `conversion-patterns` | CTAs, contact channels, form fields, clicks to contact |
| `legal-and-compliance` | Required legal pages by country + industry |
| `opportunities` | Gaps, bad patterns, underserved audiences, feature ideas |
| `synthesize-brief` | Compile everything into a Site Architecture Brief |

## License

MIT. See [LICENSE](../LICENSE).
