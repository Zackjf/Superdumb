---
name: first-time-vs-returning
description: "Apply when building any product where users come back more than once. First-time users need orientation, explanation, and hand-holding. Returning users need speed, shortcuts, and memory of their last session. Build for both — the same screen can serve both by layering first-time guidance over a returning-user-optimized default. Use for home pages, dashboards, onboarding, and any screen with repeat visitors."
---

# First-Time vs. Returning

A first-time user and a returning user have opposite needs. The first-timer asks "What is this? How does it work? Where do I start?" The returner asks "Where was I? What's new? Let me get to my thing fast." Building one experience that ignores this split either confuses new users or annoys returning ones.

## First-Time User Needs

### Orient, don't overwhelm

The first visit is not the time for a feature tour, a 10-step setup wizard, or a dashboard full of empty widgets. The first-timer needs to understand three things:

1. **What this is** — one sentence, plain language. "Track your orders and manage your shop." Not "An omnichannel commerce platform for modern brands."
2. **What they can do first** — one clear starting action. "Add your first product" with a prominent button. Not six equally-weighted options.
3. **That it's going to be OK** — the interface looks approachable, not like a cockpit.

### Empty states are onboarding

The first thing a new user sees is empty: no orders, no projects, no team members. This empty state IS your onboarding. Make it count.

**Good empty state:**
> No projects yet
> Projects help you organize your work. Create your first one to get started.
> [Create a project]

**Bad empty state:**
> No data to display.

The empty state should:
- Explain what would be here (and why it's worth having)
- Give a single, clear action to create the first item
- Optionally show an illustration or example to help them visualize

### Progressive onboarding

Don't front-load a 10-step tutorial. Introduce features when the user first encounters them:
- The first time they open settings, explain what the key settings do
- The first time they create a project, walk them through it with inline guidance
- The first time they see the dashboard with data, explain what the numbers mean

This is "just-in-time" onboarding — relevant, contextual, and non-blocking.

### Skippable always

Every piece of onboarding must be dismissible. "Skip," "I'll do this later," "Don't show again." Some users learn by exploring, not by following guides. Respect that.

## Returning User Needs

### Speed and shortcuts

The returning user knows what your product does. They're here for a specific reason. Get out of their way.

- **Recent items**: show what they worked on last. "Continue where you left off: [Project Alpha]"
- **Quick actions**: surface the 2-3 things they do most often. If they check orders every morning, the orders view should be one click from the home page (or BE the home page).
- **Remembered state**: their sort order, filters, view preferences, collapsed sections — all preserved from last session.
- **Search**: prominent and fast. Returning users often know what they want by name.

### Don't re-onboard

Once a user has completed onboarding, don't show it again. Don't show "Welcome!" every login. Don't re-explain features they've used 50 times. Track what they've seen and dismiss it permanently.

Exceptions:
- New features they haven't seen (show once, dismissible)
- Important changes that affect their workflow (show once, with a clear summary of what changed)

### What's new, briefly

If something changed since their last visit, tell them — but briefly:
- A subtle badge or dot on the nav item that has new content
- A one-line banner: "New: You can now export reports as PDF. [Try it]" — dismissible
- A changelog link for users who want details

Don't: pop up a modal every time they log in. Don't: show a 5-screen "What's new" tour.

## Serving Both From the Same Screen

You don't usually need separate screens for new vs. returning users. You need one screen that layers guidance for new users over an experience optimized for returning users.

### Techniques

**Conditional empty states**: if there's data, show it normally. If there's no data (first-timer), show the helpful empty state with guidance and a CTA.

**Dismissible tips**: inline tips or callouts that explain features on first encounter, then disappear permanently after the user dismisses or interacts.

**Smart home page**: show recent/frequent items for returning users. Show a getting-started checklist for new users (that disappears as they complete items).

**Getting-started checklist** (use sparingly):
```
Getting started:
  ✓ Create your account
  ○ Add your first product
  ○ Set up shipping
  ○ Customize your store

  2 of 4 complete
```
This gives new users a clear path, shows progress (goal-gradient motivation), and disappears when complete. Returning users never see it.

## Post-Signup Redirect: Where You Land Determines Whether Users Succeed

After signup or onboarding, where does the user land? This single redirect determines whether they understand the product or churn.

**Bad:** Redirect to an empty dashboard. User sees 0 messages, 0 profiles, 0 everything. No guidance. They don't know what to do next.

**Good:** Redirect to a setup guide or getting-started checklist. User sees "Here's how to get started: Step 1, Step 2, Step 3" with their progress tracked.

If a setup guide page exists, the post-onboarding redirect MUST go there, not to an empty dashboard.

## Explain Your Product's Concepts

If your product invents its own abstractions ("Profiles", "Destinations", "Sources", "Workspaces", "Pipelines"), each concept needs a one-sentence definition the first time the user encounters it.

**Bad:** Sidebar says "Profiles" → user clicks → page says "Manage your profiles" → user still doesn't know what a profile IS.

**Good:** First time visiting the Profiles page, show: "A profile is a phone number, email, or authenticator that receives verification codes for your team." Show this as a subtle banner that can be dismissed.

Rules:
- Every invented concept gets a one-sentence definition visible on first encounter
- The definition explains what it IS, not what you can DO with it
- It appears inline on the page, not in a separate docs link
- It's dismissible — once the user understands, it goes away
- Sidebar items for non-obvious concepts should have tooltips with brief explanations

## Invite Flows Must Support New Users

When an existing user invites someone, the invited person may not have an account yet. The invite flow must handle both:
- **Existing user:** "Sign in to accept" → accept → done
- **New user:** "Create an account to accept" → signup (pre-filled email) → accept → done

If the invite page only shows "Sign in to accept" with no signup path, new users are dead-ended.

## Anti-patterns

**The eternal setup wizard.** A 10-step onboarding flow that the user must complete before seeing the product. Most users will give up. Let them in fast, guide them gradually.

**The "Welcome back!" modal.** Every single login, a popup: "Welcome back, Maria!" with nothing useful inside. After the second time, this is annoying. After the tenth, it's infuriating.

**Re-onboarding returning users.** Showing feature tours, tooltips, or tutorials to users who already know the product because the system doesn't track what they've seen.

**No memory of previous sessions.** The user set their view to "list mode" and sorted by "newest first" last time. They come back and it's reset to "grid mode" and "alphabetical." Persist user preferences.

**One-size-fits-all home page.** A dashboard that shows empty widgets to new users (confusing) and a getting-started checklist to power users (annoying). Adapt the home page based on whether the user has data and history.
