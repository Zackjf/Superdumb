---
name: consistency
description: "Apply this to EVERY screen, component, and piece of text you build. Same word means same thing everywhere. Same pattern appears in same position everywhere. Same component has same style everywhere. Consistency eliminates cognitive overhead and builds trust — inconsistency creates confusion and feels broken."
---

# Consistency

Consistency is how users build a mental model of your product. Every time "Save" appears in the top-right corner, the user learns "top-right corner = save." Every time "Projects" means the same thing, the user learns what "Projects" means in your world. This learning is unconscious and effortless — until something breaks the pattern. Then the user has to stop and think.

The cost of inconsistency is invisible but cumulative. One button in a different position doesn't kill the user. But across 20 screens, if every page solves the same problem differently, the user never builds a mental model. They approach every page as if it's a new product. That's exhausting. They won't know why your product feels "hard to use," but this is why.

---

## Vocabulary Consistency

If you call something "Projects" on one page, it is "Projects" everywhere. Not "Workspaces" on the dashboard, "Projects" in the sidebar, "My work" on the profile, and "Items" in the search results. These four words refer to the same thing, but the user doesn't know that — they'll think these are four different features.

### The problem

Vocabulary drift happens invisibly:
- **Different developers write different pages.** Dev A calls it "members." Dev B calls it "users." Dev C calls it "people." All three are pointing at the same database table.
- **Copy-paste from different sources.** A heading was taken from the product spec (which says "workspace"), a button label was taken from the design file (which says "project"), and error text was written by the developer on the fly (who called it "folder").
- **Feature renaming that doesn't propagate.** Marketing decided "Campaigns" sounds better than "Blasts," but three pages still say "Blasts" because nobody updated them.
- **Different conventions for the same action.** One page says "Remove," another says "Delete," another says "Trash," another says "Discard." The user wonders: do these do different things?

### Rules

- **Pick one word for each concept and use it everywhere.** If it's "Projects," it's never "Workspaces," "Items," "My work," or "Folders" in any user-facing text.
- **Pick one word for each action and use it everywhere.** If removing an item is "Delete," it's always "Delete" — not "Remove" on some pages, "Trash" on others, and "Discard" on another.
- **Action words must match their consequences.** "Delete" implies permanent removal. "Archive" implies it's kept but hidden. "Remove" implies it's taken out of a group but still exists. Choose the word that honestly describes what happens, then use that same word everywhere that action occurs.
- **Headings, navigation labels, and page titles must match.** If the nav link says "Team," the page heading must say "Team" (or "Your team"), not "Members" or "People."

---

## The Vocabulary Registry

Maintain a living list of user-facing terms and their definitions. Every time you add a new screen or feature, check this list. If the concept already has a word, use that word. If it's new, add it to the list and define it.

### Example registry

| Concept | User-facing word | NOT these | Notes |
|---|---|---|---|
| The things users create and manage | Projects | Workspaces, Items, Work, Folders | Plural: "Projects." Singular: "project." |
| People on a team | Team members | Users, People, Members, Accounts, Seats | "Members" alone is OK in tight spaces (table headers) |
| Removing something permanently | Delete | Remove, Trash, Discard, Destroy, Erase | Always followed by what's being deleted: "Delete project" |
| Removing from a group but not deleting | Remove | Delete, Unlink, Detach, Dissociate | "Remove from team" not "Delete from team" |
| Hiding without deleting | Archive | Hide, Deactivate, Disable, Soft-delete | "Archive project" — available in "Archived" filter |
| The act of saving changes | Save | Submit, Update, Apply, Commit, Persist | Button: "Save changes" (not just "Save" on edit forms) |
| Creating something new | Create | Add, New, Make, Insert, Generate | Button: "Create project" — "Add" is OK for adding to a group: "Add team member" |
| The user's subscription | Plan | Subscription, Tier, License, Package, Bundle | "Your plan" in headings, "plan" in body text |
| Money the user pays | Bill / Payment | Invoice, Charge, Transaction, Fee | "Billing" for the section, "payment" for the act |

### How to use the registry

1. **Before writing any user-facing text**, check the registry. Is the concept already defined? Use the established word.
2. **When introducing a new concept**, add it to the registry. Define what word to use, what words to avoid, and any usage notes.
3. **When reviewing a PR that adds UI text**, check every user-facing string against the registry. Flag deviations.
4. **When renaming a concept**, update it in the registry AND propagate the rename to every existing screen. Partial renames are worse than no rename.

---

## Pattern Consistency

When a UI pattern exists on one page, the same pattern appears in the same way on every page where it's needed.

### Positions

- **Save/submit button**: pick a position (top-right, bottom-right, bottom-center) and use it on every form. If "Save changes" is bottom-right on the profile page, it's bottom-right on the settings page, the edit product page, and every other form.
- **Cancel/back button**: same position relative to the save button on every form. If cancel is to the left of save, it's always to the left of save.
- **Primary navigation**: same position on every page. If it's a top bar, it's a top bar everywhere. If it's a sidebar, it's a sidebar everywhere. Don't mix.
- **Search**: same position on every page that has search. Top-center, top-right, wherever — but the same.
- **User menu / profile**: same position on every page. Usually top-right.
- **Notifications**: same position and same behavior (bell icon, badge count, dropdown) on every page.
- **Destructive actions**: same visual treatment everywhere. If "Delete" is a red text button on one page, it's a red text button on every page.

### Behaviors

- **How modals work**: same enter/exit animation, same overlay darkness, same close behavior (X button, click outside, Escape key) everywhere.
- **How forms save**: if one form auto-saves, all forms auto-save. If one form requires clicking "Save," all forms require clicking "Save." Mixing auto-save and manual save creates uncertainty.
- **How lists are sorted**: if one list defaults to "Newest first," similar lists should also default to "Newest first."
- **How errors appear**: same error styling (red border, red text, icon) on every form. Don't use red outlines on one form and yellow banners on another.
- **How success is confirmed**: if one action shows an inline confirmation, similar actions show inline confirmations. If one shows a toast, similar actions show toasts. Don't mix.

---

## Visual Consistency

Same component for same function, same style, every time.

### Component consistency

- **Buttons**: one style for primary actions (filled, high contrast), one style for secondary actions (outlined or muted), one style for destructive actions (red or red-outlined). Don't mix 4 different button styles across pages.
- **Cards**: if you show items as cards on one page, similar items are cards on other pages. Same border radius, same shadow, same padding. Don't use rounded cards on one page and sharp-cornered cards on another.
- **Tables**: same header style, same row height, same hover behavior, same action column position across all tables. A user who learns one table should feel at home in every table.
- **Icons**: same icon set everywhere. Don't use a Material icon for "settings" on one page and a Feather icon for "settings" on another. Pick one icon library and use it consistently.
- **Typography**: same heading sizes, same body text size, same font weights across all pages. Don't use 24px headings on one page and 20px on another.
- **Spacing**: consistent padding and margins between elements. Don't use 16px gaps on one form and 24px on another without a reason.
- **Colors**: same color for same meaning everywhere. If blue means "interactive/link," blue always means that. If red means "error/destructive," red always means that. If green means "success," green always means that. Don't use red for a non-destructive primary button on one page.

### Layout consistency

- **Similar pages should look similar.** A list page for "Projects" should have the same layout as a list page for "Team members" — same header position, same table or card layout, same filter position, same action button position.
- **Detail pages should follow the same structure.** If a project detail page has a header, tabbed sections, and a sidebar, a team member detail page should use the same structural pattern.
- **Forms should follow the same layout.** Single column, label position, field spacing, button placement — consistent across all forms.

---

## Navigation Consistency

The navigation is the user's anchor. It tells them where they are, where they can go, and what the product contains. If it changes, the anchor is gone.

### Rules

- **Same items in same order on every page.** If the sidebar shows Home, Projects, Team, Settings — that's the order everywhere. Don't rearrange based on page context.
- **Active state is visually clear.** The current page/section is highlighted in the navigation. The user should always be able to glance at the nav and know where they are.
- **Navigation doesn't disappear.** If there's a sidebar on the main pages, there's a sidebar on all pages. Don't hide it on some pages and show it on others (unless it's a focused flow like checkout where hiding nav is intentional and temporary).
- **Sub-navigation follows the parent.** If "Settings" has sub-sections, those sub-sections appear in the same order and position every time the user enters Settings.
- **Navigation labels match page headings.** If the nav says "Analytics," the page heading says "Analytics" — not "Reports" or "Insights" or "Data."

---

## How Vocabulary Drift Happens (And How to Prevent It)

Vocabulary drift is the most common consistency violation. Understanding how it happens helps prevent it.

### Common causes

1. **No shared vocabulary list.** Developers independently choose words for the same concepts. Without a registry, each choice is reasonable in isolation but contradictory in aggregate.

2. **Design files and code diverge.** The design file says "Workspace." The developer implements it as "Project" because that's what the API returns. Nobody catches it because design review and code review happen separately.

3. **Specs use different words than the product.** The product spec says "Campaign." The API says "Blast." The design says "Message." The UI ends up with a mix of all three depending on which source the developer referenced.

4. **Feature renaming that doesn't propagate.** Someone renames "Reports" to "Analytics" in the nav, but the page heading still says "Reports," the empty state says "No reports yet," and the help docs reference "the Reports page."

5. **Multiple developers, no coordination.** Dev A builds the list page and calls the action "Remove." Dev B builds the detail page and calls the same action "Delete." Both are reasonable. Neither checked what the other did.

6. **Copy-paste from external sources.** Button text copied from a UI library example ("Submit"), error text copied from a validation library ("Invalid input"), heading copied from a competitor ("Dashboard").

### Prevention

- **Create the vocabulary registry at the start of the project.** Define terms before building UI.
- **Check the registry before writing any user-facing string.** Make it a habit, like checking types before writing code.
- **Include user-facing text in code review.** Reviewers should check every string against the registry, not just the logic.
- **Search the codebase when adding a new term.** Before introducing "Members," search for "Users," "People," "Team" to see if the concept already has a word.
- **When renaming, use find-and-replace across the entire project.** Partial renames are worse than no rename.

---

## Anti-Patterns

### Mixed terminology
"Projects" in the sidebar, "Workspaces" on the dashboard, "Your work" on the profile. The user wonders: are these three different things, or three words for the same thing? They can't tell. They'll click each one to find out. That's three unnecessary navigations caused by inconsistent vocabulary.

### Inconsistent button placement
"Save" is bottom-right on the profile form, bottom-left on the settings form, and top-right on the product edit form. The user has to hunt for the save button on every page. Their muscle memory never kicks in because the target keeps moving.

### Different layouts for similar pages
The Projects list uses cards. The Team Members list uses a table. The Billing list uses a flat list with separators. Each layout is fine in isolation, but using different layouts for structurally similar content (a list of items with names, statuses, and actions) forces the user to re-learn how to parse information on every page.

### Inconsistent action words
"Delete" on one page, "Remove" on another, "Trash" on a third. The user wonders if "Remove" does something different from "Delete." Maybe "Remove" keeps a copy somewhere? Maybe "Trash" is recoverable? If these all do the same thing, they should all use the same word.

### Mixed confirmation patterns
Deleting a project shows a modal confirmation. Deleting a team member just does it immediately with an undo toast. Deleting a document shows an inline confirmation. The user can't predict what will happen when they click "Delete" because the confirmation pattern changes every time.

### Navigation labels that don't match page content
The nav says "Analytics." The page heading says "Reports." The breadcrumb says "Insights." The URL says `/dashboard`. Four different words for the same place. Pick one.

---

## The Test

Before shipping any new screen or component:

1. **Check every user-facing word against the vocabulary registry.** Is the concept already named? Use the established name.
2. **Check the position of every action.** Does the save button match where it is on other forms? Does the destructive action match where it is on other pages?
3. **Check the visual treatment of every component.** Does this button, card, table, or icon match its counterparts on other pages?
4. **Check navigation labels against page headings.** Do they match?
5. **Search the codebase for the terms you used.** Did another developer use different terms for the same concepts? If so, align on one.
6. **Compare this page to the most similar existing page.** If they handle similar content, do they look and behave similarly?
7. **Ask: would a user who learned one page feel at home on this page?** If they'd have to re-learn positions, words, or patterns, something is inconsistent.
