---
name: spec-to-ux
description: "Use this when you have a technical spec, product spec, Claude spec, or requirements document and need to translate it into a human-centered UX spec with screen-by-screen wireframes. Transforms system-out thinking into user-in thinking. Produces an annotated wireframe for every screen showing what needs to be there for real humans — the primary action, the copy, the hierarchy, and what to hide. Use whenever someone says 'here's the spec, design the UX' or 'make this spec human-friendly' or 'wireframe this' or when reviewing a spec before implementation."
---

# Spec to UX

A technical spec describes what the system does. A UX spec describes what the user experiences. They are not the same thing. This skill takes a spec (product spec, technical spec, Claude spec, feature brief) and produces a screen-by-screen UX spec with wireframes, written from the human's perspective.

## The Problem This Solves

Technical specs describe features, data models, and system behavior. They say things like:
- "The user can manage their subscription settings"
- "The dashboard displays key metrics"
- "Users can CRUD team members"

These are system descriptions, not user experiences. When an AI coding agent builds directly from these specs, it produces system-centric UIs: pages organized around data models, labeled with developer vocabulary, showing everything the system knows.

This skill translates the spec into what the user actually needs to see and do.

## The Process

### Step 1: Read the spec and run the gates

Before any wireframing, run the three gate skills:

1. **know-your-user** — Who is the human using this? What do they know?
2. **define-the-task** — What are they trying to DO, in their words?
3. **study-the-landscape** — How do similar products handle this?

If the spec doesn't answer these, ask the person who gave you the spec. Don't guess.

### Step 2: Extract the user tasks

Go through the spec and translate every feature/requirement into a user task:

| Spec says | User task |
|---|---|
| "Subscription management CRUD" | "Change my plan" / "Cancel my subscription" / "Update payment method" |
| "Dashboard with KPIs" | "See how my shop is doing today" |
| "Team member management" | "Add someone to my team" / "Remove someone" |
| "Notification preferences" | "Stop getting emails I don't want" |
| "Report generation" | "Get the numbers my boss asked for" |

Notice: one spec feature often becomes 2-3 distinct user tasks. And some spec features combine into one user flow.

### Step 3: Define the screen list

Based on the user tasks (not the spec's feature list), determine the minimum screens needed:

1. List all user tasks
2. Group tasks that naturally happen together (viewing and editing a profile = one screen, not two)
3. Split tasks that have been crammed together (settings page with 20 different concerns = multiple screens)
4. Define the navigation structure
5. For each screen, state its ONE primary purpose

### Step 4: Wireframe each screen

For every screen, produce an ASCII wireframe with annotations.

## Wireframe Format

Use this structure for every screen:

```
SCREEN: [Screen Name]
PURPOSE: [One sentence — what the user comes here to do]
USER SAYS: [How they'd describe this task to a friend]

┌─────────────────────────────────────────────┐
│  [Logo]              Home  Orders  Account  │  ← nav (active item marked)
├─────────────────────────────────────────────┤
│                                             │
│  PAGE HEADING                               │  ← what this page is about
│  Subtext if needed                          │     in the user's words
│                                             │
│  ┌─────────────────────────────────────┐    │
│  │  PRIMARY CONTENT AREA               │    │  ← the main thing
│  │                                     │    │
│  │  [details, list, form, etc.]        │    │
│  │                                     │    │
│  └─────────────────────────────────────┘    │
│                                             │
│  ┌──────────┐                               │
│  │ PRIMARY  │  ← the ONE action             │
│  │  ACTION  │     (verb + noun label)        │
│  └──────────┘                               │
│                                             │
│  Secondary info / links                     │  ← less important, below
│                                             │
├─────────────────────────────────────────────┤
│  Footer / Help link                         │
└─────────────────────────────────────────────┘

ANNOTATIONS:
- [Heading]: "Your orders" (not "Order Management")
- [Primary action]: "Place an order" button, prominent, top of visual hierarchy
- [List items]: Show product name, date, status badge — NOT order_id
- [Empty state]: "No orders yet — they'll show up here after your first purchase"
- [Mobile]: Stack content vertically, primary action as sticky bottom button
```

### Wireframe annotations must include:

1. **Exact copy suggestions** — not just "heading goes here" but "Your orders" (the actual text)
2. **What data to show** — and what to hide (no IDs, no timestamps unless human-readable)
3. **Primary action** — one per screen, with the exact button label
4. **Empty state** — what this screen looks like with no data
5. **Error state** — what happens when something goes wrong
6. **Mobile behavior** — how this screen adapts on a phone
7. **What to hide** — explicit list of things from the spec that should NOT appear on this screen

### Wireframe rules

- Every screen has ONE primary action. If you're drawing two equal CTAs, split the screen.
- Headings use the user's vocabulary, not the spec's terminology.
- No developer artifacts appear anywhere (IDs, hashes, raw timestamps, enum values).
- Content follows the visual hierarchy: heading → primary content → primary action → secondary info.
- Forms use the right input types (refer to human-friendly-inputs skill).
- Every screen has a clear path forward and a way back.

## Example: Translating a Spec

### Input spec excerpt:
```
Feature: Subscription Management
- Users can view their current subscription plan
- Users can upgrade or downgrade their plan
- Users can cancel their subscription
- Users can update their billing information
- System displays billing history with invoice IDs
```

### UX translation:

This is NOT one screen. It's 3-4 user tasks:

**Task 1: "See my plan"**
**Task 2: "Change my plan"**
**Task 3: "Cancel"**
**Task 4: "Update payment method"**

Screen wireframes:

```
SCREEN: Your Plan
PURPOSE: See what plan you're on and what it costs
USER SAYS: "What plan am I on?"

┌──────────────────────────────────────────┐
│  [Logo]        Home  Shop  Account ●     │
├──────────────────────────────────────────┤
│                                          │
│  Your plan                               │
│                                          │
│  ┌────────────────────────────────────┐  │
│  │  ★ Professional — $29/month       │  │
│  │                                    │  │
│  │  ✓ Unlimited products              │  │
│  │  ✓ Analytics                       │  │
│  │  ✓ Priority support                │  │
│  │                                    │  │
│  │  Next billing date: August 1       │  │
│  │                                    │  │
│  │  [Change plan]    Cancel plan      │  │
│  └────────────────────────────────────┘  │
│                                          │
│  Payment method                          │
│  Visa ending in 4242    [Update]         │
│                                          │
│  Billing history                         │
│  July 1 — $29.00 — Paid    [Receipt]    │
│  June 1 — $29.00 — Paid    [Receipt]    │
│  May 1 — $29.00 — Paid     [Receipt]    │
│                                          │
├──────────────────────────────────────────┤
│  Need help?  Contact support             │
└──────────────────────────────────────────┘

ANNOTATIONS:
- [Heading]: "Your plan" — NOT "Subscription Management"
- [Plan display]: Show plan name, price, billing cycle, and key features.
  Do NOT show: plan_id, subscription_id, stripe_customer_id, or any internal references
- [Next billing]: Human date "August 1" — NOT "2026-08-01T00:00:00Z"
- [Change plan]: Links to plan comparison screen (see next wireframe)
- [Cancel plan]: Text link, not a button — it's secondary. Links to cancel confirmation.
- [Payment]: Show card type + last 4 digits. NOT full card number, NOT payment_method_id
- [Billing history]: Show date, amount, status. Link to receipt PDF.
  Do NOT show: invoice_id, transaction_hash, stripe_charge_id
- [Empty state for billing history]: "No billing history yet — your first bill will appear here after your next payment."
- [Mobile]: Stack everything vertically. Plan card full-width. Billing history as a simple list.
- [HIDE from this screen]: raw invoice IDs, subscription status enums, API timestamps,
  plan comparison (separate screen), detailed payment settings (separate screen)
```

## The UX Spec Document

After wireframing all screens, compile into a UX spec document:

```
# UX Spec: [Product/Feature Name]

## User
[User brief from know-your-user]

## Screen Map
[Simple flow showing how screens connect]
  Home → Orders (list) → Order (detail)
                       → Cancel order (confirmation)
       → Account → Your plan
                 → Change plan
                 → Update payment

## Screens

### 1. [Screen Name]
[Wireframe + annotations]

### 2. [Screen Name]
[Wireframe + annotations]

...

## Vocabulary Registry
[Concept → user-facing word mapping]

## Notes
[Anything that doesn't fit above — edge cases, open questions, deferred decisions]
```

## How This Connects to Implementation

The UX spec is the bridge between the technical spec and the code. When the agent starts building:

1. Each screen wireframe defines WHAT to build
2. The annotations define HOW things should appear (copy, data display, input types)
3. The "HIDE" notes prevent developer artifacts from leaking through
4. The vocabulary registry keeps terminology consistent across screens
5. The mobile notes prevent desktop-only implementations

The agent should reference each wireframe while building the corresponding screen, not the original technical spec. The UX spec IS the spec for implementation — the technical spec is the spec for the backend.

## Anti-patterns

**One wireframe per spec feature.** The spec has 8 features, so you make 8 screens. Wrong. Map features to user tasks, THEN determine screens. Some features combine. Some split. The number of screens should match the number of tasks, not the number of features.

**Wireframing the data model.** A screen for Users, a screen for Orders, a screen for Products, a screen for Settings — each showing all fields from the database table. This is system-out design. Start from what the user needs to DO, not what data exists.

**Putting spec language in the wireframes.** If the spec says "Subscription lifecycle management," your wireframe should NOT say that. It should say "Your plan." Translate every piece of spec language into user language.

**Skipping empty states and error states.** Every screen needs three wireframes in your head: the happy state (with data), the empty state (first time), and the error state (something went wrong). At minimum, annotate what the empty and error states say.

**No mobile annotation.** If you don't specify mobile behavior, the agent will build desktop-only. Every wireframe needs a mobile note, even if it's just "stack vertically, sticky CTA at bottom."
