---
name: manage-cognitive-load
description: "Apply when building any screen with choices, options, settings, or information density. Limits decisions per screen to 3-4, enforces progressive disclosure, and prevents the wall-of-options pattern. Use whenever a page feels 'busy' or has more than a handful of choices, or when building settings, dashboards, or configuration pages."
---

# Manage Cognitive Load

Every choice on a screen costs mental energy. Every new concept introduced requires the user to stop and process. Humans can comfortably hold 3-4 things in working memory at once (Miller's Law, adjusted for real-world UI). Beyond that, they freeze, rush through without reading, or leave.

Your job is to show just enough for the current decision, and nothing more.

## Core Rules

### 3-4 choices per decision point

When asking the user to choose, limit to 3-4 options visible at once.

- **Pricing plans?** 3 options, one highlighted as recommended.
- **Account type?** 2-3 clear choices with one-line descriptions.
- **Settings page?** Group into 3-4 sections. Each section expands to reveal its options.
- **Navigation?** 5-7 top-level items maximum. If you have more, you have too many.

If you genuinely have 15 options, don't show 15 at once. Group them into 3-4 categories, then let the user drill into the relevant one.

### One new concept per screen

If the user needs to understand what a "workspace" is before they can use it, don't also introduce "teams," "channels," and "permissions" on the same screen. Introduce workspace first. Let them interact with it. Then introduce the next concept when they need it.

### Progressive disclosure

Show the minimum by default. Reveal complexity when requested.

**Patterns that work:**
- "Advanced options" toggle that expands more fields
- "Show more" at the bottom of a truncated list
- Tooltip or "?" icon that explains a concept when tapped
- Sections that collapse/expand (but show the most-used section open by default)
- "Learn more" links to separate pages for detailed information

**Patterns that don't work:**
- Hiding the primary action behind progressive disclosure (that's hiding, not disclosing)
- "Advanced" sections that contain things most users actually need
- Making the user click three times to reach something they need every visit

### Group related items

Ungrouped items are harder to scan than grouped ones. The brain processes "4 groups of 3" faster than "12 scattered items."

- Group form fields by topic (personal info, address, payment)
- Group settings by function (account, notifications, privacy)
- Group navigation by domain (shopping, account, help)
- Use visual boundaries: spacing, light backgrounds, subtle borders, or headings

### Reduce, don't just organize

Before grouping 15 options into nice sections, ask: do all 15 need to exist?

- Can any be combined? ("Email notifications" and "Push notifications" → "Notifications" with a channel toggle inside)
- Can any use smart defaults so the user never has to touch them? (Most people want the default timezone — auto-detect it)
- Can any be removed entirely? (Does anyone actually use "Change avatar border color"?)

## Dashboard-Specific Rules

Dashboards are where cognitive overload happens most. Every metric you add competes with every other metric for attention.

- **Show 3-5 key metrics**, not 15. If the user needs more, put them on a detail page.
- **Lead with the metric they check first.** Ask: "What is the ONE number this person opens the dashboard to see?" That number should be the largest, most prominent thing.
- **Use visual hierarchy to separate primary from secondary metrics.** The primary metric gets the big number. Secondary metrics are smaller, below or to the side.
- **Don't auto-refresh dashboards with disorienting animation.** If data updates, do it subtly.

## The "Squint Test" for Cognitive Load

Squint at your screen (or blur a screenshot). You should be able to identify:
- Where the primary action/information is
- How many distinct groups of content exist (should be 3-4, not 8-10)
- Where to look first

If the squinted page looks like a uniform wall of stuff, cognitive load is too high. Add visual breaks, remove items, or group differently.

## Navigation: Max 8-10 Top-Level Items

Sidebar or top navigation with more than 10 items is a sign the app is organized around **database entities** instead of **user tasks**. 28 nav links means the developer created one link per table.

**The fix:** Group related entities under task-oriented parent items:
- "Content" (not Pages + Destinations + Guides + Trips + Fairs + Team + Testimonials + Cases = 8 links)
- "Sales" (not Leads + Proposals + Pipeline + Tags = 4 links)
- "Settings" (not Settings + Security + Webhooks + Users + SEO + Redirects + Analytics = 7 links)

Target: 8-10 top-level items max. Use sub-menus or landing pages for the rest.

## Forms: Group After 8-10 Fields

A form with 16-20 fields in a single scrollable panel is a wall of options for forms. When a form exceeds 8-10 fields, **add visual sections** with fieldset headings:

```
┌─ Informações básicas ─────────────────┐
│  Nome, Email, Telefone                │
└───────────────────────────────────────┘

┌─ Detalhes do pedido ──────────────────┐
│  Produto, Quantidade, Notas           │
└───────────────────────────────────────┘

┌─ Configuração avançada ───────────────┐
│  (collapsed by default)               │
└───────────────────────────────────────┘
```

Rules:
- 1-8 fields: single group, no sections needed
- 8-15 fields: 2-3 sections with headings
- 15+ fields: tabs or multi-step, not a single scrollable form
- Advanced/rarely-used fields behind a toggle or in a separate tab

## Anti-patterns

**The wall of options.** A settings page with 20 toggles, no grouping, no hierarchy. The user has to read every single one to find what they want. Group into sections. Put common settings first.

**The junk drawer navigation.** 12 items in the sidebar, all at the same visual weight, spanning multiple unrelated domains. If you have 12 sections, you need to rethink your information architecture, not add a 13th.

**The "helpful" tooltip explosion.** Every label has a "?" icon. When everything needs explanation, nothing is self-evident. Rewrite the labels to be self-explanatory instead of relying on tooltips. Tooltips are a band-aid for unclear labels.

**Premature choice.** Asking the user to make a decision before they have context. "Choose your plan" on the first screen, before the user knows what any plan includes. Give context first, then ask.
