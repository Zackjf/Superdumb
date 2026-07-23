---
name: minimum-screens
description: "Use this when planning ANY page, screen, or flow. Ruthlessly reduces the number of screens, steps, and navigations the user must endure. If two screens can be one, make it one. If a separate page isn't justified, use a modal or inline pattern. Apply this before building any multi-screen flow."
---

# Minimum Screens

Every screen transition is a tax on the user's attention. They lose context, wait for a load, re-orient themselves, and sometimes lose their place entirely. The goal is the fewest screens that still make sense — not one screen crammed with everything, but no screen that doesn't earn its existence.

The reason this matters: users don't come to your product to navigate your product. They come to do a thing and leave. Every extra screen is a delay between them and done.

---

## How to Count Screens Honestly

A "screen" is anything that replaces or covers the user's current view and requires them to re-orient. Count honestly:

| This counts as a screen | This does NOT count as a screen |
|---|---|
| A new page/route | A tooltip |
| A full-page modal | A dropdown menu expanding |
| A redirect to another page | An accordion section opening |
| A step in a wizard/stepper | An inline validation message |
| A separate tab that loads new content | A confirmation toast/snackbar |
| A "are you sure?" confirmation page | A small inline confirmation ("Saved!") |
| A large modal that takes over the viewport | A popover with a few options |

Gray area: a large modal (covers >50% of screen, has its own form or content) counts as a screen. A small confirmation dialog ("Delete this item? Yes / No") is borderline — it's a screen if the user has to read and decide, but acceptable because the alternative (no confirmation on destructive actions) is worse.

**The count matters because it reveals bloat.** If your "add a team member" flow is 4 screens, something is wrong. If your "view order details" requires navigating to 3 different pages, something is wrong.

---

## The "Can This Be One Screen?" Test

For every screen in your plan, ask these five questions:

1. **Does this screen have a single, distinct purpose that differs from the screen before/after it?** If the purpose overlaps (both show user details, or both collect address info), combine them.

2. **Would combining this with the previous screen create an overwhelming amount of content?** If not — combine. A form with 6 fields does not need to be 2 screens of 3 fields each.

3. **Does the user need to see this information separately from the rest?** "Order summary" before payment is justified because the user needs to review before committing money. "Confirm your email" as a separate screen after signup is not — just show it on the success screen.

4. **Is this screen just a gateway to other screens?** A "dashboard" page that's just a list of links to actual content is a wasted screen. Put the content on the dashboard itself, or send users straight to where they need to go.

5. **Could this be a section on an existing screen instead?** Settings that live on 5 separate tabs could often be one scrollable page with sections. An "edit profile" page could be inline editing on the profile view itself.

If you can't clearly answer why this screen must exist independently, it shouldn't.

---

## Combining Techniques

When you identify screens that should merge, use these patterns:

### Inline editing vs. separate edit page

**Use inline editing when:**
- The editable content is already visible on the current page
- The edit is small (changing a name, toggling a setting, updating a single field)
- The user would lose context by leaving the page

**Use a separate edit page when:**
- The edit involves a complex form with many fields
- The edit requires a different layout than the view (e.g., rich text editor)
- There are save/cancel semantics that would confuse the view state

Example: A user profile that shows name, email, bio. Don't make them click "Edit" and go to a separate page to change their name. Make the fields editable in place — click the name, it becomes an input, they type, they save. One screen, not two.

### Accordion/expandable sections vs. separate pages

**Use accordions when:**
- You have 3-7 categories of content on one page
- Each section is relatively short (a few fields, a short list)
- Users may need to reference one section while working in another

**Use separate pages when:**
- Each section is genuinely long and complex (its own multi-field form)
- The sections serve completely different tasks
- Loading all sections at once would be slow

Example: Settings with 4 categories (Account, Notifications, Privacy, Billing). If each category has 3-5 options, put them all on one page with accordion sections or just visible sections with headers. Don't make 4 separate pages with a sidebar nav — that's 4 screens where 1 works.

### Modal/dialog vs. full page

**Use a modal when:**
- The action is quick (confirm, name something, pick an option)
- The user needs to maintain context of where they came from
- The action relates directly to something on the current page (editing a row in a table, adding an item to a list)

**Use a full page when:**
- The action is complex enough to need significant screen space
- The action is a self-contained task that doesn't relate to a specific item on the parent page
- The user needs to focus without distraction from the background

Example: "Add a team member" — a modal with name + email + role is perfect. Three fields, done, back to the team list. Don't route them to `/team/members/new` with a full page layout for three inputs.

### Tabs vs. separate pages

**Use tabs when:**
- The content shares the same context (same entity, same task)
- Users might switch between tabs in a single session
- Each tab's content loads fast

**Use separate pages when:**
- The "tabs" are actually different tasks for different purposes
- Each tab has its own heavy content that shouldn't all load at once
- The tabs have grown beyond 5-6 (that's not tabs anymore, that's navigation)

---

## When Separate Screens ARE Justified

Not everything belongs on one screen. These situations earn their own page:

### Destructive or irreversible actions
Deleting an account, canceling a subscription, transferring ownership. These deserve a dedicated confirmation screen because the user needs to pause, read, and deliberately confirm. The friction is the feature.

### Genuinely different tasks
"View orders" and "Create a product" are different tasks. They serve different goals and require different UI. Don't cram them together just to reduce screen count.

### Long forms that benefit from progressive disclosure
A mortgage application with 40 fields benefits from being broken into logical steps (Personal info, Employment, Property, Review). But each step should be substantial — 8-12 fields, not 2-3.

### Legal or compliance requirements
Payment confirmation pages, terms acceptance, identity verification. Sometimes regulations require a distinct step. Comply, but don't add extra steps beyond what's required.

### Complex review-before-commit
Checkout flows need an order review screen before payment. Users expect to see what they're about to pay for, verify quantities, and confirm totals. This is earned friction.

---

## Core Function Proximity

**How many clicks from the home page is the most important action?**

Count the clicks from the default/home screen to each core function. If the app's #1 value proposition requires 3+ clicks to reach, the information architecture is wrong.

### The proximity audit

List every core function of the app and count clicks from home:

| Core function | Clicks from home | Acceptable? |
|---|---|---|
| Review pending content | 1 (nav link) | Yes |
| Add a source (the input that drives everything) | 3 (nav → Research → Sources → Add) | NO — should be 1-2 |
| See what the engine wrote this week | 0 (on dashboard) | Yes |
| Change writing rules | 2 (nav → Admin → Writing rules) | Acceptable for admin |

**Rules:**
- The **primary task** (what the user comes back to do every day) should be 0-1 clicks. It's on the home page or one nav click away.
- The **primary input** (what feeds the system) should be 1-2 clicks from home, AND linked from empty states.
- **Secondary tasks** (settings, configuration) can be 2 clicks. That's fine.
- **Anything at 3+ clicks** must justify its depth. If it's a core function, it's too deep.

### Sub-page sprawl

When a section has 6+ sub-pages, users can't find what they need without learning your navigation structure. This is a symptom of organizing by data type instead of by task.

**The fix:** Combine related views into fewer screens using tabs, filters, or sections.

Example — a "Research" section with 9 sub-pages:
```
Before: Research → [overview, findings, trends, concerns, sources,
         companies, needs-sorting, summaries, search]  = 9 pages

After:  Research → [overview (with trends + concerns as sections),
         findings (with filters for sorted/unsorted),
         sources]  = 3 pages
```

The test: if a user said "show me the research" — could they see a useful summary on ONE screen? If they need to visit 5 sub-pages to understand what's happening, you've over-split.

---

## Anti-Patterns

### Separate view and edit pages for the same thing
The user views their profile on `/profile`, then clicks "Edit" and goes to `/profile/edit` — which shows the exact same information but in input fields. This is two screens doing one job. Use inline editing or a single page that toggles between view and edit mode.

### Settings split across many tabs or pages
Five tabs: "General", "Advanced", "Display", "Notifications", "Privacy" — each with 3-4 options. That's 15-20 settings spread across 5 screens. Put them on one scrollable page with section headers. Users can find what they need with their eyes faster than with your navigation.

### Empty "dashboard" pages that just link elsewhere
A page that says "Welcome back!" and has 4 cards linking to other pages is a speed bump, not a dashboard. Either put useful content on it (recent activity, key metrics, pending items) or route users directly to where they need to go.

### Confirmation pages that add no information
"Are you sure you want to save?" Yes. They clicked "Save." They're sure. Reserve confirmation screens for destructive actions or financial commitments — not for every routine save.

### Wizard flows for simple tasks
A 4-step wizard to create a to-do item (Step 1: Name it. Step 2: Set a date. Step 3: Choose a category. Step 4: Review and confirm). That's one form with 3 fields. One screen.

### "Success" pages with no useful content
After submitting a form, redirecting to a page that only says "Thank you! Your submission has been received." and offers nothing else — no next steps, no summary, no link back. Either put useful information on this page (what happens next, reference number, expected timeline) or show an inline success message on the same page and skip the redirect.

### Splitting a short list into list page + detail page
If your list items are simple enough (name, status, date, one action), show the details inline or in an expandable row. A separate detail page is justified only when the detail view has substantial content the list can't accommodate.

---

## Output: Screen Inventory

Before building, produce a screen inventory. For every screen in your plan:

| Screen | Purpose | Fields/Content | Justification for existing separately |
|---|---|---|---|
| Team members list | View and manage team | Member list with roles, inline remove | Primary task screen — must exist |
| Add member (modal) | Invite new member | Name, email, role (3 fields) | Modal on list page — keeps context |

Then apply the reduction pass:

1. **Start with however many screens you think you need.**
2. **Cut the count in half.** Force yourself. For each screen you're cutting, identify which remaining screen absorbs its content.
3. **For each surviving screen, justify it.** "This screen exists because ___." If the justification is weak ("it felt like it needed its own page"), merge it.
4. **Apply the navigation test.** Walk through the user's task start to finish. Every time they have to navigate somewhere else mid-task, ask: could this content have been on the screen they were already on?

The goal isn't one screen for everything. The goal is that every screen earns its place, and the user never wonders "why did I have to come to this page for this?"
