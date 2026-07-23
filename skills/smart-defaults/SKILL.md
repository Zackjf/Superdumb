---
name: smart-defaults
description: "Apply this when building ANY form, input, selector, or configuration screen. Infer what you can, pre-fill what you know, default to the most common option. Every empty field is a question — make sure it's a question worth asking. If you can derive it, default it, or skip it, don't make the user answer it."
---

# Smart Defaults

Every empty field on a form is a question you're asking a real person. Questions cost attention, time, and willpower. Some questions are worth asking — "What's your shipping address?" when you genuinely don't know. Most are not — "What country are you in?" when your domain is `.co.uk` and the browser locale is `en-GB`.

The principle: reduce the number of decisions the user has to make. Not by hiding options, but by making the most likely choice the default and letting the user change it only if their situation is different from the majority.

This is not about assuming you know better than the user. It's about not making them do work you can do for them.

---

## What You Can Infer

You already have a surprising amount of information about the user before they fill in a single field. Use it.

### From the browser/device

| Signal | What you can infer | How to use it |
|---|---|---|
| Browser locale (`navigator.language`) | Language preference, likely country | Pre-select language and country. Format dates, numbers, and currency accordingly. |
| Timezone (`Intl.DateTimeZone`) | User's timezone | Display all times in their timezone. Never show UTC unless they're a developer tool user. Never show a timezone picker. |
| Device type (screen size, user agent) | Mobile vs. desktop | Optimize layout, input types, and interaction patterns. |
| Geolocation API (with permission) | City-level location | Pre-fill city/state for shipping. Suggest nearby stores or locations. |
| IP-based geolocation (no permission needed) | Country, region, rough city | Pre-select country in forms. Show local currency. Display relevant content. |
| Preferred color scheme (`prefers-color-scheme`) | Light/dark mode preference | Match their system preference. Don't ask. |
| OS / platform | Phone OS, desktop OS | Suggest the right download (iOS vs Android, Mac vs Windows). |

### From the account (returning users)

| Signal | What you can infer | How to use it |
|---|---|---|
| Name | How to address them | Pre-fill name fields. Use their name in greetings. |
| Email | Contact info | Pre-fill email fields. Don't ask them to type it again. |
| Previous addresses | Shipping/billing info | Offer saved addresses as defaults. |
| Previous orders | Preferences | "Order again" buttons. Suggested products. |
| Previous settings choices | Current preferences | Remember their sort order, view mode, filters, page size. |
| Billing address | Shipping address | Default shipping to billing address until they say otherwise. |
| Payment method | How they want to pay | Default to last-used payment method. |
| Last-used features | What they came to do | Show recently used items, last-opened projects, most-used tools. |

### From context

| Signal | What you can infer | How to use it |
|---|---|---|
| The page they're on | What they're trying to do | Pre-fill "subject" or "category" in support forms based on the page they came from. |
| Time of day | Greeting, urgency | "Good morning" not "Hello." Evening orders might need next-day shipping highlighted. |
| The link they clicked | Their intent | If they clicked "Upgrade," pre-select the next plan up, not the current one. |
| Cart contents | Purchase intent | Pre-calculate shipping, tax, total without requiring form completion first. |

---

## Pre-Selecting the Most Common Option

When a dropdown, radio group, or selector has one option that 70%+ of users will choose, pre-select it.

### Do pre-select when:

- **Country**: if your site targets one country (or your analytics show 85%+ from one country), pre-select it. A `.de` site should default to Germany. A `.com` site with 80% US traffic should default to United States.
- **Currency**: match the user's locale or the site's primary market.
- **Language**: match the browser's `navigator.language`.
- **Shipping method**: default to the most popular option (usually the cheapest).
- **Quantity**: default to 1. Nobody opens a product page wanting 0.
- **Date range filters**: default to something useful ("Last 30 days," "This month") rather than "All time" which loads slowly and shows too much.
- **Sort order**: default to the most useful sorting. For products, "Recommended" or "Most popular." For recent items, "Newest first." For search results, "Relevance."

### Don't pre-select when:

- **The choice is consequential and there's no clear majority.** Plan selection (Basic, Pro, Enterprise) — don't pre-select one, or pre-select only if one plan covers 70%+ of signups.
- **The choice is destructive and defaulting to the wrong one causes harm.** Don't default "Delete all" in a bulk action selector.
- **The choice is a preference with roughly even distribution.** If 40% of users pick A and 35% pick B, there's no strong default. Show the options without pre-selecting.

### The placeholder problem

`Select...` as a dropdown placeholder is a wasted opportunity. It says "I know nothing about you" when you probably know plenty.

| Instead of | Try |
|---|---|
| Country: `Select...` | Country: `United States` (pre-filled from IP) |
| Timezone: `Select...` | Timezone: `America/New_York` (pre-filled from browser) — or better, don't show this field at all |
| Currency: `Select...` | Currency: `USD` (pre-filled from locale) |
| Language: `Select...` | Language: `English` (pre-filled from browser) |
| Category: `Select...` | Category: the most common one, or smart-detect from context |

If you truly can't infer a default, `Select...` is acceptable. But exhaust every inference first.

---

## Remembering Previous Choices

For returning users, the best default is whatever they chose last time.

### What to remember

- **Sort order and view mode.** If they switched from grid view to list view, remember it. If they sorted by "Price: low to high," remember it.
- **Filters.** If they filtered to "Active" projects, show "Active" next time they visit the project list.
- **Form preferences.** If they always ship to the same address, default to it. If they always select "Express shipping," default to it.
- **Dashboard configuration.** If they rearranged widgets, collapsed sections, or changed date ranges, persist it.
- **Page size.** If they changed "Show 10 per page" to "Show 50 per page," remember it.
- **Last-used items.** Show recently opened projects, documents, or records near the top.

### How to remember

- **Logged-in users**: store preferences server-side, associated with their account.
- **Anonymous users**: use `localStorage` for preferences that don't need to persist across devices.
- **Don't use cookies for preferences.** Cookies are sent with every request and have size limits. Use them for auth only.

### What NOT to remember

- **Sensitive data that shouldn't persist.** Payment details beyond a saved card reference. Full address on a shared device.
- **One-time choices.** If they selected "Gift wrap" on one order, don't default to gift wrap on every future order. Gift wrapping is not a preference — it's a situational choice.
- **Error states.** If they had a failed payment, don't remember and re-show the failure next visit. Show a clean state.

---

## Smart Field Ordering

The order of options within a dropdown or list affects how fast users find their answer. Put the most likely answers first.

### Techniques

- **Most popular at top.** If 60% of users pick "United States," it goes first — not buried after Uganda and Ukraine in alphabetical order. Use a "Popular" section at the top followed by the full alphabetical list.
- **Recent choices first.** For returning users, show their previously selected options at the top of the list, separated from the full list.
- **Contextually relevant first.** If the user is on a page about shipping to Europe, show European countries first.
- **Alphabetical as fallback.** When there's no popularity data or contextual signal, alphabetical order is the expected default. Users know how to navigate it.

### Example: country selector

```
--- Recent ---
United States

--- Popular ---
United States
United Kingdom
Canada
Australia

--- All countries ---
Afghanistan
Albania
Algeria
...
```

This serves 80%+ of users within the first 5 options instead of requiring them to scroll to "U" in a 250-item list.

---

## The "Is This Field Worth Asking?" Test

For every field on every form, run these four questions in order. Stop at the first "yes":

### 1. Can you derive it?

If you can calculate, look up, or infer the answer from data you already have, don't ask the user.

- **Full name** → you have it from their account. Pre-fill it.
- **Country** → you have it from IP or locale. Pre-fill it.
- **Timezone** → you have it from the browser. Pre-fill it (or better, just use it without showing a field).
- **Order total** → you can calculate it from the cart. Show it, don't ask.
- **Account type** → you know it from their subscription. Don't ask them to select it.

### 2. Can you default it?

If there's a sensible default that works for the majority, set it and let the minority change it.

- **Shipping address** → default to billing address. Add a "Ship to a different address" toggle.
- **Notification preferences** → default to reasonable settings (email for important things, off for marketing). Let them customize later.
- **Quantity** → default to 1.
- **Payment method** → default to their last-used card.

### 3. Can you ask later?

If the field isn't needed to complete the current task, defer it. Get the minimum now, ask for extras when they become relevant.

- **Profile photo** → not needed during signup. Ask after they've used the product.
- **Phone number** → not needed for most signups. Ask when you need to send a verification code or when they enable 2FA.
- **Company name** → not needed during signup. Ask when they first create a team or workspace.
- **How did you hear about us?** → not needed ever on the signup form. Ask later in a non-blocking way (or check your analytics).

### 4. Can you skip it entirely?

Some fields exist because someone once said "it would be nice to know" rather than because they're needed.

- **Title/salutation** (Mr./Mrs./Dr.) → unless you're a formal institution, skip it. Address people by name.
- **"Confirm email"** → just show them what they typed and let them verify visually. A second field catches typos only when users copy-paste, which defeats the purpose.
- **Middle name** → unless it's legally required for your use case, skip it.
- **Fax number** → it's not the 90s.
- **"How did you hear about us?"** → almost always skippable. Use analytics, attribution, or ask later.

---

## Anti-Patterns

### Blank dropdowns with "Select..."
When you have the data to infer a default, a blank dropdown is an admission that you didn't bother. Country selectors that start empty when you know the user's IP. Timezone pickers that start blank when you have the browser timezone. Language selectors that default to nothing when the browser declares a language preference.

### Asking for country on a country-specific site
If your site is `shop.co.uk`, targeting UK customers, with GBP pricing, and British English copy — don't ask "What country are you in?" You know. Pre-fill United Kingdom. Show a "change country" link for the exceptions.

### Showing timezone pickers
Almost no user should ever need to see a timezone picker. Detect the timezone from the browser. Display times in the user's local timezone. If they travel and the timezone changes, the browser's timezone changes too. The only exception is scheduling across timezones ("book a meeting with someone in Tokyo"), and even then, show both timezones as context rather than asking the user to manually select one.

### Making users re-enter information you already have
The user is logged in. You have their name, email, and address on file. Then your support form asks for their name and email. Your checkout asks for their billing address despite having it from last order. Your profile edit form loads with empty fields instead of their current values. Every piece of data you already have should be pre-filled. No exceptions.

### Requiring configuration before first use
"Before you can use the app, please set up your preferences, configure your dashboard, and choose your notification settings." No. Let them use the app with sensible defaults. They'll configure things when (and if) they care to. Most users will never touch settings — so your defaults need to be good, but the setup shouldn't be a gate.

---

## The Test

For every form, input, or configuration screen:

1. **Count the empty fields.** Each one is a question. For each, ask: derive, default, defer, or delete?
2. **Check for inference opportunities.** Are you asking for anything the browser, account, or context already knows?
3. **Check your dropdowns.** Does any start with "Select..." when you could pre-fill a likely value?
4. **Check your returning user experience.** Does the form remember what they chose last time?
5. **Check your field order.** Are the most likely options at the top of every list?
6. **Remove one more field.** Whatever you've arrived at, challenge yourself to remove one more field. If the form still works, that field wasn't necessary.
