---
name: prevent-errors
description: "Apply when building any form, input, or interactive element where users can make mistakes. Prevention is better than error messages. Constrain inputs, validate inline, disable invalid paths, and guide users toward correct choices. Use whenever building forms, data entry, configuration, or any screen where the user provides input."
---

# Prevent Errors

The best error message is one the user never sees. Instead of letting users make mistakes and then telling them what they did wrong, design the interface so that mistakes are difficult or impossible to make.

This is Nielsen's heuristic #5, and it's more effective than any error message you could write.

## Constrain Inputs

Use the right input type so invalid values can't be entered in the first place.

| Instead of | Use | Why |
|---|---|---|
| Text field for dates | Date picker | Users can't type "Janaury 35th" |
| Text field for time | Time picker or dropdown | Users can't enter "25:99" |
| Text field for yes/no | Toggle switch | Only two valid states |
| Text field for one-of-many | Dropdown or radio buttons | Users can only pick valid options |
| Text field for quantity | Stepper (+/−) with min/max | Users can't enter −3 or 99999 |
| Text field for phone | `tel` input with formatting | Keyboard shows numbers, format is guided |
| Text field for color | Color picker or swatches | Users can't type "bleen" |
| Text field for URL | Input that auto-prepends https:// | Users don't have to remember the protocol |

The principle: if the set of valid answers is known and bounded, don't use a text field. Use a control that only allows valid answers.

## Disable Invalid Paths

If an action can't be taken right now, disable it — don't let the user click and then show an error.

- **Submit button**: disable until all required fields are valid. Re-enable the instant they are.
- **Date picker**: gray out dates that aren't available (past dates for a booking, already-booked slots).
- **Quantity stepper**: disable the "−" button at 1 (or your minimum). Disable "+" at your maximum.
- **Navigation**: if a step requires completing the previous step, show the future step as locked/grayed with a reason: "Complete shipping info first."

**Important**: when something is disabled, explain WHY. A grayed-out button with no explanation is as frustrating as an error. Use a tooltip or inline text: "Fill in all required fields to continue."

## Validate Inline, on Blur

Don't wait until the user hits "Submit" to tell them something is wrong. Validate each field when they leave it (on blur).

### Timing rules

- **On blur** (when they tab or click to the next field): validate format, required, min/max length.
- **Not on every keystroke**: typing "j" in an email field and immediately seeing "Invalid email" is hostile. Wait until they're done.
- **On submit**: final validation pass, scrolling to the first error if any.
- **Exception — "available" checks**: username/email availability can check on blur with a slight delay (debounce 500ms), showing a spinner then a checkmark or error.

### Display rules

- Put the error message directly below the field it's about, in red or a clear error style.
- Mark the field itself with a visual indicator (red border, error icon).
- Don't just say "Invalid" — say what's wrong and how to fix it: "Email needs an @ symbol" not "Invalid email."
- When the user fixes the error, remove the error message immediately (on change, not on blur).

## Guide Toward Correct Input

### Show expected format

If a field needs a specific format, show it before the user types, not after they fail:
- Placeholder text: "MM/DD/YYYY" (but note: placeholders disappear on focus, so also use helper text for critical formats)
- Helper text below the field: "Must be at least 8 characters"
- Input masks for structured data: phone `(___) ___-____`, credit card `____ ____ ____ ____`

### Show requirements upfront

For password fields:
- Show all requirements before they start typing
- Check off requirements as they're met (live feedback during typing is OK here because it's additive, not critical)
- Don't reveal new requirements after they fail. If you need a special character, say so upfront, not after they've typed a 16-character password without one.

### Offer suggestions

- Autocomplete for known-value fields (cities, countries, names)
- "Did you mean?" for likely typos (especially email domains: "Did you mean @gmail.com?")
- Suggestion chips for search: show popular/recent searches when the field is focused

## Confirm Before Destructive Actions

This overlaps with `user-control-and-freedom`, but from the error-prevention angle:

- Before delete: "Delete 'Project Alpha'? This removes all 12 files inside it."
- Before overwrite: "A file named 'report.pdf' already exists. Replace it?"
- Before bulk actions: "This will archive 47 conversations. Continue?"
- Use the item name and count in the confirmation. "Are you sure?" is never sufficient.
- Require typing the item name for high-stakes deletions (deleting an account, removing a whole project): "Type 'my-project' to confirm deletion."

## Protect Against Accidental Data Loss

- **Auto-save** drafts, form progress, and in-progress work. The user should never lose work because they accidentally closed a tab.
- **Warn before navigating away** from unsaved changes: "You have unsaved changes. Leave anyway?"
- **Never clear forms on validation error.** If the user's email is wrong, highlight the email field. Don't wipe the form and make them start over.
- **Debounce double-clicks** on submit buttons. Disable the button after the first click (with a loading state) so they can't accidentally submit twice.

## Anti-patterns

**Validation only on submit.** The user fills out 15 fields, hits Submit, and a banner appears: "3 errors found." They scroll around trying to find them. Validate inline, on blur.

**Clearing the form on error.** The cardinal sin. The user's entire input is sacred. Show what's wrong, let them fix just that one thing. Preserve everything else.

**Disabled buttons with no explanation.** A grayed-out "Continue" button. Why can't I continue? What's missing? Either add a tooltip/message explaining why, or keep it enabled and show the validation error on click.

**Revealing requirements after failure.** "Password must contain a special character." Why didn't you tell me that before I typed my password three times? Show all requirements upfront, always.

**Letting users select invalid options.** A date picker that lets you select yesterday for a future-only booking, then shows an error. Gray out invalid dates instead. Same for time slots, sizes, or anything with known constraints.

**Non-functional UI elements.** A search bar with no handler, dropdown items that don't navigate anywhere, buttons with no `onClick`, links to pages that don't exist. These are worse than having nothing — they actively confuse users who expect something to happen. Never render interactive elements that don't work yet. Remove them until implemented. A search bar that does nothing is worse than no search bar.
