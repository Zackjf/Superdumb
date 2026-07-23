---
name: recognition-over-recall
description: "Apply when building any flow where users move between screens, reference previous actions, or need context from earlier steps. Users should never have to remember information from a previous screen — show it to them. Use for confirmation screens, multi-step flows, dashboards referencing other data, or any UI where the user acts on something they selected or entered earlier."
---

# Recognition Over Recall

Users can recognize things they've seen before far more easily than they can recall them from memory. Every time your UI asks "which one was it again?" — by showing a bare ID, an ambiguous reference, or a screen that forgets what just happened — you're forcing recall when you could offer recognition.

Show context. Show the thing. Don't make them remember.

## Show What They're Acting On

When a user takes an action on a specific item, show that item's details on the confirmation/action screen. Don't assume they remember.

### Examples

**Good — Canceling an order:**
> Cancel order #1234?
> Blue Running Shoes (Size 10) × 1 — $89.99
> Ordered July 20, 2026
> [Cancel this order] [Keep order]

**Bad — Canceling an order:**
> Are you sure you want to cancel?
> [Yes] [No]

Cancel WHAT? The user has to remember which order they clicked on and whether it was the right one.

**Good — Removing a team member:**
> Remove Sarah Chen (sarah@example.com) from the Marketing team?
> She'll lose access to all Marketing projects.
> [Remove from team] [Cancel]

**Bad — Removing a team member:**
> Remove this member?
> [Confirm] [Cancel]

### The rule

Any screen that acts on a specific item must display:
- The item's name/title
- Enough detail to identify it (a thumbnail, a date, a description)
- What will happen to it

## Show Context Across Steps

In multi-step flows, carry forward what the user has already entered or selected. Don't make them hold it in their head.

### Order summary persistence

During checkout, show the cart contents on every step — not just step 1. The user needs to see what they're buying while they enter shipping info and payment details. A collapsed sidebar or persistent mini-summary works.

### Form review step

Before final submission of a long form, show a summary of everything they entered:
```
Review your application:
  Name: Maria Santos
  Email: maria@example.com
  Plan: Professional ($29/mo)
  Billing: Monthly
  [Edit] [Submit application]
```

Each section should have an "Edit" link that takes them back to that specific step without losing other progress.

### Progress breadcrumbs with content

Step indicators that show what was entered, not just "Step 1 ✓":
```
  ✓ Shipping: 123 Main St, Austin TX  →  ● Payment  →  ○ Confirm
```

## Recent and Frequent Items

Help users find things they've used before without searching from scratch.

- **Recent searches**: when a search field is focused, show their last 3-5 searches.
- **Recent files/projects**: on a home screen, show recently accessed items before anything else.
- **Frequent actions**: if the user does the same 3 tasks every day, put them front and center.
- **"Order again"**: for repeat purchases, show previous orders with a one-click reorder.
- **Last-used values**: pre-fill dropdowns with the user's last selection (see smart-defaults skill).

## Make Lists Identifiable

When showing lists of items, include enough detail that the user can identify each one without clicking into it.

**Good — Order list:**
| Order | Items | Date | Status |
|---|---|---|---|
| #1234 | Blue Running Shoes (Size 10) | July 20 | Shipped |
| #1233 | Black T-Shirt (Medium), Socks | July 18 | Delivered |

**Bad — Order list:**
| Order ID | Date | Status |
|---|---|---|
| a8f3c91b-2d4e | 2026-07-20 | 2 |
| 7bc2e44a-9f1d | 2026-07-18 | 3 |

The user can't identify their order without clicking into each one. Show the product names, show human dates, show readable statuses.

## Navigation That Shows Where You've Been

- **Active states**: the current page is highlighted in the navigation
- **Breadcrumbs**: show the path for deep hierarchies (Home > Products > Shoes > Running)
- **Browser history support**: use real URLs (not hash fragments or JS state) so the browser's back button works and shows meaningful page titles in history
- **"You were here"**: for returning users, consider showing where they left off: "Continue where you left off: [Project Alpha]"

## Search That Remembers

- Show recent searches when the search field is focused
- Show search suggestions as the user types (autocomplete)
- After a search, keep the query visible in the search field so they know what they searched for
- If they navigate to a result and come back, preserve the search results (don't make them search again)
- Filter states should persist in the URL so the browser back button restores them

## Anti-patterns

**Amnesia screens.** A confirmation dialog that says "Delete this item?" without showing which item. A checkout page that doesn't show what's being purchased. A settings change that doesn't show the current value being changed. Always show the thing.

**Context-free references.** "Your request has been submitted (Ref: TKT-8847291-X)." What request? Show a summary of what they submitted, not just a ticket number.

**Blank search fields after navigation.** The user searches, clicks a result, hits back — and the search field is empty, results are gone. Preserve search state.

**"Go back and check" flows.** The user is on step 3 and needs information from step 1 to answer a question on step 3. Don't make them navigate back — show the relevant info from step 1 on step 3.
