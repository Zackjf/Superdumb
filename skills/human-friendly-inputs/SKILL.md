---
name: human-friendly-inputs
description: "Use this when building ANY form, input, selector, data display, or interactive control. Ensures inputs match how humans think, hides developer artifacts, and uses the right control for every situation."
---

# Human-Friendly Inputs, Forms & Data Display

Every input is a question you're asking a real person. Every piece of data you display is something they need to understand instantly. Build forms like you're having a conversation, not interrogating a database.

**Core rule: If it came from your database, code, or API — it's not ready to show a human yet.**

---

## Never Render Raw HTML/Markdown to Users

When building blog pages, CMS-driven content, rich text displays, or any screen that renders user-authored or AI-generated content:

### The problems

1. **Raw HTML tags visible as text.** User sees `<p>Welcome to our blog</p>` or `<h2>About Us</h2>` instead of formatted text. This happens when HTML content is rendered with `{content}` (text interpolation) instead of a proper renderer.

2. **XSS via `dangerouslySetInnerHTML`.** Content from a database or CMS is injected as raw HTML with no sanitization. If any content was user-submitted, AI-generated, or imported, it can contain `<script>` tags, event handlers (`onload`, `onerror`), or malicious iframes.

3. **Markdown source shown as-is.** User sees `## Heading` and `**bold**` and `[link](url)` as literal characters instead of rendered formatting. This happens when Markdown content is stored but no Markdown processor is used at render time.

4. **Mixed format confusion.** Editor says "Content (Markdown)" but the renderer uses `dangerouslySetInnerHTML` expecting HTML. Or content is stored as HTML but displayed with a Markdown renderer that escapes the tags.

### Rules

- **Never use `dangerouslySetInnerHTML` without sanitization.** Always run content through `DOMPurify`, `sanitize-html`, or equivalent before rendering. Strip `<script>`, `<iframe>`, event handler attributes, and `javascript:` URLs.
- **Never render content with plain `{content}` if it contains markup.** Use a proper renderer — `react-markdown` for Markdown, a sanitized `dangerouslySetInnerHTML` for HTML, or a rich-text component for structured content.
- **Match the editor format to the renderer.** If the editor produces Markdown, render with a Markdown processor. If it produces HTML (from a WYSIWYG like TipTap or Quill), render as sanitized HTML. Never mismatch.
- **Test with real content.** Paste content with `<script>alert('xss')</script>`, raw HTML tags, Markdown syntax, and special characters. If any of it renders wrong or executes, fix it before shipping.
- **Preview what the user will see.** Blog editors and CMS should show a live preview or at minimum a "Preview" button that renders content exactly as the public page will.

### Common patterns Claude gets wrong

| What Claude builds | The problem | The fix |
|---|---|---|
| `<div dangerouslySetInnerHTML={{ __html: post.content }} />` | No sanitization — XSS risk | `<div dangerouslySetInnerHTML={{ __html: DOMPurify.sanitize(post.content) }} />` |
| `<p>{post.body}</p>` where body contains `<h2>Title</h2><p>Text</p>` | Raw HTML tags shown as text | Use a renderer, not text interpolation |
| Editor labeled "Markdown" but renderer uses `dangerouslySetInnerHTML` | Format mismatch — Markdown rendered as HTML or vice versa | Use `react-markdown` or convert Markdown to HTML before storing |
| `<div>{markdownContent}</div>` | Markdown syntax shown as literal characters (`## `, `**bold**`) | Use `<ReactMarkdown>{markdownContent}</ReactMarkdown>` |
| AI-generated content rendered without escaping | AI may produce malformed HTML, unclosed tags, or unexpected formatting | Sanitize all AI output before rendering |

---

## Never Show Developer Artifacts

Users don't think in IDs, hashes, timestamps, or status codes. They think in names, dates, and plain words.

### What to hide vs. what to show

| Developer artifact | What the user sees instead |
|---|---|
| `user_id: 84729` | "John Smith" |
| `order_id: a8f3c-91b2-...` | "Order #1234" |
| `2026-07-20T14:32:00.000Z` | "3 days ago" or "July 20, 2026" |
| `1721849283` (unix timestamp) | "Monday at 2:30 PM" |
| `4999` (cents) | "$49.99" |
| `status: 2` or `PENDING_REVIEW` | "Being reviewed" (with a yellow dot) |
| `sku: WDG-BLU-LG-001` | "Blue Widget — Large" |
| `geo_lat: 37.77, geo_lng: -122.41` | "San Francisco, CA" |
| `err_code: E_VALIDATION_422` | "That email doesn't look right" |
| `commit: 3a7f2b9` | (don't show at all, or "Last updated Tuesday") |
| `null` / `undefined` / `NaN` | "" or "Not set" or "None yet" |
| `created_at` / `updated_at` | Only show if the user actually cares. Usually they don't. |
| `[Object object]` or raw JSON | Never. Parse it or don't show it. |

### Rules

- **URLs displayed to users**: show `example.com/page`, not `https://www.example.com/page?utm_source=internal&ref=dashboard_v2`
- **IDs in URLs are OK** (the browser bar is for the system), but never display them in the UI as labels or references
- **If you need an ID for a technical reason** (like a support ticket), generate a short human-readable one: `#1234`, `TKT-5678`, not a UUID
- **Dates**: relative when recent ("2 hours ago", "yesterday"), absolute when older ("July 20, 2026"). Never raw ISO strings.
- **Numbers**: format with commas (`1,234` not `1234`), round when appropriate (`$49.99` not `$49.9900`), use units (`12 lb` not `12`)
- **Enums/statuses**: map every internal value to a human word + visual indicator (color dot, badge, icon). Never expose the raw enum.

---

## Never Expose Technical Formats as Inputs

Some data has a technical storage format that should NEVER be shown to or entered by users. The system must translate between the human format and the machine format.

### Scheduling (cron, intervals)

Cron expressions (`*/15 * * * *`, `0 7 * * 5`) are for servers, not humans. Users think "every Friday at 7am" — give them controls that match:

| User thinks | Give them | Not this |
|---|---|---|
| "Every Friday at 7am" | Day-of-week checkboxes + time picker | A text field for cron syntax |
| "Every 15 minutes" | Dropdown: "Every 5 min / 15 min / 30 min / 1 hour" | `*/15 * * * *` |
| "Once a day at midnight" | Time picker with "Daily" preset selected | `0 0 * * *` |
| "First Monday of each month" | Frequency dropdown + day picker | `0 9 1-7 * 1` |

**Build a schedule picker component** with:
1. Frequency selector: "Every X minutes" / "Daily" / "Weekly" / "Monthly"
2. If daily/weekly: day-of-week checkboxes (for weekly) + time picker
3. If interval: dropdown of sensible intervals (5/15/30/60 min)
4. Preview text: "Runs every Friday at 7:00 AM" — human-readable confirmation
5. Store as cron internally — never show the cron string

### Other technical formats to never expose

| Technical format | Human replacement |
|---|---|
| Regex patterns | Keyword/phrase inputs with "contains" / "starts with" / "matches exactly" dropdowns |
| SQL/query syntax | Filter builder with dropdowns: field → operator → value |
| JSON configuration | Structured form with labeled fields |
| Color hex codes (`#FF5733`) | Color picker with swatches |
| File paths (`/var/data/export/`) | File browser or drag-and-drop |
| API endpoints / URLs for webhooks | "Connect to [Service]" with guided setup, not a raw URL field |
| Duration in milliseconds (`86400000`) | "1 day" or a number field with unit dropdown (minutes/hours/days) |
| Byte sizes (`1073741824`) | "1 GB" — always convert to human-readable units |
| Image/media as URL (`https://cdn.example.com/img.jpg`) | File upload with drag-and-drop + preview. Users don't have URLs for their images — they have files on their device. Even when images ARE URLs (from a CDN), show a thumbnail preview, not the URL string. |
| Webhook URLs | "Connect to [Service]" with guided setup or paste-and-test pattern, not a raw URL field with no validation or preview |

The principle: if a developer would recognize the format but a shop owner wouldn't, it needs a human translation layer.

---

## Use the Right Input for the Job

The input type should match how the person thinks about the answer, not how your database stores it.

### Input type decision guide

| Situation | Use this | Not this |
|---|---|---|
| Yes or No | Toggle switch | Dropdown with 2 options |
| One choice from 2-5 options | Radio buttons (all visible) | Dropdown (hides choices) |
| One choice from 6+ options | Dropdown or searchable select | Radio buttons (too long) |
| One choice from 20+ options | Searchable/filterable select | Plain dropdown (too many to scroll) |
| Multiple choices from few options | Checkboxes | Multi-select dropdown |
| Multiple choices from many options | Chip/tag input with search | Long checkbox list |
| A date | Date picker | Text field |
| A date range | Dual date picker with presets ("Last 7 days", "This month") | Two separate text fields |
| A time | Time picker or constrained dropdown | Free text field |
| A phone number | `tel` input, accept any format | Text field with format enforcement |
| An email | `email` input with inline validation | Plain text field |
| A small quantity (1-10) | Stepper with +/- buttons | Text field |
| A large number | Text field with formatting | Stepper (too many clicks) |
| Currency | Formatted input with currency symbol baked in | Plain text + "enter in cents" |
| A color | Color picker or preset swatches | Hex code text field |
| A file | Drag-and-drop zone with click fallback | Bare `<input type="file">` |
| An image/media | File upload with preview + drag-and-drop | A URL text field |
| A logo or avatar | Upload with crop/preview, drag-and-drop | A URL text field |
| A password | Text field with show/hide toggle | Text field with no visibility option |
| A long text response | Textarea that grows with content | Fixed-height textarea with scrollbar |
| A URL | Text input that prepends `https://` automatically | Text field requiring full URL |
| A search | Input with instant results as you type | Input + separate search button + results page |
| Star rating | Clickable stars / visual rating | Number input 1-5 |
| An address | Single field with autocomplete/Places API | 5 separate fields (street, city, state, zip, country) |
| Country | Searchable dropdown with flags, user's country pre-selected | 250-item alphabetical dropdown |

---

## Form Layout & Structure

### One column, top-aligned labels

- **Single column forms.** Always. Multi-column forms break scanning order and cause skipped fields.
- **Labels above inputs**, not beside them. Above-aligned labels have the fastest completion times (UX research by Matteo Penzo).
- **Labels are short nouns or questions.** "Email" or "What's your email?" — not "Please enter your email address in the field below."

### Grouping and ordering

- **Group related fields** with a subtle visual boundary (light border, background, or spacing). Name + email + phone together. Address fields together.
- **Order fields the way humans think about them.** Name before email. Email before phone. Street before city. Start date before end date. Don't follow database column order.
- **Put the most common/required fields first.** Optional fields at the bottom or behind a "More options" toggle.

### Required vs. optional

- **Assume fields are required by default.** Mark the optional ones "(optional)" — don't mark required ones with asterisks.
- **But first: does this field need to exist at all?** Every field you remove is friction eliminated. If you can infer it, derive it, or ask later — cut it.

### Field sizing

- **Input width hints at expected length.** Zip code input should be short. Bio textarea should be wide. Don't make every input the same full width.
- **Tap targets: minimum 44x44px.** Fingers are bigger than mouse pointers. Small checkboxes and radio buttons are hostile on mobile.

---

## Validation & Error Handling

### Validate smart, not strict

- **Inline validation on blur** (when the user leaves the field), not on every keystroke. Keystroke validation feels like someone looking over your shoulder.
- **Never clear the form on error.** The user just typed all of that. Show what's wrong, let them fix it, keep everything else.
- **Mark the specific field with the error**, not just a banner at the top. Scroll to the first error if it's off-screen.
- **Error text goes directly below the field it's about.** Not in a list at the top. Not in a toast that disappears.

### Be generous with what you accept (Postel's Law)

- **Phone numbers**: accept `(555) 123-4567`, `555-123-4567`, `5551234567`, `+1 555 123 4567`. Parse them all. Display consistently.
- **Names**: accept accents (José), apostrophes (O'Brien), hyphens (Smith-Jones), spaces (van der Berg), and single-character names. Never reject a real name.
- **URLs**: accept with or without `https://`, with or without `www.`. Normalize it yourself.
- **Email**: basic format check only. Don't reject `+` tags, long TLDs, or unusual but valid addresses.
- **Currency**: accept `$49.99`, `49.99`, `$49`, `49,99` (European). Parse it.
- **Dates**: if using a text fallback, accept `7/20/26`, `07/20/2026`, `July 20, 2026`. But prefer a date picker so this isn't an issue.

### Error messages are copy, not codes

- Bad: `Error: field validation failed (E_PHONE_FORMAT)`
- Bad: `Invalid input`
- Good: `That phone number looks too short — try including the area code`
- Good: `We need your email so we can send the receipt`

---

## Selectors & Pickers

### Dropdowns

- **Don't use a dropdown for fewer than 5 options.** Use radio buttons — they show all choices at once without an extra click.
- **Don't use a plain dropdown for more than 15-20 options.** Switch to a searchable select.
- **Pre-select the most common choice** when there's a clear default. Don't leave it on "Select..."  unless the choice genuinely matters and has no obvious default.
- **"Select..." placeholder is fine when no default exists** — but never use it to satisfy a required field. If they skip it, tell them why it matters.

### Date & time pickers

- **Offer presets for common ranges.** "Today", "This week", "Last 30 days", "This month" save clicks and reduce errors.
- **Show the day of the week** in date pickers. "Friday, July 24" is more useful than "07/24" because people think in days.
- **For scheduling: show availability**, not just a calendar. Gray out unavailable dates/times. Don't let them pick something invalid then show an error.

### Search & autocomplete

- **Start showing results after 2-3 characters**, not requiring them to press Enter.
- **Show recent/frequent selections** when the field is focused but empty.
- **Handle "no results" with a helpful message**, not a blank dropdown. "No results for 'X' — try a different spelling?" or offer to create a new entry if applicable.

---

## Data Display That Respects Humans

When showing data back to users (tables, lists, detail views):

- **Lead with the name/title**, not the ID or type. "Blue Widget — Large" not "Product #WDG-BLU-LG-001"
- **Show status as a visual**, not just text. A green dot + "Active" beats plain text "active". A red badge + "Overdue" beats "status: overdue".
- **Relative time for recent, absolute for old.** "2 hours ago" → "Yesterday at 3pm" → "July 20, 2026". Never "2026-07-20T14:32:00Z".
- **Round numbers to what matters.** "1.2k visitors" not "1,247 visitors" in a dashboard. Show the precise number on hover or in the detail view.
- **Currency always has the symbol and 2 decimals.** `$49.99` not `49.99` not `4999`. Right-align currency columns in tables.
- **Tables: left-align text, right-align numbers.** This isn't style — it's readability. Decimal points and digits line up when right-aligned.
- **Truncate long text with an ellipsis**, and show the full text on hover or click. Don't let one long name blow out your layout.
- **Empty states have a message and a CTA.** Not a blank table. "No orders yet — once a customer places an order, it'll show up here."

---

## Mobile-Specific Input Rules

- **Use the right keyboard.** `inputmode="numeric"` for numbers, `inputmode="email"` for email, `inputmode="tel"` for phone. Don't make people switch keyboards.
- **Autocomplete attributes.** `autocomplete="email"`, `autocomplete="tel"`, `autocomplete="given-name"`. Let the phone fill it in.
- **Don't use hover-dependent interactions.** Tooltips on hover don't work on touch. Use inline helper text or tap-to-reveal.
- **Large tap targets.** 44px minimum height for any tappable element. Space between targets so fat-finger taps don't hit the wrong one.
- **Don't disable zoom.** Ever. Some people need it.

---

## The Test

Before shipping any form or data display, answer these:

1. Is there any raw ID, hash, timestamp, or code visible to the user? **Remove it.**
2. Is there a text field where a picker, toggle, or constrained input would work? **Replace it.**
3. Are you asking for information you could infer or already have? **Cut the field.**
4. Could two fields be combined into one? **Combine them.**
5. Would a non-technical person understand every label, every error, and every option? **Rewrite until yes.**
6. On a phone, does every input trigger the right keyboard? **Set inputmode.**
7. If the user makes a mistake, do they lose any of their other input? **They must not.**
8. Is there a dropdown with 3 options? **Make it radio buttons.**
9. Is there a displayed number without units, formatting, or context? **Add them.**
10. Is any field asking the user to match a system's format? **Make the system match the user instead.**
