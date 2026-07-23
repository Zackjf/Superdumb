# ForHumans

Build for real humans, not developers. Every UI, every label, every form, every error message.

---

## Hard Rules (never break these)

These are non-negotiable. Memorize them. Apply them to every piece of UI you write.

1. **No developer artifacts in the UI.** No IDs, hashes, UUIDs, raw timestamps, status codes, enum values, error codes, or raw `error.message`. Ever. Map every internal value to a human word before displaying it.
2. **Every button says what it does.** "Save changes", "Send message", "Book this class". Never "Submit", never "OK", never "Click here".
3. **One primary action per screen.** If you have two equally-weighted CTAs, you have zero.
4. **The user's word wins.** If users call it "orders" and your data model calls it "transactions", the UI says "orders."
5. **Don't ask what you already know.** If you can infer it, pre-fill it, or skip it — do that.
6. **No paragraph text in UI.** If it's more than 2 sentences on a UI screen, rewrite as bullets, headings, or cut it.
7. **Every action gets feedback.** Click a button, something visible happens. Always. Loading state → success/error.
8. **Forms never clear on error.** The user's input is sacred. Show what's wrong, let them fix just that.
9. **Never render raw error.message in production.** Log it. Show the user a human message with a recovery path.
10. **Never use alert() or confirm().** Use in-app toasts, banners, and dialog components that match your design system.
11. **Never link to pages that don't exist.** No nav items, footer links, or CTAs pointing to unbuilt pages. Remove them until implemented.
12. **Never show non-functional UI.** No search bars without handlers, no buttons without onClick, no placeholder data presented as real. If it doesn't work yet, don't render it.
13. **Images and media are file uploads, not URL text fields.** Users have files on their device, not CDN URLs in their clipboard.
14. **No raw HTML tags or Markdown syntax visible to users.** Sanitize all rendered content. Never use dangerouslySetInnerHTML without DOMPurify or equivalent.

---

## When This Applies

These skills apply whenever you are building, modifying, or reviewing any user-facing UI — pages, forms, text, errors, empty states. They do NOT apply to developer tools, CLIs, or backend code that never reaches users.

---

## The 5 Skills That Matter Most

If you read nothing else, apply these five on every UI task:

1. **`skills/speak-human/`** — every word in the user's language, no jargon
2. **`skills/human-friendly-inputs/`** — right input types, no dev artifacts, no raw HTML rendering
3. **`skills/graceful-failure/`** — every failure mode gets a human message and recovery path
4. **`skills/manage-cognitive-load/`** — 3-4 choices max, nav max 8-10 items, group forms after 8 fields
5. **`skills/consistency/`** — same words and patterns everywhere, vocabulary registry

---

## The Full Process

### Phase 1: GATES (before building any UI)

Complete these before writing UI code. Do not skip them for "simple" pages.

1. **`skills/know-your-user/`** — Who is this person? What do they know? What words do they use?
2. **`skills/define-the-task/`** — What are they trying to DO? What's the primary input that feeds the system?
3. **`skills/study-the-landscape/`** — How do 2-3 competitors handle this? What patterns do users expect?

Present all three to the user for approval before proceeding.

### Phase 2: BUILD (apply relevant skills while coding)

**Every UI task:**
- `speak-human` — user's language, domain jargon translated
- `human-friendly-inputs` — right inputs, no dev artifacts, no raw HTML, sanitize content
- `consistency` — vocabulary registry, same patterns everywhere
- `graceful-failure` — every catch block has a human message, every error has a recovery path

**Pages/screens:**
- `minimum-screens` — fewest steps, core functions within 1-2 clicks of home
- `scannable-not-readable` — headings + bullets, no paragraphs
- `manage-cognitive-load` — 3-4 choices, nav max 8-10, form sections after 8 fields
- `use-familiar-patterns` — solved problems use solved UI

**Flows (multi-step, onboarding, checkout):**
- `show-where-i-am` — progress indicators, breadcrumbs, active states
- `first-time-vs-returning` — orient new users (redirect to setup guide, not empty dashboard), speed up returning users
- `user-control-and-freedom` — undo, back, escape hatches
- `peak-and-finish-strong` — great endings, one moment of delight

**Forms:**
- `smart-defaults` — infer, pre-fill, reduce fields
- `prevent-errors` — constrain inputs, validate inline on blur, no non-functional UI

**Data and feedback:**
- `action-feedback` — every click responds
- `copy-and-microcopy` — empty states, loading, errors, confirmations
- `trust-and-reassurance` — pricing transparency, support visible, trust signals near conversion
- `recognition-over-recall` — show context across screens

**Layout:**
- `accessible-by-default` — 44px targets, contrast, keyboard nav, works one-handed

**When a page feels overcomplicated:**
- `simplify-the-page` — reimagine with half the fields, smarter defaults, outcomes over mechanisms

### Phase 3: REVIEW (after building)

Run `skills/outsider-review/` — walk every screen as a first-timer, a rusher, a non-technical person, and a phone user.

---

## Special Modes

### Spec-to-UX
When given a tech/product spec: run `skills/spec-to-ux/` to translate into a UX spec with screen-by-screen ASCII wireframes, user vocabulary, and what to hide.

### Audit Existing UI
When reviewing an existing project: run `skills/audit-existing-ui/` for a systematic walkthrough with prioritized fix table AND phased implementation plan (system-wide fixes → critical page fixes → major → architecture → polish).

### Simplify
When a page works but is overcomplicated: run `skills/simplify-the-page/` for a before/after redesign with fewer fields, smarter defaults, and outcomes over mechanisms.

---

## All Skills (27)

| Phase | Skill | One-line purpose |
|---|---|---|
| Gate | `know-your-user` | Who is this person and what words do they use? |
| Gate | `define-the-task` | What are they trying to DO? What's the primary input? |
| Gate | `study-the-landscape` | How do competitors solve this? |
| Build | `speak-human` | No jargon. Domain translation tables. User's word wins. |
| Build | `human-friendly-inputs` | Right inputs, no dev artifacts, no raw HTML, sanitize content |
| Build | `consistency` | Vocabulary registry. Same word = same thing everywhere. |
| Build | `minimum-screens` | Fewest screens. Core functions 1-2 clicks from home. |
| Build | `scannable-not-readable` | Headings + bullets. No paragraphs on UI screens. |
| Build | `manage-cognitive-load` | 3-4 choices max. Nav max 8-10. Group forms after 8 fields. |
| Build | `use-familiar-patterns` | Solved problems use solved UI. |
| Build | `smart-defaults` | Infer, pre-fill, default from org/account settings. |
| Build | `prevent-errors` | Constrain inputs. Validate inline. No non-functional UI. |
| Build | `copy-and-microcopy` | Empty states, loading, errors, confirmations, tooltips. |
| Build | `action-feedback` | Every action responds. Loading → success/error. |
| Build | `trust-and-reassurance` | Pricing, reversibility, support visible, trust near conversion. |
| Build | `graceful-failure` | Every failure mode: human message + recovery path + preserved state. |
| Build | `show-where-i-am` | Progress bars, breadcrumbs, active nav, step counts. |
| Build | `first-time-vs-returning` | Orient new, speed up returning. Setup guide after signup. |
| Build | `user-control-and-freedom` | Undo, back, escape. Every action reversible or confirmed. |
| Build | `peak-and-finish-strong` | Great endings. One moment of delight. |
| Build | `recognition-over-recall` | Show context. Don't make users remember across screens. |
| Build | `accessible-by-default` | 44px targets, contrast, keyboard nav, works one-handed. |
| Build | `simplify-the-page` | Reimagine with half the fields. Outcomes over mechanisms. |
| Review | `outsider-review` | Walk as first-timer, rusher, non-technical, phone user. |
| Special | `spec-to-ux` | Tech spec → UX spec with ASCII wireframes per screen. |
| Special | `audit-existing-ui` | Systematic audit → phased implementation plan. |
| Special | `generous-inputs` | Accept any format, parse generously (Postel's Law). |
