---
name: conversion-patterns
description: "Analyze how competitors convert visitors — what CTAs they use, what contact channels, how many form fields, how many clicks to contact, and what trust signals appear near conversion points. Produces conversion recommendations backed by evidence from visited sites."
---

# Conversion Patterns Analysis

How do visitors go from "browsing" to "in contact with the business"? Study the conversion mechanisms across all visited sites.

## What to Count

| Pattern | Count across sites |
|---|---|
| Primary contact: WhatsApp | ?/Y |
| Primary contact: Phone call | ?/Y |
| Primary contact: Form submission | ?/Y |
| Primary contact: Booking/calendar | ?/Y |
| Primary contact: Live chat | ?/Y |
| Primary contact: Email | ?/Y |
| Floating WhatsApp button | ?/Y |
| Floating chat widget | ?/Y |
| CTA in navigation | ?/Y |
| CTA on every page | ?/Y |

### Form fields
For every contact/booking form found, list the fields:
- Which fields appear on most forms?
- What's the average field count?
- What's the minimum (the leanest form)?

### CTA copy
Collect the exact CTA button text from every site:
- "Agendar cita" — X sites
- "Contactanos" — X sites
- "Solicitar presupuesto" — X sites
- etc.

The most common CTA text is what users expect. Use it or something very close.

### Clicks to contact
For each site, count: how many clicks from homepage to actually sending a message or submitting a form?

## Output

```
CONVERSION PATTERNS:

Primary channel: WhatsApp (12 of 15 sites)
  Recommendation: WhatsApp is primary CTA. Floating button on every page.

CTA text: "Agendar cita" (7 sites), "Pedir cita" (3), "Contactanos" (3)
  Recommendation: Use "Agendar cita" — it's the market standard.

Form fields (median across 10 forms):
  Name (10/10), Phone (10/10), Service needed (7/10), Message (5/10)
  Average: 3.2 fields. Leanest: 2 fields (name + phone).
  Recommendation: 3 fields — name, phone, service dropdown.

Clicks to contact: Average 1.8, Best: 1 (floating WhatsApp), Worst: 4
  Recommendation: 1 click max via floating WhatsApp, 2 clicks via nav CTA.

Trust signals near CTA:
  "Consulta sin costo" (8 sites) — free consultation promise
  Response time promise (4 sites) — "Respondemos en menos de 2 horas"
  Recommendation: Add both near the primary CTA.
```
