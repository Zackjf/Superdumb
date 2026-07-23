---
name: synthesize-brief
description: "Final step of Know Your Enemy. Takes the raw site analyses from 15-25 visited sites and produces a Site Architecture Brief — the document that tells you exactly what pages to build, what content to put on them, what legal pages to include, and what patterns to follow. This document is handed to SuperDumb or a developer to start building. Use after all sites have been visited and analyzed."
---

# Synthesize Brief

You've visited 15-25 sites. You have structured notes on each one. Now turn that raw data into decisions.

The output is a **Site Architecture Brief** — the single document that answers every "should we...?" question about the site before a single line of code is written.

## How to Synthesize

### Count everything

Go through your site analyses and count:

- How many sites have a blog? Active or abandoned?
- How many show prices? In what format?
- How many have FAQ pages?
- How many have individual service pages vs. one services list?
- How many have testimonials? Where? (separate page, homepage, both?)
- What are the top 3 nav labels used for each section?
- What's the primary contact channel? (count WhatsApp vs phone vs form vs booking)
- How many have legal pages? Which ones?
- How many display credentials/licenses?
- What's the average nav item count?

**The numbers drive the recommendations.** "12 of 15 sites have individual service pages" is a recommendation. "3 of 15 have a blog" is also a recommendation — probably NOT to blog.

### Separate table stakes from differentiators

**Table stakes** (all or nearly all successful sites have this):
- If 12+ of 15 sites do something, it's table stakes. You must do it too. Omitting it will feel broken.

**Recommended** (most successful sites have this):
- If 7-11 of 15 sites do something, it's recommended. Strong evidence it helps.

**Differentiator** (few sites do this, but the ones that do rank/convert better):
- If only 3-6 sites do something, but those sites are all in the top 5 rankings, it's a differentiator — an opportunity to stand out.

**Not needed** (evidence says skip):
- If fewer than 3 of 15 sites do something, and there's no ranking correlation, skip it. Explicitly state this so nobody wastes time building it.

### Resolve conflicts

When best-in-class sites (global) do something differently from local competitors:

- **If it's a cultural/local issue, follow local.** If Venezuelan dental sites use WhatsApp and US sites use booking calendars, follow Venezuela. The user is in Venezuela.
- **If it's a quality issue, follow best-in-class.** If local sites have outdated designs but best-in-class sites use modern layouts, follow best-in-class. The user wants a good site.
- **If it's a content issue, research further.** If best-in-class sites blog but local sites don't, check whether blog content ranks for local keywords. If not, skip the blog.

## Brief Template

```
# Site Architecture Brief

## Business
[Business type] in [City, Country]

## Research Summary
[X] direct competitors visited
[X] best-in-class examples visited
[X] adjacent local businesses visited
Total: [X] sites analyzed

---

## 1. Pages

### Required (table stakes)
| Page | Evidence | Notes |
|------|----------|-------|
| Homepage | 15/15 have one | Hero + services preview + trust + CTA |
| [Service pages] | 12/15 have individual pages | Individual pages rank 3x better than a single list |
| About / Team | 14/15 | Credentials critical for trust in [industry] |
| Contact | 15/15 | [Primary channel] primary, form secondary |
| Privacy policy | 8/15 + legally recommended | See legal section |

### Recommended
| Page | Evidence | Notes |
|------|----------|-------|
| FAQ | 6/15, those 6 capture more long-tail traffic | [X] common questions identified |
| Testimonials | 8/15, embedded on homepage + separate page | Real names, stars, specific results |

### Not Needed
| Page | Evidence | Why skip |
|------|----------|---------|
| Blog | 3/15 active, 0 rank for blog content | No SEO value in this market |
| Patient portal | 0/15 | Not expected for this business type |
| Newsletter | 0/15 | Nobody subscribes to [industry] newsletters |

---

## 2. Navigation

**Recommended structure:**
[Item 1] | [Item 2] | [Item 3] | [Item 4] | [CTA Button →]

**Evidence:**
- Average nav items across competitors: [X]
- Most common labels: [list exact text from competitors]
- [X] of 15 have a CTA button in nav
- [X] of 15 use dropdowns (recommendation: [yes/no])

**Mobile:** [hamburger / bottom nav / sticky CTA]

---

## 3. Content Strategy

**Blog:** [Yes/No]
- [X] of 15 competitors blog
- [X] of those blogs are active (posted in last 3 months)
- Blog content ranks for [X] keywords / does not rank
- Recommendation: [build a blog focused on X / skip the blog]

**FAQ:** [Yes/No]
- [X] of 15 have FAQ pages
- Top questions found across competitor sites and People Also Ask:
  1. [Question]
  2. [Question]
  3. [Question]

**Case studies / testimonials:** [Format recommendation]
**Video:** [Yes/No, what type]
**Guides / resources:** [Yes/No]

---

## 4. Conversion

**Primary channel:** [WhatsApp / Phone / Form / Booking / Chat]
- Evidence: [X] of 15 use [channel] as primary

**CTA text used by competitors:**
- "[Text 1]" — [X] sites
- "[Text 2]" — [X] sites
- "[Text 3]" — [X] sites

**Form fields (contact/booking forms):**
- Most common: [list fields + count]
- Average field count: [X]
- Recommendation: [X] fields maximum

**Clicks from homepage to contact:** [average across competitors]

**Floating/sticky elements:**
- [X] of 15 have floating WhatsApp / chat / CTA
- Recommendation: [yes/no, what type]

---

## 5. Trust Signals

**What the top-ranking sites display:**
| Signal | Count | Recommendation |
|--------|-------|----------------|
| Professional credentials | X/15 | Required |
| Real facility photos | X/15 | Required (no stock photos) |
| Google Reviews widget | X/15 | Recommended |
| Before/after gallery | X/15 | [Recommended / Not needed] |
| Years in business | X/15 | [Recommended] |
| Professional association badges | X/15 | [If applicable] |

**Trust signals near CTAs:**
- What appears next to the contact form or WhatsApp button on top sites

---

## 6. Legal & Compliance

[Output from legal-and-compliance skill]

### Required Pages
| Page | Reason |
|------|--------|
| Privacy policy | [Law name] requires it for sites collecting personal data |

### Required Display
| Item | Reason |
|------|--------|
| License number | [Professional regulation requires it] |

### Not Required
| Item | Why |
|------|-----|
| Cookie banner | [No local law requires it, site is local-only] |

---

## 7. SEO Patterns

- **Individual vs aggregated:** [Do individual service pages rank better?]
- **Structured data:** [What schema types do top sites use?]
- **Keyword patterns:** [What search patterns drive traffic?]
  - "[business type] en [city]" — [volume/competition]
  - "[service] [city]" — [volume/competition]
- **Content length:** [Average word count on top-ranking pages]
- **Internal linking:** [Do top sites cross-link services? How?]

---

## 8. Cultural & Geographic

- **Contact preference:** [WhatsApp / Email / Phone] — based on [X] of [Y] sites
- **Currency:** [USD / Local / Both] — standard in [country] for this industry
- **Language:** [Formal / Informal] Spanish/Portuguese/English
- **Social platforms:** [Instagram / Facebook / TikTok / LinkedIn] — which are linked most
- **Business hours:** [How prominently displayed] — [X] of 15 show hours on homepage
- **Local specifics:** [Anything a non-local developer would miss]

---

## 9. Technical

- **Platform breakdown:** [WordPress X, Wix Y, Custom Z]
- **Page speed benchmark:** Top 5 average [X]s, bottom 5 average [Y]s
- **Booking systems used:** [Calendly / local system / WhatsApp / none]
- **Target page speed:** Under [X] seconds (based on local internet conditions)
- **Recommendation:** [Static site / CMS / Full app] based on requirements

---

## Next Steps

Hand this brief to SuperDumb's spec-to-ux skill to produce wireframes for each page, or to a developer to start building.

The brief answers WHAT to build. SuperDumb answers HOW to build each page.
```

## Quality Checks

Before finalizing the brief:

1. **Every recommendation cites evidence.** "12 of 15 sites do X" — not "I think you should do X."
2. **"Not needed" is explicitly stated.** The client needs to know what to SKIP as much as what to build. Don't leave items ambiguous.
3. **Legal section was researched, not assumed.** Don't default to US/EU requirements for a site in Venezuela.
4. **Cultural specifics are from observation, not assumption.** "WhatsApp is primary" because you SAW it on 12 of 15 sites, not because you assumed.
5. **The page list is complete.** Every page the site needs — including legal pages, error pages, and any compliance pages — is listed.
6. **Nav labels use the LOCAL LANGUAGE.** If the site is in Spanish, the nav recommendations are in Spanish. Don't recommend "Services" for a Venezuelan site — recommend "Servicios."
