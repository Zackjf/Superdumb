# Consistency Checklist

Practical audits and templates for keeping a UI consistent. Run these before shipping.

---

## 1. Vocabulary Registry

Define every user-facing concept once. Use this template to prevent the same thing from being called three different names.

| Concept | User-facing word | NOT these words | Where it appears |
|---------|-----------------|-----------------|------------------|
| The things users create | **Projects** | Workspaces, Items, Work, Folders | Nav, cards, empty states |
| People on the team | **Team members** | Users, People, Accounts, Seats | Settings, invite flow, sidebar |
| Removing permanently | **Delete** | Remove, Trash, Discard, Destroy | Modals, menus, buttons |
| Removing from a group | **Remove** | Delete, Unlink, Detach | List actions, modals |
| Hiding without deleting | **Archive** | Hide, Deactivate, Disable | List actions, filters |
| Saving changes | **Save** | Submit, Update, Apply, Commit | Form buttons (always "Save changes") |
| Creating new | **Create** | Add, New, Make, Insert | Buttons ("Add" OK for adding to groups) |
| The subscription | **Plan** | Tier, License, Package, Bundle | Pricing, settings, banners |
| Finding things | **Search** | Query, Filter, Find | Search bars, nav |
| Logging in | **Sign in** | Log in, Authenticate, Auth | Auth screens, nav |
| Logging out | **Sign out** | Log out, Disconnect, End session | User menu (must match "Sign in") |
| Help content | **Help center** | Docs, KB, FAQ, Support | Nav, footer, tooltips |

**How to audit:** Search your codebase for all user-facing strings. Grep button labels, headings, toasts, and error messages. Flag any concept with 2+ names.

---

## 2. Button Audit

Every button should use the format **verb + noun** (or just a verb for obvious contexts).

| Check | Pass | Fail |
|-------|------|------|
| Buttons use verb + noun | "Save changes," "Add member," "Export CSV" | "Submit," "OK," "Next," "Go" |
| Destructive buttons name the action | "Delete project," "Remove member" | "Yes," "Confirm," "OK" |
| Cancel is consistent | Always "Cancel" (not sometimes "Close," "Dismiss," "Back") | Mixed: "Cancel" here, "Close" there |
| One primary button per section | One filled button per screen section | Two filled buttons competing |
| Labels match the result | "Create account" actually creates an account | "Submit" (submit what?) |

**Quick test:** Read every button on every screen out loud. If you can't tell what will happen from the label alone, rewrite it.

---

## 3. Position Audit

Shared elements must appear in the same position across all screens.

| Element | Expected position | Check every screen |
|---------|-------------------|--------------------|
| Primary navigation | Left sidebar or top bar (pick one) | Does it ever move or disappear? |
| Page title | Top-left of content area | Ever missing or in a different spot? |
| Primary CTA | Top-right of content area or bottom of form | Does it jump between locations? |
| Back / breadcrumb | Top-left, above the page title | Missing on any drill-down pages? |
| Search | Top of page or top of sidebar | Disappears on some screens? |
| User avatar / menu | Top-right corner | Always there? |
| Toast / notifications | Top-right or bottom-center (pick one) | Mixed positions? |
| Save/submit button | Same position on every form | Bottom-right on some, bottom-left on others? |
| Cancel button | Same position relative to save on every form | Moves around? |

**How to audit:** Screenshot every screen. Lay them out in a grid. Draw lines where shared elements sit. Crooked lines = inconsistency.

---

## 4. Visual Audit

Same components must look the same everywhere.

| Component | What to check |
|-----------|---------------|
| Buttons | Same padding, border-radius, font-size across all screens? |
| Cards | Same shadow, border, corner radius? |
| Form inputs | Same height, border color, focus state? |
| Typography | Same heading sizes (H1, H2, H3) on all pages? |
| Icons | Same icon set? Same size? Same stroke width? No mixing sets? |
| Colors | Same blue for all primary actions? Same red for all errors? Same green for success? |
| Spacing | Same padding inside cards? Same gap between sections? |
| Avatars | Same size and shape (round vs. square) everywhere? |
| Tables | Same header style, row height, hover state? |

**How to audit:** Open two screens side by side. Compare the same component type. If you spot a difference, check which one matches the design system and fix the other.

---

## 5. Behavior Audit

Same interactions must produce the same results everywhere.

| Interaction | Expected behavior | Common inconsistency |
|-------------|-------------------|----------------------|
| Click outside a modal | Closes the modal | Some modals close, others don't |
| Press Escape | Closes modal / dropdown / overlay | Works on some overlays, not others |
| Click a table row | Opens detail view OR does nothing (pick one) | Opens detail on one table, selects on another |
| Form submit on Enter | Submits the form | Works on login, not on other forms |
| Unsaved changes + navigate | Shows "Unsaved changes" warning | Some forms warn, others silently discard |
| Auto-save vs. manual save | One approach everywhere | Some forms auto-save, others need a button |
| Loading pattern | Skeleton, spinner, or inline (pick one) | Mixed: skeleton on page A, spinner on page B |
| Success feedback | Toast, inline, or banner (pick one) | Toast on save, inline on delete, nothing on archive |
| Error display | Inline below field, not in a banner | Inline on some forms, banner on others |

**How to audit:** List every interaction pattern in your app. Test each one on every screen. Flag differences.

---

## 6. Navigation Audit

Nav labels must match the page headings they link to.

| Check | Pass | Fail |
|-------|------|------|
| Labels match headings | Nav says "Team," page H1 says "Team" | Nav says "Settings," page says "Account settings" |
| Same items in same order | Nav is identical on every page | Items reorder or disappear |
| Active state shown | Current page is highlighted in nav | No visual indicator of current location |
| Max items respected | 8-10 top-level nav items | 15+ items with no grouping |
| All links work | Every nav item leads to a built page | Links to placeholder or 404 pages |
| Consistent on all screens | Nav is present everywhere | Disappears on some pages (except focused flows like checkout) |

**Rule:** The word you click must be the word you see as the H1 on the page you land on. No exceptions.

---

## 7. Error Handling Audit

Every error must follow the same pattern.

| Error type | Required format | Common failures |
|------------|----------------|-----------------|
| Validation | Inline below the field: "[Field] + [what's wrong] + [how to fix]" | Generic "Invalid input" or errors at page top |
| Network | Toast or banner: "Couldn't save. Check your connection and try again." | Silent failure (user thinks it saved) |
| Server | "Something went wrong on our end. We've been notified." | Stack trace or raw error.message |
| Permission | "You don't have access. [Request access]" | Blank screen or redirect to login |
| Not found | "This [thing] was deleted or moved. [Go back]" | Generic 404 page |

**Additional checks:**
- [ ] No `alert()` or `confirm()` anywhere -- all use in-app components
- [ ] All error messages have the same tone (not formal on one page, casual on another)
- [ ] Errors appear near the problem (inline), not dumped at the top of the page
- [ ] All API errors show a human message, never raw error objects

---

## 8. Empty State Audit

Every list, table, feed, and collection must have a designed empty state.

| Screen / Component | Has empty state? | Has explanation? | Has CTA? |
|--------------------|:----------------:|:----------------:|:--------:|
| Projects list | [ ] | [ ] | [ ] |
| Notifications | [ ] | [ ] | [ ] |
| Search results (no match) | [ ] | [ ] | [ ] |
| Activity feed | [ ] | [ ] | [ ] |
| Team members | [ ] | [ ] | [ ] |
| Data tables | [ ] | [ ] | [ ] |
| File uploads area | [ ] | [ ] | [ ] |
| Comments section | [ ] | [ ] | [ ] |

**Rules:**
- "No results" (searched but nothing matched) must differ from "nothing created yet"
- Every empty state needs: (1) what this area is for, (2) why it's empty, (3) how to add the first item
- Never show a blank white space where data will eventually appear

**How to audit:** Create a brand-new test account. Every screen you see is an empty state. Screenshot all of them.

---

## 9. Destructive Action Audit

Every destructive action must be confirmed consistently.

| Check | Pass | Fail |
|-------|------|------|
| Confirmation shown | Every destructive action shows a confirmation | Some delete instantly, others confirm |
| Names the item | "Delete 'Q3 Report'?" | "Are you sure?" |
| States consequences | "This removes all 12 files and cannot be undone." | "This action is irreversible." (too vague) |
| Specific button label | [Cancel] and [Delete project] | [No] and [Yes] |
| Danger styling | Destructive button is red/danger, NOT primary blue | Delete button looks the same as "Save" |
| Safe option is default | Cancel is visually dominant, danger is secondary | Delete is the highlighted option |
| Consistent pattern | All use dialog, or all use undo toast (not mixed) | Some use dialog, some delete instantly |

**Severity scale:**

| Severity | Example | Required confirmation |
|----------|---------|----------------------|
| Low | Remove a tag, dismiss a notification | No modal (allow undo via toast) |
| Medium | Delete a file, remove a team member | Confirmation modal |
| High | Delete a project, cancel a subscription | Modal + consequence summary |
| Critical | Delete account, wipe all data | Type the name to confirm |

---

## Master Checklist (pre-release)

- [ ] **Vocabulary:** Every concept has one name (check the registry)
- [ ] **Buttons:** All use verb + noun format
- [ ] **Positions:** Shared elements are in the same spot on every screen
- [ ] **Visuals:** Same components use same styles everywhere
- [ ] **Behaviors:** Same interactions produce same results everywhere
- [ ] **Navigation:** Nav labels match page headings word-for-word
- [ ] **Errors:** Every error follows the same format and placement
- [ ] **Empty states:** Every list/table/feed has a designed empty state with a CTA
- [ ] **Destructive actions:** All confirmed with the right severity level
