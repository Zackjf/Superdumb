---
name: action-feedback
description: "Use this whenever a user clicks, taps, submits, saves, deletes, toggles, or performs ANY action in the UI. Every single action must produce visible feedback. No silent actions. If the user does something and nothing visibly changes, they WILL click again, panic, or leave."
---

# Action Feedback

Every action a user takes must produce a visible response. Every single one. No exceptions.

When someone clicks a button and nothing happens, three things go through their mind in rapid succession: "Did it work?" then "Is it broken?" then "Should I click again?" That uncertainty — even for half a second — erodes trust. Do that enough times and the user stops trusting your product entirely.

The principle is simple: the user acts, the interface responds. Always. Immediately. Visibly.

---

## Why Immediate Feedback Matters

Human perception of speed works in thresholds:

- **Under 100ms**: feels instant. The user perceives no delay. This is the target for direct-manipulation feedback (button press, toggle, checkbox).
- **100ms to 1 second**: feels responsive. The user notices a brief pause but stays in flow. Acceptable for actions that involve a server round-trip.
- **1 to 10 seconds**: feels slow. The user's attention starts to wander. You need a progress indicator or at minimum a spinner with context.
- **Over 10 seconds**: feels broken. The user will leave, refresh, or click the button again (causing duplicate actions). You need a progress bar, status updates, or a "we'll notify you when it's done" pattern.

These aren't style preferences. They're how human brains process interaction. Your UI needs to respect these thresholds or it will feel broken even when it's working perfectly.

---

## Button Clicks

When a user clicks a button, three things happen in sequence: the click, the processing, and the result. Each phase needs its own feedback.

### Phase 1: Acknowledge the click (immediate, under 100ms)

The button should visually respond the instant it's clicked. This is usually handled by CSS `:active` states, but make sure it's noticeable. The user needs to see that their click registered.

- Button shows a pressed/depressed state.
- If the button triggers an async operation, immediately transition to a loading state.

### Phase 2: Show processing (if it takes more than ~300ms)

- Replace the button text with a loading indicator: a small spinner inside the button, or the text changes to something like "Saving..." or "Sending..."
- Disable the button to prevent double-clicks. But keep the loading state visible — a disabled button with no explanation looks broken.
- Don't just show a generic spinner somewhere else on the page. The feedback should be on or near the thing the user interacted with.

### Phase 3: Show the result

- **Success**: the button returns to normal (or changes to a brief success state like a checkmark), and a confirmation message appears. The message should be specific: "Changes saved" not "Success."
- **Error**: the button returns to its clickable state, and an error message appears inline explaining what went wrong and how to fix it.

### Before / After

| Before (bad) | After (good) |
|---|---|
| Button says "Save." User clicks. Nothing visible changes. Data saves silently in the background. | Button says "Save changes." User clicks. Button shows spinner + "Saving..." text. After save completes, button briefly shows checkmark, and a "Changes saved" message appears. |
| Button says "Submit." User clicks. Page reloads 2 seconds later. | Button says "Send application." User clicks. Button shows "Sending..." and disables. After success, user sees "Application sent! We'll get back to you within 2 business days." |

---

## Form Submissions

Forms are high-stakes interactions. The user has invested time filling in fields. They need to know their effort landed.

### Rules

- After successful submission: show a clear success message on the same page OR redirect to a result page with confirmation. If you redirect, the new page must make it clear the submission worked.
- The success message must say what happened and what comes next. "Your application has been submitted. We'll email you within 2 business days" not "Form submitted."
- If the form stays on screen after submission (like a settings page), clear indication of what changed. A "Saved" indicator, a brief success banner, a timestamp update.
- If submission fails: show errors inline next to the fields that have problems. Scroll to the first error if it's off-screen. Never clear the form. Never lose the user's input.
- If the form triggers a background process (like sending an email or starting an import): tell the user that it started and how they'll know when it finishes.

### Before / After

| Before (bad) | After (good) |
|---|---|
| Form submits, page reloads, user is back at a blank form with no message. Did it work? | Form submits, green banner appears: "Your message has been sent. We typically respond within 24 hours." |
| Form submits, error appears at the top of the page: "Validation error." Which field? | Inline error appears below the email field: "That email doesn't look right — check for typos?" Scrolls to the error. All other input preserved. |

---

## Delete and Destructive Actions

Destructive actions deserve extra care because they can't easily be undone. The user needs to know exactly what they're about to destroy, and they need confirmation that it happened.

### Rules

- **Before the action**: show a confirmation dialog that names the thing being deleted and describes the consequences. "Delete 'Q3 Marketing Plan'? This removes the project and all 24 tasks inside it. You can't undo this." Use specific names and numbers, not "this item."
- **The confirm button says what it does**: "Delete project" not "OK" or "Yes." The dismiss button is clearly lower-emphasis: "Keep project" or "Cancel."
- **After the action**: show a result message. "Project deleted." If undo is possible, include an undo option: "Project deleted. [Undo]" — keep the undo available for at least 10 seconds.
- **The deleted item disappears from the list/view**. Don't make them refresh to see the change.
- **If the deletion affects other things** (cascade deletes, team access changes), say so in the confirmation dialog, not after the fact.

### Before / After

| Before (bad) | After (good) |
|---|---|
| User clicks delete icon. Item vanishes instantly. No confirmation, no undo. | User clicks delete. Dialog: "Remove 'Sarah Chen' from the team? She'll lose access to all shared projects." [Remove] [Cancel]. After removal: "Sarah Chen has been removed. [Undo — 10 sec]" |
| "Are you sure?" [OK] [Cancel] | "Delete 'Q3 Report'? You can't undo this, and Alex and Jordan will lose access to it too." [Delete report] [Keep report] |

---

## Save Actions

Saving should feel effortless and certain. The user should never wonder whether their changes were saved.

### Rules

- **Explicit save (user clicks a button)**: the save button shows a loading state, then a "Saved" confirmation. Brief and clear.
- **Auto-save**: show a small, non-intrusive indicator. "Saving..." while it saves, then "Saved" or "All changes saved" with a timestamp or relative time ("Saved just now", "Last saved 2 minutes ago"). Place it near the content being edited, not in a toast that disappears.
- **Save failure**: if auto-save fails, make it very visible. "Couldn't save — check your connection." Don't silently lose their work. If possible, keep retrying in the background and tell them when it recovers: "Back online — changes saved."
- **Unsaved changes warning**: if the user tries to navigate away with unsaved changes, warn them. "You have unsaved changes. Leave without saving?" This is the browser's `beforeunload` event, but also handle it in your SPA router.

### Before / After

| Before (bad) | After (good) |
|---|---|
| User edits a document. No save indicator anywhere. They close the tab and hope it saved. | Subtle indicator in the header: "Saving..." then "All changes saved" with a small checkmark. |
| User clicks "Save." Nothing happens. Data was saved, but no feedback. | User clicks "Save changes." Button shows spinner, then "Saved!" for 2 seconds, then returns to "Save changes." |
| Auto-save fails silently. User's last hour of work is lost. | "Couldn't save your changes — you seem to be offline. We'll keep trying." Then, when connection returns: "Back online. All changes saved." |

---

## Background Operations

Some actions kick off processes that take time: importing data, generating reports, sending bulk emails, processing uploads. The user needs to know what's happening even when the operation runs in the background.

### Rules

- **If it takes 2-10 seconds**: show a progress indicator. A progress bar is better than a spinner because it communicates how much is left. If you can't calculate progress, use an indeterminate progress bar with a text status: "Processing 847 records..."
- **If it takes more than 10 seconds**: let the user do other things. Show the progress in a non-blocking way (a status bar, a notification area, a persistent banner). "Your import is running — we'll notify you when it's done. You can keep working."
- **If it takes minutes**: send a notification (in-app, email, or both) when it completes. Show a persistent status somewhere they can check: "Import started at 2:15 PM — processing 12,000 records. We'll email you when it's ready."
- **Never leave the user staring at a screen waiting**. If it takes more than a few seconds and they can't do anything else, your UX architecture needs rethinking.
- **Show results when done**. "Import complete: 847 records imported, 3 skipped (see details)." Link to the result.

### Before / After

| Before (bad) | After (good) |
|---|---|
| User clicks "Import CSV." Spinner shows. 45 seconds of nothing. Then a blank page. | User clicks "Import." Progress bar shows: "Importing... 234 of 847 records." On completion: "Import complete! 847 records imported, 3 skipped. [View details]" |
| User clicks "Generate report." Nothing happens for 20 seconds. Then a PDF downloads with no warning. | "Generating your report — this usually takes about 30 seconds. We'll let you know when it's ready." 30 seconds later: "Your report is ready. [Download PDF]" |

---

## Error Feedback

When something breaks, the user needs to know immediately, specifically, and at the point where it broke.

### Rules

- **Show errors inline**, next to the element that caused the problem. Not just in the console. Not just in a banner at the top of the page.
- **Be specific**. "That phone number needs an area code" not "Invalid input."
- **Offer a fix**. Tell them what to do. "Try again" or "Check your connection" or "Use a different email address."
- **Don't let errors disappear**. Toast notifications that vanish after 3 seconds are terrible for errors. The user might be looking somewhere else. Errors should persist until the user has addressed them or dismissed them.
- **For network/server errors**: own it. "Something went wrong on our end. Try again in a minute." Don't blame the user for your server crash.
- **For validation errors on submit**: scroll to the first error. Highlight all fields with errors. Show a summary if there are multiple: "3 fields need your attention" with inline messages on each.

### Before / After

| Before (bad) | After (good) |
|---|---|
| `console.log("Error:", err)` and nothing in the UI. | Inline error message appears next to the affected element with guidance on how to fix it. |
| Red banner: "An error occurred." | Specific inline message: "We couldn't charge your card. The expiration date might be wrong — double-check it?" |
| Toast that appears for 2 seconds: "Error saving." Then disappears. User was looking at another field. | Persistent error below the save button: "Couldn't save — your session may have expired. [Reload page]" |

---

## Loading States

Loading is the space between action and result. Fill that space with useful information, not blank screens.

### The hierarchy (best to worst)

1. **Skeleton screens**: gray placeholder shapes that mimic the layout of the content that's loading. They tell the user what's coming and make the wait feel shorter because the page looks "almost ready."
2. **Contextual spinners with text**: a small spinner near the content being loaded with a message like "Loading your orders..." Tells them what's happening.
3. **Generic spinners**: a centered spinner with no context. Better than nothing, but barely. The user doesn't know what's loading or how long it will take.
4. **Blank screen**: the worst option. The user sees nothing and assumes the page is broken.

### Rules

- Never show a blank screen while content loads. Something should always be visible — a skeleton, a spinner, a message.
- Show skeleton screens for content areas (lists, cards, feeds). Show spinners for small components or actions.
- If a specific section of the page is loading while the rest is ready, only show the loading state on that section. Don't block the whole page.
- For initial page loads: show the page chrome (nav, header, sidebar) immediately and load content areas independently.

### Before / After

| Before (bad) | After (good) |
|---|---|
| Blank white screen for 2 seconds, then everything appears at once. | Navigation and page structure appear immediately. Content area shows skeleton screens. Content fades in as it loads. |
| Full-page spinner blocking everything. | Only the content area that's loading shows a spinner. Nav and other page elements are interactive. |

---

## The "Nothing Happened" Anti-Pattern

This is the most common feedback failure: the user clicks a button that does something invisible (sends an email, updates a backend record, triggers a webhook) and nothing on screen changes.

### Why it's dangerous

- The user doesn't know if it worked.
- They might click again, causing duplicate actions (two emails sent, two charges processed).
- They lose trust in the product. "Is this thing even doing anything?"

### How to fix it

Every action, even ones that have no visible UI result, must produce visible feedback:

| Invisible action | Visible feedback needed |
|---|---|
| Sending an email | "Email sent to alex@example.com" |
| Syncing data | "Syncing... Done. Last synced: just now." |
| Copying to clipboard | "Copied!" (brief confirmation near the copy button) |
| Adding to favorites | Heart icon fills in + brief "Added to favorites" |
| Toggling a setting | Toggle animates + "Setting saved" |
| Triggering a background job | "Export started — we'll email you when it's ready." |
| Resending an invite | "Invite resent to sarah@example.com" |

---

## Timing Summary

| Response time | User perception | Required feedback |
|---|---|---|
| 0-100ms | Instant | Visual press/click state (CSS transition, active state) |
| 100ms-1s | Responsive | Brief loading indicator on the control (spinner in button, subtle animation) |
| 1-10s | Noticeable delay | Progress indicator with context ("Saving your changes...") |
| 10s-1min | Long wait | Progress bar or percentage. Let user do other things. "This might take a moment." |
| 1min+ | Background task | "We'll notify you when this is done." Persistent status indicator. Email/notification on completion. |

---

## The Test

Before shipping any interactive element, check:

1. **Click every button on the page.** Does something visible happen for each one? If any button click produces no visible change, add feedback.
2. **Submit every form.** Do you see a clear success state? Do errors show inline? Does the form retain your input on error?
3. **Trigger every error state.** Turn off your network, enter invalid data, try edge cases. Does the user see a helpful message, or a blank page / cryptic error?
4. **Check the timing.** Is any operation taking more than 1 second without a progress indicator? More than 100ms without a click acknowledgment?
5. **The "did that work?" test.** For every action, can the user tell — without checking a database or refreshing the page — that it worked? If not, you're missing feedback.
6. **The double-click test.** What happens if the user clicks the button twice? Does it send two emails? Create two records? Charge them twice? Disable the button during processing.
