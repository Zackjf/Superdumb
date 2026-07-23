# 20 Solved UI Patterns

These patterns cover ~90% of interfaces. Pick the one that matches your screen, follow the do/don't, and move on.

| # | Pattern | What it is | Do | Don't |
|---|---------|------------|----|-------|
| 1 | **List > Detail** | A scrollable list where each item opens a detail view. Used for products, orders, messages, contacts. Back button returns to the list with scroll position preserved. | Show 2-3 identifying fields per row (name, status, date). Let users scan without clicking. | Show every field in the list row. If users must click to know what an item is, the list failed. |
| 2 | **Form > Confirmation > Success** | Multi-step data entry ending in a review screen and a success state. Used for applications, submissions, orders. | Show a summary on the confirmation step with an "Edit" link per section. The success screen gives a next action. | Submit directly from the form with no review. Users need a chance to catch mistakes before committing. |
| 3 | **Dashboard** | 3-5 key metrics with quick actions. The home screen for logged-in users. Answers "how am I doing?" at a glance. | Limit to 3-5 metrics. Add 2-3 quick-action buttons for the most common tasks. Link metrics to detail pages. | Cram 15 charts on one screen. A dashboard that requires scrolling to find the important number is a report, not a dashboard. |
| 4 | **Settings** | Grouped sections of preferences. Saved on change or with a single save button per section. | Group into logical sections (Profile, Notifications, Security). Show current values inline. | One giant form with 40 fields and a single save button at the bottom. |
| 5 | **Onboarding** | Progressive disclosure that gets users to value fast. Skippable, resumable, and ideally 3-5 steps max. | Show progress (step 2 of 4). Let users skip and come back. End on a screen where they can DO something. | Force 12 mandatory steps before showing any product value. |
| 6 | **Empty State** | What users see when a list or section has no data yet. Must explain what goes here and how to add the first item. | Show an illustration or icon, a 1-sentence explanation, and a primary CTA ("Add your first project"). | Show a blank screen, a zero, or just the word "None." |
| 7 | **Search > Results > Detail** | Search input, results list, detail view. The three screens must feel like one flow. | Show result count. Highlight matched terms. Preserve the query when user goes back from detail. | Return zero results with no suggestions. Always offer "Did you mean...?" or related terms. |
| 8 | **Pricing Page** | 3 plans side by side, one highlighted as recommended. Feature comparison below. | Highlight one plan ("Most popular"). Use monthly/annual toggle. Keep feature rows scannable (checkmarks, not paragraphs). | Show 6 plans or hide pricing behind "Contact sales" for every tier. |
| 9 | **Login / Sign Up** | Single-purpose screens for authentication. Minimal distraction, clear error states. | Separate login and sign-up into distinct screens with a link between them. Support SSO/social login above the form. | Combine login and sign-up in one form with a toggle. Users get confused about which mode they're in. |
| 10 | **Profile / Account** | User's own information: name, email, avatar, password, connected accounts, danger zone (delete). | Group into sections. Put destructive actions (delete account) at the bottom with a confirmation step. | Mix billing settings, notification preferences, and profile info on one screen with no sections. |
| 11 | **Checkout** | Shipping > Payment > Confirm. Linear flow, no distractions, minimal navigation. | Show an order summary sidebar at every step. Auto-save progress. Show trust signals near payment fields. | Add navigation links, promotional banners, or related products during checkout. |
| 12 | **Notifications** | A list of events with read/unread state, timestamps, and actions. Accessible from a persistent bell icon. | Mark as read on view. Group by date. Let users mark all as read. Link each notification to the relevant screen. | Show notifications with no way to act on them or clear them. |
| 13 | **Data Table with Actions** | Rows of structured data with sort, filter, and per-row/bulk actions. Used for admin panels, CRMs, inventory. | Sticky header row. Sortable columns. Bulk select with checkbox column. Keep row actions to 2-3 (more in a "..." menu). | Render 50+ columns. Let users choose visible columns and default to the useful 5-8. |
| 14 | **Modal / Dialog** | An overlay that requires user attention. Used for confirmations, quick edits, and choices that block the flow. | Use for focused tasks (confirm delete, quick edit). Close on overlay click and Escape key. One primary action button. | Use modals for complex forms, long content, or stacking modal-on-modal. If it needs scrolling, it needs its own page. |
| 15 | **Card Grid** | A grid of cards with image, title, and metadata. Used for portfolios, product catalogs, team members. | Keep card content to image + title + 1-2 metadata items. Equal height cards. Responsive columns (4 > 3 > 2 > 1). | Mix card sizes in the same grid or put long paragraphs inside cards. |
| 16 | **Timeline / Activity Feed** | Chronological list of events. Used for audit logs, social feeds, project history. | Show relative timestamps ("2 hours ago"). Group by day. Use icons/avatars to differentiate event types. | Show raw ISO timestamps or mix chronological and reverse-chronological order. |
| 17 | **Sidebar Navigation** | Persistent left nav with icon + label. Collapsible on smaller screens. Used for apps with 5-15 top-level sections. | Group related items with section dividers. Highlight current page. Collapse to icons on tablet. | Nest more than 2 levels deep. If you need sub-sub-menus, rethink your information architecture. |
| 18 | **Tab Navigation** | Horizontal tabs for switching between views of the same entity. Content changes, context stays. | Use for 2-7 tabs on the same entity (e.g., a user's Profile / Orders / Settings). Keep tab labels to 1-2 words. | Use tabs for unrelated pages. If the tabs don't share context, use sidebar nav instead. |
| 19 | **Wizard / Stepper** | A multi-step flow with a progress indicator. Each step validates before proceeding. Used for setup, applications, configurations. | Show step names in the progress bar. Allow back navigation. Validate per step, not all at the end. | Allow skipping required steps or show a progress bar that resets on errors. |
| 20 | **Error / 404 Page** | A dead-end screen that helps users recover. Must acknowledge what happened and offer a way out. | Friendly headline, 1-sentence explanation, search bar or link to homepage, and back button. | Show a stack trace, a generic "Something went wrong," or a page with no navigation. |

## Quick reference: When to use what

| User intent | Pattern |
|-------------|---------|
| Browse a collection | List > Detail or Card Grid |
| Submit information | Form > Confirmation > Success or Wizard |
| Monitor status | Dashboard |
| Configure preferences | Settings |
| Find something specific | Search > Results > Detail |
| Complete a purchase | Checkout |
| Start using the product | Onboarding |
| Compare options | Pricing Page |
