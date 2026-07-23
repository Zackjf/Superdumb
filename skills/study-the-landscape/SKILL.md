---
name: Study the Landscape
description: >
  GATE SKILL. Before building, look at how real products solve this same problem.
  Users arrive with expectations shaped by every other product they use.
  This skill blocks UI work until a landscape brief is produced.
---

# Study the Landscape

This skill runs after "Know Your User" and "Define the Task." You know who the person is and what they're trying to do. Now find out how the rest of the world already solves this problem — because your user has seen those solutions and will expect yours to rhyme with them.

## Why this matters

Jakob's Law: users spend most of their time on OTHER sites. They expect your site to work like the ones they already know. Every time you deviate from an established pattern, you create friction — even if your way is objectively better. The user has to stop, figure out what's different, and learn your way. Most won't bother.

This doesn't mean copy everything. It means know what you're deviating from, and only deviate when the benefit is clear and obvious.

## What to do

### 1. Identify the closest real-world products

What products do this same task (or a very similar one) for a similar audience? Think broadly:

| If you're building... | Look at... |
|---|---|
| Booking / scheduling | Calendly, OpenTable, Resy, Google Calendar |
| Ecommerce / checkout | Amazon, Shopify stores, Apple Store |
| Messaging / chat | iMessage, WhatsApp, Slack, Discord |
| File management | Dropbox, Google Drive, Finder/Explorer |
| Invoicing / billing | Stripe Dashboard, FreshBooks, Square |
| Forms / signup | Typeform, Google Forms, any major SaaS signup |
| Settings / preferences | iOS Settings, Gmail Settings, Spotify account |
| Search | Google, Amazon search, Airbnb search |
| Dashboards / reporting | Shopify admin, Google Analytics, bank apps |

Pick 2-3 that are most relevant to your user and task. Prioritize products your specific user is likely to have used (refer to the user brief from "Know Your User").

### 2. Review how they solve it

For each competitor or analogous product, examine (fetch their pages if needed):

- **Vocabulary**: What words do they use for key actions and concepts? ("Book" vs. "Reserve" vs. "Schedule"? "Cancel" vs. "End" vs. "Stop"?)
- **Flow length**: How many steps from intent to done? Count clicks, screens, and form fields.
- **UI patterns**: What components do they use? (Modals? Inline editing? Separate pages? Step wizards? Single scrolling page?)
- **Information hierarchy**: What's shown prominently vs. tucked away? What's above the fold?
- **Default state**: What does the screen look like before the user does anything? Empty state? Pre-populated? Example data?
- **Confirmation and feedback**: How do they tell the user "it worked"? (Inline confirmation? Redirect? Toast? Email?)
- **Mobile behavior**: How does it work on a phone? Is it the same flow or simplified?

### 3. Find the patterns

After reviewing 2-3 products, sort what you found into three categories:

**Things they all agree on (table stakes).**
If every booking product shows date, time, and party size on the confirmation screen, you must too. These are not features — they are baseline expectations. Omitting them will feel broken.

**Things they all differ on (opportunities).**
If every checkout flow handles gift options differently, there's no established pattern. This is where you have room to do something better without fighting user expectations.

**Things they get wrong (lessons).**
Filter what you see through the other ForHumans skills. If every competitor buries cancellation behind five screens, that's not a pattern to copy — it's a dark pattern to avoid. The landscape study informs you, but "Know Your User" and "Define the Task" override it when competitors are hostile to their users.

### 4. Produce the landscape brief

Write a concise brief that captures your findings. This gets referenced during UI implementation.

Example:

> **Landscape brief — Cancel subscription flow**
>
> Reviewed: Spotify, Netflix, NYT.
>
> **Expected patterns (table stakes)**:
> - "Cancel" link is in Account or Subscription settings
> - Confirmation screen shows when access ends
> - User can still access service until end of billing period
> - Cancellation is reflected immediately in account status
>
> **Common vocabulary**:
> - "Cancel subscription" (not "terminate," "end," or "deactivate")
> - "You'll have access until [date]"
> - "Restart" or "Resubscribe" (for re-activation)
>
> **Typical flow**: 2-4 steps (find cancel link, confirm, done)
>
> **Where competitors differ**:
> - Retention offers (Spotify asks why you're leaving; Netflix does not)
> - Some show a survey, some don't
> - Some require multiple confirmation clicks, some just one
>
> **Where competitors get it wrong**:
> - NYT historically made cancellation require a phone call (dark pattern, do not copy)
> - Some bury the cancel link deep in settings behind misleading labels
>
> **Recommendation**: Keep it to 2-3 steps. Use "Cancel subscription" as the label. Show the access end date on confirmation. Skip the retention survey — it serves the company, not the user.

## When to deviate from the landscape

You may deviate from established patterns when ALL of these are true:

1. You have a clear, specific reason (not "it's more elegant" or "it's more innovative").
2. The benefit to the user is obvious and immediate — they will notice and appreciate the difference.
3. The deviation does not require the user to learn a new interaction model.
4. You've checked with the user brief — this deviation works for THIS person in THIS context.

"It's cleaner" is not a reason. "It saves two steps for a user who does this ten times a day" is a reason.

## Anti-patterns

**Building in a vacuum.**
Not looking at what exists means you'll either accidentally reinvent something worse or violate expectations your user already has. Spend 15 minutes looking before spending hours building.

**Copying everything, including the bad parts.**
The landscape study is research, not a blueprint. If every competitor has a confusing settings page, that's not validation — it's an opportunity. Always filter what you find through the other ForHumans skills. "Everyone does it this way" is not sufficient justification if "this way" is hostile to the user.

**Only looking at direct competitors.**
If you're building a booking flow for a dog groomer, don't only look at other pet-grooming apps (there may not be good ones). Look at Calendly, OpenTable, or any well-executed booking flow. The task pattern matters more than the industry.

**Treating this as a competitive analysis document.**
This is not a strategy deck. You don't need market positioning or feature matrices. You need to know: what will the user expect to see, what words will they expect, and how many steps will feel normal? Keep it practical.

## Output

A landscape brief containing:
- Products reviewed (2-3)
- Expected patterns (table stakes the user will assume exist)
- Common vocabulary (the words the user has been trained to expect)
- Typical flow length (how many steps feel normal)
- Where competitors agree (do not deviate here without strong reason)
- Where competitors differ (your room to improve)
- Where competitors get it wrong (opportunities, not patterns to copy)
