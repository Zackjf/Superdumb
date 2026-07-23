---
name: simplify-the-page
description: "Use this when a page WORKS but feels heavy, complex, or overwhelming. Not for finding bugs — for reimagining pages to be radically simpler. Takes an existing page and asks: what if this had half the fields, half the options, half the text? Produces a before/after redesign with a simplified wireframe. Use whenever a page has too many fields, too many tabs, too many options, too much text, or requires the user to understand concepts they shouldn't need to know."
---

# Simplify the Page

This skill is not about fixing bugs. The audit skill catches wrong input types, raw enums, missing error states. This skill is for pages that technically work but are **too complex for what they do**.

The question this skill answers: **"What if we started over and designed this page with half the stuff?"**

Most pages built by AI agents are over-built. They expose every database field, show every option, explain every concept, and give the user control over things they don't care about. The result is a page that works but feels like a cockpit.

---

## When to Use This

Use this skill when a page has any of these symptoms:

- **More than 8-10 form fields** visible at once
- **More than 3-4 tabs** on a single editor
- **A settings page where most users would only change 1-2 things** but 15 options are shown
- **A dashboard with 8+ metrics** competing for attention
- **A page that requires understanding a concept** the user shouldn't need to know (what's a "profile"? what's a "destination"? what's a "masking mode"?)
- **A page where you have to scroll past stuff you don't care about** to reach the thing you came for
- **A multi-step flow that could be one step**
- **A page with explanatory paragraphs** because the UI isn't self-evident without them

---

## The Process

### Step 1: What is this page's ONE job?

State it as the user would say it. Not "manage subscription settings" — that's 4 jobs. Pick the ONE most common reason someone comes to this page.

Examples:
- Trip editor: "Describe a trip so it looks good on the website"
- Settings: "Change the one thing that's bugging me"
- Experiment detail: "Did my title test win or lose?"
- Dashboard: "How is my site doing?"

### Step 2: What's the minimum to do that job?

List only what's absolutely necessary. Be ruthless.

**The 3-question filter for every element on the page:**
1. **Would the user notice if this was gone?** If no → remove it.
2. **Do 80%+ of users ever interact with this?** If no → hide it behind "Advanced" or move to a separate page.
3. **Can this be a smart default instead of a choice?** If yes → default it and remove the field.

### Step 3: Redesign with a wireframe

Produce a before/after showing the simplified version. Use the same ASCII wireframe format as `spec-to-ux`.

---

## Simplification Techniques

### Collapse tabs into sections (or eliminate them)

**Before:** An editor with 5 tabs — Details, Pricing, Itinerary, SEO, Settings
**The question:** Does the user actually switch between these tabs in one session? Or do they edit Details on Monday and SEO on Thursday?

If tabs are used independently, they might be better as separate pages reached from a list. If they're used together, collapse them into one scrollable page with section headings.

**Rule of thumb:**
- 1-2 tabs → just use one page with sections, tabs are overhead
- 3-4 tabs → tabs are justified if each tab is a distinct task
- 5+ tabs → you've crammed too many concerns into one editor. Split by frequency: "Common" (the fields they touch every time) and "Advanced" (everything else)

### Replace fields with smart defaults

**Before:** 20-field trip editor with type, style, summary, description, duration days, duration nights, group min, group max, activity level, languages, pricing mode, starting price, currency, price notes, inclusions, exclusions, hero image, enquiry form, whatsapp template, featured toggle.

**After:** 6-field trip editor:
- Name
- Summary (one paragraph)
- Description (rich text)
- Duration ("7 days, 6 nights" — one field, not two)
- Starting price (with currency auto-detected from org settings)
- Hero image

Where did the other 14 fields go?
- **Type, style, activity level** → derived from description by AI or set as tags
- **Group min/max** → defaulted from org settings, editable in "Advanced"
- **Languages** → defaulted from org settings
- **Pricing mode** → defaulted to "starting from" (the most common)
- **Currency** → defaulted from org settings
- **Price notes, inclusions, exclusions** → collapsed into an "Add details" expandable
- **Enquiry form, whatsapp template** → defaulted from org settings
- **Featured toggle** → moved to list page (toggle inline, not in the editor)

**The principle: most fields should have a sensible default set once at the org/account level, not re-entered on every new item.**

### Replace concepts with outcomes

**Before:** "Masking Mode" dropdown with options "Full Mask", "Partial", "No Masking"
**After:** "When a code arrives in your channel:" with radio buttons showing what each option actually looks like:
```
○ Show the full code: 482910
○ Show only the last 2 digits: ••••10
○ Hide the code completely: •••••• (tap to reveal)
```

The user doesn't need to understand "masking mode." They need to see what happens.

**Before:** "Reveal TTL" number input in seconds
**After:** "How long can codes be viewed?" dropdown with "30 minutes", "1 hour", "4 hours", "24 hours", "No limit"

Turn raw config into a visual choice. If the user can see the outcome, they don't need to understand the mechanism.

### Replace statistics with verdicts

**Before:** Experiment results showing: p-value: 0.0164, Z-score: 2.14, Control CTR: 3.2%, Variant CTR: 4.1%, Impressions: 12,847, Confidence: 98.4%
**After:**

```
┌────────────────────────────────────────┐
│  ✓ WINNER: "10 Best Running Shoes"     │
│                                        │
│  Gets 28% more clicks than the         │
│  original title.                       │
│                                        │
│  Based on 12,847 impressions.          │
│  We're 98% confident this is real.     │
│                                        │
│  [Apply winning title]  [See details]  │
└────────────────────────────────────────┘
```

The "See details" expands to show p-value, Z-score, and CTR comparison for users who want it. But the PRIMARY view is: who won, by how much, and what to do about it.

### Replace walls of settings with one-question-at-a-time

**Before:** A settings page with 15 options in a flat list
**After:** Settings organized as questions:

```
How should codes look in chat?
  ○ Show the full code
  ○ Show only the last 2 digits  ← recommended
  ○ Hide completely

How long should codes be viewable?
  [1 hour ▾]  ← most teams use this

Who can see codes?
  ○ Anyone in the channel
  ○ Only specific team members
```

Each question is self-contained. The user answers one, moves to the next. No "Save" button at the bottom of 15 options — each choice auto-saves or saves with a single "Save" at the bottom of a short, manageable list.

### Replace multi-page flows with one smart page

**Before:** Add a source: Navigate to Research → Sources tab → click "Add source" → fill out modal with Name, URL, Type (dropdown with 9 options), Feed URL, Scan Frequency, Notes

**After:** Add a source: Paste a URL. That's it.

The system:
1. Detects the source type from the URL (Reddit, YouTube, RSS, etc.)
2. Fetches the name from the page title
3. Auto-detects the feed URL
4. Sets frequency to "Daily" by default
5. Shows a confirmation: "We found Search Engine Journal (RSS feed). We'll check it daily."

One field. One action. Everything else is inferred or defaulted. The user can fine-tune later if they want.

### Remove explanatory text by making the UI self-evident

**Before:** A paragraph explaining what profiles are, followed by a list of profiles
**After:** The list itself makes it clear:

```
Your code sources

📱 +1 (555) 123-4567     SMS codes → #security-codes     Active
📧 codes@company.com     Email codes → #security-codes    Active
🔐 Stripe Authenticator  App codes → #security-codes      Active

[+ Add a phone, email, or authenticator]
```

No explanation paragraph needed. The visual layout — icon + source + arrow + destination + status — tells the user everything. The CTA button text ("Add a phone, email, or authenticator") teaches the concept without a paragraph.

---

## The Simplification Wireframe

For each page you simplify, produce:

```
PAGE: [Name]
CURRENT STATE: [Brief description of what's there now]
PROBLEM: [Why it's too complex — be specific]
USER'S ACTUAL JOB: [One sentence]

BEFORE:
[Brief description or wireframe of current state]
  - X fields / X tabs / X sections
  - User needs to understand: [concepts]
  - Time to complete: ~X minutes

AFTER:
┌────────────────────────────────────────┐
│  [Simplified wireframe]                │
│                                        │
│  [Only the essential elements]         │
│                                        │
│  [Primary action]                      │
└────────────────────────────────────────┘
  - X fields (was Y) / X visible options (was Y)
  - User needs to understand: [nothing, ideally]
  - Time to complete: ~X seconds

WHERE DID THE REST GO?
  - [Field A] → defaulted from org settings
  - [Field B] → derived from input automatically
  - [Field C] → moved to "Advanced" section (collapsed)
  - [Field D] → removed entirely (nobody uses this)
  - [Tab E] → merged into main view as a section
  - [Concept F] → replaced with visual outcome

MIGRATION:
  - Existing values for removed fields are preserved in the database
  - "Advanced" section shows all hidden fields for power users
  - No data loss
```

---

## The Radical Simplicity Test

After redesigning, check:

1. **Can someone complete the task without reading any explanatory text?** If no, the UI isn't self-evident yet.
2. **Could you remove one more field?** Always try. If it still works, that field wasn't needed.
3. **Are you showing the mechanism or the outcome?** Users care about "28% more clicks" not "p-value 0.016". Show outcomes.
4. **Is there a paragraph of text on this page?** Replace it with better labels, better layout, or remove it. Paragraphs on UI pages mean the UI isn't self-explanatory.
5. **How many concepts does the user need to understand to use this page?** Target: zero new concepts. If you must introduce one, explain it inline with an example, not a definition.
6. **Would your mom/dad/non-technical friend be able to use this page?** If not, it's still too complex.

---

## Anti-patterns

**"Power users need all these options."**
Maybe. But show them the simple version first, with an "Advanced" toggle for power users. 95% of users will never click Advanced. Build for the 95%, accommodate the 5%.

**"We might need this field later."**
Then add it later. Don't build for hypothetical futures. Every field you show today is cognitive load for every user today.

**"The user should understand how this works."**
No. The user should understand what happens when they click the button. They don't need to understand the mechanism, the algorithm, the protocol, or the data model. Show outcomes, hide machinery.

**"We already built all these features."**
Features that nobody uses are noise, not value. Every feature on the page competes with every other feature for attention. The most impactful redesign is often: remove half the features from the page (not from the product — just from the default view).
