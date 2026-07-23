---
name: show-where-i-am
description: "Apply when building any multi-step flow, multi-page site, or navigation structure. Ensures users always know where they are, how they got here, and how far they have left to go. Use for onboarding flows, checkout, wizards, multi-page forms, dashboards with sub-pages, or any site with more than 3 pages."
---

# Show Where I Am

Users should never have to wonder: "Where am I? How did I get here? How much is left?" A confused user is an anxious user, and an anxious user abandons the flow.

## System Status Indicators

### Progress in multi-step flows

Any flow with more than 2 steps needs a visible progress indicator.

**What to show:**
- Current step and total: "Step 2 of 4"
- A progress bar or step indicator with labeled steps
- Which steps are complete, current, and upcoming

**What works:**
```
  ● Create account  →  ● Shipping  →  ○ Payment  →  ○ Confirm
       done              you are here      next          last
```

**What doesn't work:**
- A progress bar with no labels (what am I progressing toward?)
- Step numbers with no titles ("Step 3" — of what?)
- No indicator at all (the user has no idea if this is almost done or just starting)

### Active navigation state

The current page must be visually distinct in the navigation. Highlighted, bolded, underlined, different background — something obvious. The user glances at the nav to orient themselves. If nothing looks "active," they feel lost.

### Breadcrumbs for deep hierarchies

If your site has more than 2 levels of depth, use breadcrumbs:
```
Home > Products > Shoes > Running Shoes
```

Breadcrumbs tell the user exactly where they are in the hierarchy and let them jump back to any level with one click. Each segment should be clickable except the current page.

### Page titles that match the navigation

If the nav item says "Orders," the page heading must say "Orders" — not "Purchase History" or "Your Transactions." A mismatch between nav label and page title makes users doubt they clicked the right thing.

## Flow-Specific Patterns

### Checkout and forms

- Show step count at the top: "Step 2 of 3"
- Label each step with what it covers: "Shipping → Payment → Confirm"
- Mark completed steps as done (checkmark, filled circle)
- Allow clicking back to completed steps
- Don't reset completed steps when going back

### Onboarding

- Show completion percentage or step count
- Consider a checklist format: "3 of 5 tasks complete"
- Let users skip steps and come back (unless order matters)
- Remember where they left off if they leave and return

### Long scrolling pages

- For pages with multiple sections (like a long settings page), use a sticky section indicator or sidebar that highlights the current section as the user scrolls
- "Back to top" link when the user has scrolled far down
- Anchor links in a table of contents for very long content

## Loading and Processing States

When the system is working, tell the user:

- **Short operations (< 2 seconds):** Spinner or loading indicator, no text needed
- **Medium operations (2-10 seconds):** Spinner with a message: "Saving your changes..." or "Loading your orders..."
- **Long operations (10+ seconds):** Progress bar with estimated time or stage: "Processing payment... this usually takes about 10 seconds"
- **Background operations:** Let the user continue doing other things. Show a subtle indicator (badge, toast) when complete: "Your export is ready"

The worst loading state is none at all. The user clicks a button, nothing happens, they click again, now they've submitted twice.

## Anti-patterns

**Mystery flows.** A multi-step form with no step count. The user fills out page after page wondering "How much more?" This creates anxiety and increases abandonment.

**Dead-end pages.** A page with no clear path forward or back. No nav, no breadcrumbs, no "next" button. The user is stranded.

**Ghost navigation.** A nav bar where nothing looks selected. The user can't tell which page they're on without reading the page title — and sometimes not even then.

**Silent processing.** The user clicks "Save," nothing visible happens for 3 seconds. Did it work? Did it freeze? They click again. Now they've saved twice or created a duplicate.

**Lying progress bars.** A progress bar that jumps from 10% to 90% instantly, then sits at 90% for 30 seconds. If you can't estimate progress accurately, use an indeterminate spinner with a stage message instead.
