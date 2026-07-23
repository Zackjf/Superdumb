---
name: audit-existing-ui
description: "Use this when reviewing or improving an existing site, app, or UI. Systematically walks every screen against ForHumans principles and produces a prioritized fix list."
---

# Audit Existing UI

When you're dropped into an existing project, you can't rewrite everything. You need to find the highest-impact problems first and fix them in order.

---

## Step 1: Understand Before Judging

Before flagging anything, complete the gate skills:

- **know-your-user**: Who uses this? What do they know? (Ask the developer if unclear.)
- **define-the-task**: What are the top 3 things users come here to do?

Without this, you'll optimize for the wrong things.

## Step 2: Walk Every Screen

Go through the codebase and identify every user-facing screen/page/view. For each one, run this checklist:

### Developer artifacts check
- [ ] Any raw IDs, UUIDs, or hashes visible?
- [ ] Any raw timestamps (ISO, Unix)?
- [ ] Any internal status codes or enum values shown as-is?
- [ ] Any `null`, `undefined`, `NaN`, `[Object object]`, or empty renders?
- [ ] Any URLs with query params, tracking codes, or internal refs displayed to users?
- [ ] Any raw error codes or stack traces surfaced?

### Raw content rendering check
- [ ] Any `dangerouslySetInnerHTML` without sanitization (DOMPurify, sanitize-html)? (XSS risk)
- [ ] Any raw HTML tags visible as text? (`<p>`, `<h2>`, `<div>` shown to users instead of rendered)
- [ ] Any raw Markdown syntax visible? (`## `, `**bold**`, `[link](url)` shown as literal characters)
- [ ] Does the editor format match the renderer? (Markdown editor → Markdown renderer, not HTML)
- [ ] Any AI-generated content rendered without sanitization?
- [ ] Any `{content}` text interpolation where the content contains HTML markup?
- [ ] Do blog/CMS pages have a preview that matches the public rendering?
- [ ] Any `alert()` or `confirm()` used instead of in-app UI components? (native browser dialogs break the design)

### Non-functional UI check
- [ ] Any search bars, buttons, or menu items that don't do anything when clicked?
- [ ] Any links to pages that don't exist? (Check footer links, nav links, CTA destinations)
- [ ] Any placeholder URLs? (Social links to `twitter.com`, `github.com`, `instagram.com` — not actual profiles)
- [ ] Any placeholder content? (Lorem ipsum, "TODO", hardcoded demo data, `@placeholder.io` email domains)

### Language check
- [ ] Any developer/technical vocabulary? ("authenticate", "initialize", "parameter", "configuration", "instance", "query", "payload", "deprecated")
- [ ] Any buttons that say "Submit", "OK", "Click here", or single generic words?
- [ ] Any headings that describe the system instead of the task? ("Account Management" vs "Your account")
- [ ] Any paragraphs of text that should be bullets or headings?
- [ ] Would a non-technical person understand every word on this screen?

### Input & form check
- [ ] Any text fields where a picker, toggle, or constrained input should be?
- [ ] Any dropdowns with fewer than 5 options? (Should be radio buttons)
- [ ] Any dropdowns with 20+ options that aren't searchable?
- [ ] Any fields asking for info that could be inferred or pre-filled?
- [ ] Any rigid format validation? (phone, URL, date requiring exact format)
- [ ] Do inputs trigger the right mobile keyboard?
- [ ] Are errors shown inline next to the field, or in a generic banner?

### Technical format exposure check
- [ ] Any cron expressions visible or editable by users? (Replace with schedule picker)
- [ ] Any regex patterns exposed? (Replace with keyword/phrase UI)
- [ ] Any JSON/config shown raw? (Replace with structured forms)
- [ ] Any raw URL inputs for images/media? (Replace with file upload/picker)
- [ ] Any file path inputs? (Replace with file browser or drag-and-drop)
- [ ] Any duration in milliseconds or raw numbers? (Replace with human units)

### Information architecture check
- [ ] What is the primary input that makes this system work? Is it reachable in 1-2 clicks from home?
- [ ] Do empty states link to the primary input action?
- [ ] How many clicks from home to each core function? Any core function at 3+ clicks?
- [ ] Does any section have 6+ sub-pages? (Likely needs consolidation into fewer screens with tabs/filters)
- [ ] Is the app organized around data entities or user tasks?
- [ ] Are outputs (dashboards, reports) more prominent than inputs (data sources, configuration)?

### Conversion & lead-gen check (for public/marketing sites)
- [ ] Is the primary conversion action (form, CTA) above the fold on the key landing page?
- [ ] Do ALL listing pages have a conversion mechanism, or are some dead ends?
- [ ] Are CTA button labels specific ("Get a free quote") or generic ("Submit", "Send")?
- [ ] Do CTA destinations stay consistent? (Don't send leisure users to /plan-trip and business users to /contact)
- [ ] Are placeholder/broken links live? (Check WhatsApp `wa.me/` links, social profile URLs, legal page links)
- [ ] Are trust signals (testimonials, stats, guarantees) placed NEAR conversion points, not on isolated pages?
- [ ] Is there a persistent contact mechanism (floating WhatsApp, chat widget, sticky CTA)?
- [ ] Do empty listing pages have CTAs, or are they dead ends ("Coming soon." with nothing to click)?

### Reuse & consistency check (codebase-level)
- [ ] Does a better component already exist in this codebase for a job being done manually? (e.g., MediaField exists but a form uses a raw ID text input; PendingButton exists but a form manually manages loading state; useConfirm exists but some deletes fire without confirmation)
- [ ] Are all destructive actions (delete, remove, archive) handled the same way? Search for all delete handlers — do they all confirm?
- [ ] Does the app have unsaved-changes protection? If a component exists for it, is it actually wired into every editor?
- [ ] Are forms with 10+ fields grouped into visual sections (fieldsets)?
- [ ] Do SEO fields (title, description) have character counters?

### Language & localization check (for non-English sites)
- [ ] Is the admin UI in the same language as the target users? (Mixed English nav + Portuguese content = inconsistency)
- [ ] Are fallback/default strings translated? (Generic "Submit" vs localized "Enviar formulario")
- [ ] Do error messages respect the user's locale?
- [ ] Are placeholder URLs and demo content replaced with real data?

### Structure & flow check
- [ ] Is there more than one primary action competing for attention?
- [ ] Could any two screens be combined into one?
- [ ] Is there a multi-step flow with no progress indicator?
- [ ] Can the user go back / undo / escape at every step?
- [ ] Are there any dead-end screens with no next action?
- [ ] Does the empty state have a message and CTA, or is it just blank?

### Feedback & trust check
- [ ] Any actions (button clicks, form submits) with no visible feedback?
- [ ] Any destructive actions with no confirmation?
- [ ] Any missing loading states?
- [ ] Any success actions with no confirmation/next-step message?
- [ ] Are error messages human-readable and helpful?
- [ ] Is there visible support/help access?

### Consistency check
- [ ] Is the same concept called different names on different screens?
- [ ] Are similar actions in different positions on different screens?
- [ ] Do similar pages use different layouts or patterns?

### Complexity / simplification check
- [ ] Any page with 10+ form fields visible at once? (Needs grouping or smart defaults)
- [ ] Any editor with 4+ tabs? (Likely over-split — can tabs be merged or eliminated?)
- [ ] Any settings page where most users would only change 1-2 things but 10+ options are shown?
- [ ] Any page with explanatory paragraphs? (The UI isn't self-evident — simplify until it is)
- [ ] Any page showing raw statistics/metrics where a verdict would suffice? (p-value → "Winner" / "Not enough data")
- [ ] Any page where the user must understand an internal concept to use it? (Can you show the outcome instead of the mechanism?)
- [ ] Any multi-field form where most fields could be smart-defaulted from org/account settings?
- [ ] Any page you'd want to redesign with half the elements? Flag it for the simplify-the-page skill.

For pages flagged for simplification, run `skills/simplify-the-page/SKILL.md` and produce a before/after wireframe with the redesign.

## Step 3: Categorize & Prioritize

Group every finding into:

### Critical (fix first)
User cannot complete their primary task, or the UI shows raw developer artifacts.
Examples:
- UUID displayed as a label
- Form clears all input on validation error
- Primary action is buried or invisible
- Raw error code shown with no explanation

### Major (fix next)
User can complete the task but the experience is confusing, slow, or trust-damaging.
Examples:
- Developer vocabulary in headings/buttons
- Wrong input type (text field for dates, dropdown for yes/no)
- No progress indicator on a 5-step flow
- 15 options on one settings page with no grouping
- No feedback after submitting a form

### Minor (fix when touching the file)
Suboptimal but functional. Fix these opportunistically, not as dedicated work.
Examples:
- Could use better microcopy on empty states
- Slightly inconsistent spacing
- Could add smart defaults to pre-fill a field
- Success message is generic ("Done!") but exists

## Step 4: Present the Issues Table

Output a table of all findings:

| Priority | Screen/Component | Issue | Fix | Skill Reference |
|---|---|---|---|---|
| Critical | Order detail page | Shows `order_id: a8f3c-91b2...` as heading | Use order number `#1234` or order title | human-friendly-inputs |
| Critical | Checkout form | 12 fields, asks for country despite geo-IP | Cut to 6 fields, auto-detect country | smart-defaults |
| Major | Settings page | 18 options in a flat list | Group into 4 sections, hide advanced | manage-cognitive-load |
| Major | All buttons | Say "Submit" | Change to action-specific labels | speak-human |
| Minor | Empty cart | Shows blank white space | Add message + "Start shopping" CTA | copy-and-microcopy |

## Step 5: Create the Implementation Plan

After the issues table, produce an **actionable implementation plan** organized into phases. This is what gets handed to the developer or coding agent to execute.

### Phase structure

Organize fixes into phases by dependency and blast radius:

**Phase 1: System-wide fixes (do first — one change, many pages fixed)**
These are changes to shared components, utility functions, or constants that fix issues across the entire app in one shot.

Example:
```
PHASE 1: System-wide fixes

1.1 Create an enum display-name map
    File: src/lib/labels.ts (create or update)
    Action: Add STATUS_LABELS, RESULT_LABELS, MODE_LABELS maps
    Fixes: Issues #1, #7, #12 (raw enums on 8+ pages)

1.2 Replace alert()/confirm() with toast/dialog
    Files: src/components/blog/PostEditor.tsx (lines 94, 101, 110)
           src/app/settings/organization/page.tsx (line 105)
    Action: Import toast from design system, replace alert() with toast()
    Fixes: Issues #8, #9

1.3 Add role="alert" to error components
    File: src/components/ui/form/FormError.tsx (line 13)
    Action: Add role="alert" to the <p> element
    Fixes: Every form validation error across the app
```

**Phase 2: Page-by-page fixes (Critical priority)**
Individual page fixes for Critical issues, organized by file so the agent touches each file once.

Example:
```
PHASE 2: Critical page fixes

2.1 Fix hero image input
    File: src/components/admin/pages/PageDetailsForm.tsx
    Line: 107-114
    Action: Replace <Input> with <MediaField> component (already exists)
    Before: <Input placeholder="ID da midia" ... />
    After: <MediaField value={heroMediaId} onChange={setHeroMediaId} label="Imagem principal" />

2.2 Fix raw proposal status on lead detail
    File: src/components/admin/leads/LeadDetail.tsx
    Line: 103
    Action: Replace {proposal.status} with PROPOSAL_STATUS_LABELS[proposal.status]
    Import: import { PROPOSAL_STATUS_LABELS } from "@/lib/labels"
```

**Phase 3: Page-by-page fixes (Major priority)**
Same format as Phase 2, for Major issues.

**Phase 4: Structural/architectural fixes**
Navigation restructuring, page consolidation, information architecture changes. These are larger refactors.

Example:
```
PHASE 4: Architecture

4.1 Consolidate sidebar navigation
    File: src/components/admin/AdminSidebar.tsx
    Action: Reduce from 28 links to 10-12 by grouping:
      - "Conteudo" (collapse: Pages, Destinations, Guides, Trips, Fairs, Team, Testimonials, Cases)
      - "Vendas" (Leads, Proposals)
      - "Configuracoes" (Settings, SEO, Redirects, Webhooks, Users, Security, Analytics)

4.2 Move Sources to top-level navigation
    File: src/components/research/research-tabs.tsx
    Action: Move Sources from tab #7 to tab #2, or promote to sidebar nav
```

**Phase 5: Polish (Minor fixes)**
Opportunistic fixes to apply when touching related files.

### Implementation plan rules

- **Group fixes by file.** If three issues affect the same file, put them in one task so the file is opened once.
- **System-wide fixes first.** A shared label map that fixes raw enums on 8 pages is more efficient than fixing each page individually.
- **Each task must be specific.** File path, line numbers, what to change, what it looked like before, what it should look like after.
- **Include the "Before → After" for copy changes.** Don't just say "fix the button label" — say `Before: "Submit" → After: "Save changes"`.
- **Estimate scope per phase.** "Phase 1: ~5 files, ~30 minutes. Phase 2: ~8 files, ~1 hour." This helps the developer plan.
- **Each phase should be independently shippable.** Phase 1 makes everything better. Phase 2 makes it better still. Don't create dependencies between phases unless necessary.

## Step 6: Execute

Work through the phases in order. After each phase:
- Verify fixes against the skills they reference
- Check that fixes didn't introduce inconsistency with other screens
- Move to the next phase

Do not attempt to fix everything at once. Targeted, specific fixes in priority order. Each phase is a shippable improvement.
