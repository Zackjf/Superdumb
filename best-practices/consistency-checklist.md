# Consistency Checklist

Run this before shipping any multi-page build. Copy the checklist, check each item, flag violations.

---

## Vocabulary Registry Template

Create this at the start of every project. Check it before writing any user-facing text.

| Concept | User-facing word | NOT these | Notes |
|---|---|---|---|
| The things users create | Projects | Workspaces, Items, Work, Folders | |
| People on the team | Team members | Users, People, Accounts, Seats | "Members" OK in tight spaces |
| Removing permanently | Delete | Remove, Trash, Discard, Destroy | Always "Delete [thing]" |
| Removing from a group | Remove | Delete, Unlink, Detach | "Remove from team" |
| Hiding without deleting | Archive | Hide, Deactivate, Disable | |
| Saving changes | Save | Submit, Update, Apply, Commit | Button: "Save changes" |
| Creating new | Create | Add, New, Make, Insert | "Add" OK for adding to groups |
| The subscription | Plan | Tier, License, Package, Bundle | |
| Money the user pays | Payment | Invoice, Charge, Transaction | |
| Finding things | Search | Query, Filter, Find | |
| Logging in | Sign in | Authenticate, Log in, Auth | Pick one, use everywhere |
| Logging out | Sign out | Log out, Disconnect, End session | Match "Sign in" |

---

## Vocabulary Audit

- [ ] Pick one word for each concept. Search the codebase for alternatives. Replace all.
- [ ] Check that navigation labels match page headings exactly.
- [ ] Check that button labels use the same verb for the same action everywhere.
- [ ] Check that error messages use the same terms as the rest of the UI.
- [ ] Check that empty states use the same terms as the populated states.

---

## Button Audit

- [ ] Every button uses verb + noun ("Save changes", "Delete project", "Send message")
- [ ] No buttons say just "Submit", "OK", "Yes", "No", "Confirm", or "Click here"
- [ ] Primary buttons have the same style (filled, high contrast) on every page
- [ ] Secondary buttons have the same style (outlined or muted) on every page
- [ ] Destructive buttons have the same style (red or danger variant) on every page
- [ ] Save/submit buttons are in the same position on every form

---

## Position Audit

- [ ] Save/submit button: same position on every form (bottom-right, bottom-left, or top-right — pick one)
- [ ] Cancel button: same position relative to save on every form
- [ ] Search bar: same position on every page that has search
- [ ] Primary navigation: same position on every page (sidebar or top bar, not mixed)
- [ ] User menu / profile: same position on every page
- [ ] Destructive actions: same position relative to other actions on every page

---

## Visual Audit

- [ ] Same button component used for same function (not custom buttons on some pages)
- [ ] Same card style for similar content (same border radius, shadow, padding)
- [ ] Same table style for all data tables (same header, row height, hover)
- [ ] Same icon set everywhere (don't mix Material, Feather, Lucide, etc.)
- [ ] Same font sizes for same hierarchy level (h1 is the same size on every page)
- [ ] Same colors for same meanings (blue = interactive, red = error/destructive, green = success)
- [ ] Same spacing between elements (don't use 16px gaps on one form and 24px on another)

---

## Behavior Audit

- [ ] Same interaction = same result everywhere
  - If clicking a list item opens a detail panel on one page, it does the same on others
  - If swipe-to-delete works on one list, it works on every list
- [ ] If forms auto-save on one page, they auto-save on every page. If one requires clicking "Save", all do.
- [ ] Same loading pattern everywhere (skeleton, spinner, or inline — pick one)
- [ ] Same success feedback everywhere (toast, inline, or banner — pick one)
- [ ] Same error display everywhere (inline below field, banner at top, or toast — be consistent)

---

## Error Handling Audit

- [ ] All forms show validation errors inline below the field (not in a banner, not in a toast)
- [ ] All API errors show a human message (not raw error.message)
- [ ] All network errors show "Check your connection" with retry
- [ ] All destructive actions are confirmed the same way (all use dialog, or all use undo toast — not mixed)
- [ ] All error messages have the same tone (not formal on one page and casual on another)
- [ ] No alert() or confirm() anywhere — all use in-app components

---

## Empty State Audit

- [ ] Every list, table, grid, and feed has an empty state (not a blank area)
- [ ] Every empty state has: a brief explanation, why it's empty, and a CTA
- [ ] Empty states use consistent styling (same icon size, same text treatment)
- [ ] Empty states for "no results" differ from "nothing created yet"
- [ ] Empty states link to the primary input action when relevant

---

## Destructive Action Audit

Search for all delete/remove/archive handlers in the codebase:

- [ ] All destructive actions are confirmed before executing
- [ ] Confirmation dialogs name the specific item ("Delete 'Project Alpha'?" not "Are you sure?")
- [ ] Confirmation dialogs describe consequences ("This removes all 12 files inside it")
- [ ] The destructive button has a specific label ("Delete project" not "Yes" or "Confirm")
- [ ] The safe option is visually dominant (Cancel = primary style, Delete = red/danger)
- [ ] All destructive actions use the same confirmation pattern (all dialog, or all undo toast)

---

## Navigation Audit

- [ ] Same items in same order on every page
- [ ] Active page is visually highlighted in the navigation
- [ ] Navigation labels match page headings (if nav says "Analytics", page says "Analytics")
- [ ] No more than 8-10 top-level nav items
- [ ] Navigation doesn't disappear on any page (unless intentionally hidden in focused flows like checkout)
- [ ] No nav items link to pages that don't exist

---

## Reuse Audit

- [ ] Does a better component already exist in the codebase for any job being done manually?
  - MediaField exists → are all image inputs using it? (not raw URL text fields)
  - PendingButton exists → are all loading-state buttons using it?
  - ConfirmDialog exists → are all destructive actions using it?
  - UnsavedChangesBanner exists → is it wired into all editors?
- [ ] Are there duplicate implementations of the same pattern? (two different toast systems, two different modal components)
- [ ] Search for `alert(` and `confirm(` — replace all with in-app components
- [ ] Search for `dangerouslySetInnerHTML` — is every instance sanitized?
