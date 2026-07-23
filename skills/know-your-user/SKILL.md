---
name: Know Your User
description: >
  GATE SKILL. Before building ANY user-facing UI, define who the actual human is.
  Not "the user" — a real person with context, knowledge gaps, and their own vocabulary.
  This skill blocks all UI work until a user brief is produced.
---

# Know Your User

This is the primary gate skill in the ForHumans framework. No UI work begins until this skill completes. Every screen, label, flow, and default traces back to the person defined here.

## What to do

### 1. Define the person

State who this human actually is. Give them a situation, not a role matrix.

Good examples:
- "A shop owner checking daily sales on her phone between customers."
- "A parent signing up their kid for soccer at 11pm after the kids are in bed."
- "A contractor submitting an invoice so he can get paid this week."

Bad examples:
- "The user."
- "An admin."
- "Stakeholders across the organization."

Be specific enough that you could picture this person in a room. If you can't, you don't know your user yet.

### 2. Determine what they already know

Almost never:
- Your data model
- Your API structure
- Technical terms like "webhook," "payload," "instance," "tenant"
- How your backend organizes information

Sometimes:
- General concepts in their own domain ("inventory," "booking," "appointment")
- How similar products work (see the study-the-landscape skill)

Always:
- What they are trying to accomplish today
- The words they use in their own life for the things your system calls something else

### 3. Determine what they do NOT know

Assume they do not know:
- Anything about how your system works internally
- What your database tables are called
- What "state" their records are in
- The difference between your system's concepts that sound similar (e.g., "workspace" vs. "project" vs. "organization")

If your system has a concept the user has never encountered, that concept should not appear in the UI. Translate it or hide it.

### 4. Map their vocabulary to yours

Make a concrete mapping. Their word goes in the UI. Your word stays in the code.

| They say | Your system calls it |
|---|---|
| "My orders" | `purchase_records` |
| "Cancel" | `subscription.status = 'cancelled'` |
| "My plan" | `billing_tier` |
| "Team" | `organization_members` |

Hard rule: when in doubt about vocabulary, pick the word a person would use when describing this task to a friend over coffee. Not the word from your schema. Not the word from your product spec. The coffee word.

### 5. Understand their context

- **Device**: Are they on a phone, tablet, or desktop? Which is most likely?
- **State of mind**: Rushed? Relaxed? Anxious? Browsing? Trying to fix a problem?
- **Environment**: At a desk with full attention? Standing in a store? On a bus? In a meeting pretending to pay attention?
- **Frequency**: Is this something they do daily, weekly, once ever? This changes how much explanation you need to provide.
- **Stakes**: What happens if they mess this up? Nothing? They lose money? Someone doesn't get picked up from school?

### 6. Produce the user brief

Write 3-5 sentences that capture this person. Every other ForHumans skill references this brief. It should be specific enough that two different developers reading it would build similar UIs.

Example:
> "Maria runs a small bakery. She checks her sales and inventory on her phone, usually during a lull in customers or at closing. She thinks in terms of 'what sold today' and 'what do I need to bake tomorrow' — not in terms of SKUs, inventory records, or analytics dashboards. She has no patience for setup flows or configuration. If something doesn't look obvious in three seconds, she'll close the app and use her notebook instead."

## Anti-patterns

**"The user is anyone who visits the site."**
This is not a user definition. It is an abdication of the job. A UI built for everyone serves no one well. Get specific. If you genuinely have multiple distinct user types, run this skill once for each type and build separate flows.

**Assuming users know what "workspace," "instance," "dashboard," or "pipeline" mean.**
These are developer/product-team words. Real people do not say "let me check my dashboard." They say "let me see how things are going." The vocabulary mapping in step 4 exists to catch this. Use it.

**Defining the user by their permissions or role in your system.**
"Admin users can manage team members and billing" describes your access control model, not a person. Who IS this admin? What are they actually trying to do today?

## Output

A user brief (3-5 sentences) written in plain language. This brief is referenced by every subsequent ForHumans skill. No UI work proceeds without it.
