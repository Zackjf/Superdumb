---
name: user-control-and-freedom
description: "Apply when building any flow where users take actions, make choices, or move through steps. Users need undo, go back, and escape hatches at every point. Every action should feel reversible or at least confirmed before committing. Use whenever building multi-step flows, forms, destructive actions, modals, or any interaction where the user might want to change their mind."
---

# User Control & Freedom

Users make mistakes. They click the wrong thing, change their mind, explore a path they didn't mean to. If your UI punishes mistakes — by offering no way back, no undo, no escape — users become afraid to explore. A user who's afraid to click is a user who's about to leave.

The principle: every action should feel safe. Either the user can undo it, go back from it, or they were clearly warned before committing.

## Always Provide an Exit

### Go back

Every screen in a multi-step flow needs a visible "Back" or "Previous" button. Not just the browser back button — an explicit control in your UI.

- Place it consistently (usually bottom-left, or top-left as an arrow)
- Going back should restore the previous state — don't clear what they entered
- If "Back" isn't possible (after a payment is processed), explain why: "Your order has been placed. Need to make changes? Contact us."

### Close / Cancel / Dismiss

Every modal, overlay, drawer, and popover needs a clear close mechanism:
- An "X" button in a consistent position (top-right is standard)
- Clicking outside the modal to dismiss (for non-critical modals)
- The Escape key to close
- A "Cancel" text button for form modals

If a modal contains unsaved changes, warn before closing: "You have unsaved changes. Discard them?" But don't trap users — always let them leave if they choose to.

### Escape from flows

If the user is mid-way through a multi-step flow (onboarding, checkout, wizard) and wants to leave:
- Let them. Don't block navigation.
- Save their progress if possible, so they can resume later.
- If you can't save progress, warn them: "If you leave, your progress won't be saved. Leave anyway?"
- Never force the user to complete a flow. No full-screen takeovers with no close button.

## Undo

### Soft delete over hard delete

When a user deletes something, don't destroy it immediately. Use soft delete:
- Move it to a trash/archive
- Show an "Undo" option for a few seconds after the action
- Keep it recoverable for 30 days
- Only hard-delete after the retention period

**Pattern:** "Item deleted. [Undo — 10 seconds]" — a toast/snackbar with a timed undo. This is the gold standard for low-stakes deletions.

### Undo for edits

After saving changes, offer undo when practical:
- "Changes saved. [Undo]"
- Version history for documents and content
- "Revert to previous" for settings changes

### When undo isn't possible

Some actions can't be undone (sending an email, processing a payment, publishing to a live audience). For these:
- Make the irreversibility clear before the action: "This will send the email to 5,000 subscribers. This can't be undone."
- Require explicit confirmation — not just a generic "Are you sure?" but a specific description of the consequences
- Consider adding a delay: "Email scheduled. Sending in 30 seconds. [Cancel]" — Gmail's "Undo send" is a perfect example

## Confirmation for Destructive Actions

Not every action needs a confirmation dialog — that leads to confirmation fatigue where users click "Yes" without reading. Reserve confirmations for actions that are:
- **Destructive**: deleting data, removing team members, canceling subscriptions
- **Irreversible**: sending emails, publishing content, processing payments
- **High-impact**: changing permissions, modifying shared resources

### Good confirmation dialogs

- Name the specific thing being affected: "Delete project 'Summer Campaign'?" not "Are you sure?"
- Describe the consequences: "This will permanently delete the project and all 23 files inside it."
- Make the destructive button specific: "Delete project" not "Yes" or "OK"
- Make the safe option visually dominant: "Cancel" should be primary style, "Delete" should be secondary/red
- Don't default focus to the destructive button

### Bad confirmation dialogs

- "Are you sure?" — sure about what?
- "OK / Cancel" — which one is safe?
- Confirming non-destructive actions — "Are you sure you want to save?" trains users to ignore all confirmations

## Don't Trap Users

### No forced registration walls

Don't require account creation to browse content, view pricing, or explore the product. Let users see value before asking for commitment. Gate features that genuinely require an account (saving progress, personalization), not the entire experience.

### No exit-intent popups that block navigation

"Wait! Before you go..." modals that prevent the user from leaving are hostile. They communicate desperation, not value. If the user wants to leave, let them leave.

### No dark patterns

- Don't make the "decline" option confusing: "No, I don't want to save money" is manipulative
- Don't make unsubscribe harder than subscribe
- Don't disguise ads as content or navigation
- Don't pre-check opt-in boxes that the user didn't ask for

## Anti-patterns

**One-way doors with no warning.** The user clicks something and can't get back. No undo, no back button, no way to reverse. They feel trapped. Every significant action should be either reversible or clearly warned.

**Confirmation fatigue.** Every action asks "Are you sure?" — saving, editing, navigating, breathing. Users learn to click "Yes" without reading. Reserve confirmations for genuinely destructive or irreversible actions only.

**Progress-destroying back buttons.** The user fills out 3 steps of a form, hits back to change something in step 1, and all of step 2 and 3 are wiped. Going back should preserve state, not reset it.

**Full-screen takeovers with no escape.** An onboarding wizard that covers the entire screen with no close button, no skip option, and no way to access the rest of the product. The user is hostage to your flow.
