---
name: use-familiar-patterns
description: "Apply this when building ANY page or flow that resembles a solved problem — login, signup, checkout, search, settings, pricing, error pages, profiles, contact forms. Users expect your site to work like sites they already know. Don't reinvent patterns that are already well-established. Novel UI costs users time and trust."
---

# Use Familiar Patterns

Users spend most of their time on other websites and apps. They've signed in a thousand times. They've checked out hundreds of times. They've searched, filtered, sorted, and browsed on every platform imaginable. Every one of those experiences trained them to expect things in certain places, working in certain ways.

When you follow those expectations, your UI feels intuitive — not because it's inherently obvious, but because the user already learned the pattern elsewhere. When you deviate, you force the user to stop, study, and figure out your novel approach. Most won't bother. They'll leave, or they'll make mistakes, or they'll lose trust.

This is Jakob's Law: users prefer your site to work like the sites they already use. It's not a suggestion — it's a description of how human learning works.

---

## The Standard Pattern Catalog

These tasks have been solved. The patterns are established. Use them.

### Login / Sign in

What users expect:
- Email/username field + password field, stacked vertically
- "Sign in" button below the fields
- "Forgot password?" link near the password field
- "Create account" / "Sign up" link below or nearby
- Social login options (Google, Apple, etc.) as an alternative, clearly separated from email login
- Errors inline: "That email isn't registered" or "Wrong password" — not a generic "Invalid credentials"

Don't:
- Put login in a sidebar, dropdown, or popover
- Combine login and signup in one form with a toggle (confusing — they look the same and users pick the wrong one)
- Require username when email works fine
- Make "Sign in" and "Sign up" look identical (different pages or clearly separated sections)

### Signup / Registration

What users expect:
- Minimal fields: name (or just email) + password
- Password requirements shown before they type, not after they fail
- Social signup as a fast alternative
- Confirmation of what happens next ("Check your email" or "You're in!")

Don't:
- Ask for 10 fields during registration. Get the minimum. Collect the rest later.
- Require a username when email works
- Make password requirements a guessing game (show them upfront, check in real-time)
- Use "Submit" as the button. Use "Create account" or "Sign up."

### Checkout / Payment

What users expect:
- Clear order summary visible throughout
- Linear flow: Shipping info, Payment info, Review, Confirm
- Familiar payment form: card number, expiry, CVV (or saved payment / Apple Pay / Google Pay)
- Total with tax and shipping visible before the final click
- "Place order" as the final button (not "Submit" or "Confirm")
- Order confirmation with order number and expected delivery

Don't:
- Require account creation before checkout (guest checkout is expected)
- Hide the total until the last step
- Invent a creative checkout flow (accordion, conversational, single-page-with-modals). Linear steps work. Use them.
- Remove the order summary during payment entry

### Search and Search Results

What users expect:
- Search bar at the top of the page, usually center or right
- Magnifying glass icon
- Results appear below the search bar or on a results page
- Each result has a title, snippet, and link
- Filtering/sorting options on the left or top of results
- "No results" message with suggestions

Don't:
- Hide search behind an icon that expands on click (on desktop — this is acceptable on mobile)
- Show results in a modal or overlay that blocks the page
- Return "0 results" with no helpful message or suggestion
- Require pressing Enter to search (show results as you type when feasible)

### Settings / Preferences

What users expect:
- Grouped into clear categories (Account, Notifications, Privacy, Billing)
- Toggle switches for on/off settings
- Dropdowns or radio buttons for multi-option settings
- Save confirmation when changes are made
- Accessible from a profile menu or main navigation

Don't:
- Spread settings across 8 separate pages when they'd fit on 1-2
- Use checkboxes where toggle switches are expected
- Auto-save without telling the user (or worse, require a page refresh)
- Label the page "Configuration" or "Preferences Panel"

### Profile / Account

What users expect:
- Photo, name, email displayed prominently
- "Edit" button or inline editing for each field
- Clear section for password/security changes
- Link to billing/subscription from here

Don't:
- Require navigating to a separate page to edit each field
- Show database fields the user can't edit or doesn't understand
- Mix security settings with profile settings without clear separation

### Contact / Support Forms

What users expect:
- Name, email, subject (or category), message
- "Send message" button
- Confirmation that it was sent and when to expect a response
- Alternative contact methods visible (phone, chat, email)

Don't:
- Ask for 15 fields. Name, email, message is often enough.
- Use "Submit" as the button label
- Leave the user wondering if the message was sent. Show clear confirmation.
- Require login to contact support

### Pricing Pages

What users expect:
- 2-4 plan options displayed as columns or cards
- Price prominently displayed with billing frequency (per month, per year)
- Feature list for each plan, with checkmarks for included features
- One plan highlighted as "Most popular" or "Recommended"
- Clear CTA button on each plan ("Start free trial," "Choose this plan")
- Comparison of annual vs. monthly pricing

Don't:
- Show more than 4 plans (too many choices causes decision paralysis)
- Hide the price behind "Contact sales" for standard plans
- Use feature lists with different lengths that make comparison hard
- Make the enterprise plan look like the only real option

### Error Pages (404, 500, etc.)

What users expect:
- Clear message: "Page not found" or "Something went wrong"
- A way back: link to home page, search bar, or suggested pages
- Friendly tone (not a stack trace, not "Error 404")

Don't:
- Show the raw HTTP error code as the primary heading
- Show a blank page or browser default error
- Dead-end the user with no navigation or links
- Show technical details ("the server returned a 502 Bad Gateway response")

---

## When a Standard Dropdown Is Better Than a Custom Radial Selector

This is the core principle stated bluntly: boring, standard UI components beat novel, creative ones almost every time.

| Standard component | Novel alternative | Why standard wins |
|---|---|---|
| Dropdown | Radial selector, spinning wheel | Every user knows how a dropdown works. Zero learning curve. |
| Normal form with fields | Conversational wizard ("What's your name? Great! Now what's your email?") | Forms are faster. Users can see all fields, skip around, and fix mistakes. Conversational UI forces a fixed order. |
| Checkbox list | Drag-and-drop ranking | Checkboxes are instant. Drag-and-drop requires figuring out the interaction model. |
| Standard scroll | Parallax scrolling, horizontal scroll, snap-scroll sections | Standard scroll is unconscious. Novel scroll requires conscious attention to navigate. |
| Date picker calendar | Natural language date input ("type a date like 'next Tuesday'") | Calendars are visual and precise. NLP date input is ambiguous and error-prone. |
| Hamburger menu (mobile) | Bottom navigation bar (mobile) | Actually, bottom nav IS the standard on mobile now. Use it for 3-5 primary destinations. Hamburger is fine for secondary items. |
| Tab bar | Swipe-to-navigate between sections | Tabs are visible and labeled. Swipe is invisible and discoverable only by accident. |

The user's mental budget for learning your interface is near zero. Every novel component spends from that budget. Spend it only where the payoff is enormous.

---

## When Novel UI IS Justified

Custom, non-standard UI earns its place in these situations:

### 1. It's your core differentiator
If the novel interaction IS the product — a drawing tool, a map interface, a video editor — then the custom UI is justified because the user came specifically for that experience. But the surrounding chrome (navigation, settings, account management) should still use standard patterns.

### 2. The standard pattern is genuinely broken for your use case
If you're building a color picker for professional designers and the standard color picker is insufficient, build a custom one. But verify that the standard is truly broken — not just "we think ours is cooler."

### 3. You've validated with real users
If user testing shows that your novel approach is faster, clearer, or preferred — and this isn't a test of 3 people who are your colleagues — then the data justifies the deviation. But test against the standard, not against nothing.

### The bar for novel UI

All three of these must be true:
1. The user will use this interaction frequently enough to justify learning it
2. The novel approach is measurably better (faster, fewer errors, higher completion)
3. The novelty doesn't require instructions or a tutorial to understand

If you need an onboarding tooltip to explain how your nav works, your nav is too novel.

---

## Reference: study-the-landscape

Before building any pattern that feels like it might be novel, reference the `study-the-landscape` skill. Look at how 2-3 established products handle the same task. If they all do it the same way, that's the pattern. Do it that way.

The landscape study doesn't just tell you what to build — it tells you what users will be confused by if you build something different.

---

## Anti-Patterns

### Novel navigation on desktop
Hamburger menus on desktop, side-scrolling navigation, hidden nav that appears on scroll, navigation that requires clicking a non-obvious element. On desktop, users expect a horizontal navigation bar at the top or a vertical sidebar. Use one of those.

### Custom scrolling behavior
Hijacking the scroll wheel to do something other than scroll (snap to sections, horizontal scroll, zoom, parallax that moves at a different speed). Users have deep muscle memory for what scroll does. Overriding it is disorienting and hostile. If users can't predict what will happen when they scroll, they'll feel out of control.

### Reinventing date pickers
Building a custom date input that requires typing a date in a specific format, or a creative calendar with non-standard navigation, or a slider for date ranges. The standard date picker calendar is well understood. Use it. Add presets ("Today," "This week," "Last 30 days") for common selections.

### Creative checkout flows
Checkout is where money changes hands. Users are at maximum anxiety. They need to feel safe, oriented, and in control. This is not the place for design innovation. Linear steps, clear totals, familiar payment form, visible security indicators. Every creative checkout flow loses conversions compared to a standard one.

### Reinventing form controls
Custom-styled checkboxes that don't look like checkboxes. Radio buttons that look like cards but don't behave like radio buttons (can you select multiple? who knows?). Sliders for precise numeric input. Toggle switches that don't clearly show on/off state. Use native or well-established component library controls.

### Gesture-only interactions
Swipe to delete, long-press to edit, pinch to zoom on non-image content, shake to undo. These are invisible. Users can only discover them by accident or by reading instructions. Always provide a visible alternative (a button, a menu option) for any action that has a gesture shortcut.

---

## The Test

For every page and component you build:

1. **Name the pattern.** "This is a login page." "This is a search results page." "This is a settings page." If you can name it, there's an established pattern for it. Follow it.
2. **Would a user from a competitor's product know how to use this immediately?** If someone who uses Shopify comes to your ecommerce admin, could they find their way around without a tour? If not, your patterns are too novel.
3. **Does any interaction require explanation?** Tooltips that say "drag to reorder" or "swipe to delete" are signs that the interaction isn't self-evident. Consider using a visible button instead.
4. **Is there a standard component that does this job?** Before building a custom component, check if a dropdown, checkbox, toggle, date picker, or text input already solves the problem.
5. **Is this novel because it's better, or novel because it's different?** Different is not better. Different is a cost. Only pay it when the benefit is clear.
