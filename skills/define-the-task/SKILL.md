---
name: Define the Task
description: >
  GATE SKILL. After knowing the user, define what they are trying to DO.
  Not what features exist — what is the job-to-be-done, stated in the user's own words.
  This skill blocks UI work until the task, happy path, and "done" state are defined.
---

# Define the Task

This skill runs after "Know Your User." You have a user brief. Now define the single thing they are trying to accomplish on this screen or in this flow.

## What to do

### 1. State the task the way the user would say it

Say it in first person, the way the user would describe it to a friend.

Good examples:
- "I want to cancel my subscription."
- "I need to see what sold today."
- "I want to book a table for Saturday."
- "I need to add someone to my team."

Bad examples:
- "The user manages subscription lifecycle."
- "This page provides CRUD operations on the booking entity."
- "Users can view, edit, and delete team member records."
- "The dashboard surfaces key performance indicators."

If you can't state the task in one plain sentence, you don't have one task. You have several. Split them.

### 2. Define the happy path

The happy path is the simplest possible route from "I want to do this" to "It's done." Not the most robust route. Not the route that handles every edge case. The path where everything goes right.

Write it as 3-5 steps maximum. If it takes more than 5 steps, something is wrong — you're either combining tasks or adding unnecessary steps.

Example — "I want to cancel my subscription":
1. User taps "Cancel subscription" on their account page.
2. System asks "Are you sure?" with one sentence explaining what happens next.
3. User confirms.
4. System cancels and shows confirmation with the date service ends.

That's it. Four steps. Not a retention flow. Not a survey. Not three modal dialogs explaining what they'll lose. The happy path is: they want to cancel, let them cancel.

### 3. Identify the minimum information needed

For every piece of information you plan to ask the user for, ask yourself:
- **Can it be inferred?** If they're logged in, you already know who they are. Don't ask for their email.
- **Can it be defaulted?** Most people want the standard option. Default to it and let the rare exception change it.
- **Can it be skipped entirely?** If it's not strictly required to complete the task, drop it. You can always ask later.
- **Can it be asked later?** Collect the minimum to get started. Progressive disclosure beats upfront interrogation.

Every field, every dropdown, every checkbox is friction. Justify each one. "It would be nice to know" is not justification. "We literally cannot complete this task without it" is.

### 4. Define what "done" looks like for the user

Not "record updated in the database." Not "API returns 200." What does the user SEE that tells them the thing they wanted to do is now done?

Good examples:
- "A confirmation screen that says 'Your subscription has been cancelled. You have access until July 30.'"
- "The new team member appears in the list with a 'Pending invite' badge."
- "The booking shows up on their upcoming reservations with the date, time, and party size."

Bad examples:
- "The entity is persisted."
- "A success toast notification appears."
- "The user is redirected to the list view."

The "done" state should give the user confidence that the thing happened and tell them anything they need to know next (when does it take effect? do they need to do anything else? can they undo it?).

### 5. One task, one page

If you find yourself writing "This page lets users manage their account settings, view billing, update preferences, and configure notifications" — stop. That is four tasks:

1. Update account settings
2. View billing
3. Update preferences
4. Configure notifications

Each one gets its own pass through this skill. Each one gets its own happy path. They might live under the same navigation section, but they are separate tasks with separate screens or flows.

The test: can a user land on this page and immediately know what to do? If the answer is "it depends on what they're here for," you have too many tasks on one page.

## Output

Produce all three of these:

1. **One sentence** starting with "The user wants to..." that states the task in their words.
2. **The happy path** in 3-5 numbered steps.
3. **The "done" state** — what the user sees that tells them it worked.

Example:

> **Task**: The user wants to cancel their subscription.
>
> **Happy path**:
> 1. Tap "Cancel subscription" on the account page.
> 2. See a confirmation prompt explaining when service ends.
> 3. Confirm cancellation.
> 4. See a confirmation screen with the end date.
>
> **Done**: The user sees "Your subscription has been cancelled. You have access until [date]." They feel certain it's done and know when access stops.

### 6. Identify the primary input

Every app has outputs (dashboards, reports, content, results) and inputs (the data, configuration, or sources that make the outputs possible). The primary input is the thing without which the whole system produces nothing.

Ask: **"What does the user need to feed this system for it to do its job?"**

Examples:
- A content engine that monitors trends → the primary input is **sources** (what sites/communities to watch). No sources → no research → no findings → no content. This should be prominent, not buried.
- An analytics dashboard → the primary input is **connecting data** (linking accounts, adding tracking). No data → empty dashboard.
- A CRM → the primary input is **adding contacts**. No contacts → nothing to manage.
- An email tool → the primary input is **importing a list** or **writing the first email**.

**The primary input should be as prominent as the primary output.** If the dashboard is the home page but "add a source" is buried 3 clicks deep, the information architecture is backwards. The thing that makes the system work should be one of the first things a new user sees, and easily reachable for returning users.

When the dashboard shows "No data yet" or "First run pending" — that empty state MUST link directly to the primary input action. Don't just say "data will appear after the first scan." Say "Add your first source to get started" with a direct link.

## Anti-patterns

**Burying the primary input.**
The system's outputs (dashboard, reports, generated content) are prominent. But the inputs that make those outputs possible (sources, data connections, configuration) are hidden in a sub-menu 3 clicks away. If the user can't easily feed the system, the system produces nothing. Input prominence must match output prominence.

**Combining multiple tasks into one page or flow.**
"This page lets users manage their account settings, view billing, update preferences, and configure notifications." That is four separate tasks wearing a trench coat pretending to be one. Separate them.

**Defining the task in system terms.**
"CRUD operations on the subscription entity" is not a task. It is an implementation detail. The user does not want to "perform CRUD operations." They want to cancel, or change their plan, or check when they'll be billed next. Each of those is a distinct task.

**Overloading the happy path with edge cases.**
The happy path is not where you handle "but what if their payment method is expired and they're in a team plan and they have a pending refund." Handle edge cases, yes — but define the happy path first, cleanly, without conditionals. Edge cases are branches off the happy path, not part of it.

**Asking for information you don't need.**
If completing the task requires two fields, show two fields. Not six fields with four marked "optional." Optional fields are still friction. They still make the user pause and wonder "should I fill this in?" Remove what you don't need.
