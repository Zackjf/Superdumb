---
name: copy-and-microcopy
description: "Use this whenever you write ANY text a user will see — empty states, loading messages, errors, success confirmations, helper text, tooltips, placeholders, confirmation dialogs. Every word matters. One bad error message can lose a user's trust. One good empty state can teach them the whole product."
---

# Copy & Microcopy

Every piece of text in your UI is a conversation between your product and a human being. Not a system broadcasting to a user. Not a robot issuing status reports. One person talking to another.

The text people see in your UI during the quiet moments — when there's no data, when something is loading, when something breaks, when something succeeds — shapes their entire experience more than your feature set does. A beautiful UI with robotic copy feels cold. A simple UI with thoughtful copy feels trustworthy.

---

## Empty States

An empty state is the first thing a new user sees. A blank screen says "this is broken." A helpful empty state says "you're in the right place, here's how to get started."

### Rules

- Never show a blank screen, an empty table, or a blank list with no explanation. The user will assume something is broken.
- Every empty state needs three things: a brief explanation of what belongs here, why it's empty, and what to do next.
- Include a CTA (call to action) that gets them started. A button, a link, something actionable.
- Keep the tone encouraging, not apologetic. They haven't failed — they just haven't started yet.

### Before / After

| Before (bad) | After (good) |
|---|---|
| *(blank white space)* | "No orders yet — once a customer places an order, it'll show up here." |
| "No results found" | "No results for 'blue widget' — try a broader search or check the spelling." |
| "0 items" | "Your cart is empty. Browse the shop to find something you'll love." |
| "No messages" | "No messages yet. When someone reaches out, you'll see it here." |
| *(empty table with column headers and nothing else)* | "You haven't created any projects yet. Start your first one — it only takes a minute." [Create project] |

### Why this matters

Empty states are your best onboarding tool. A new user sees them before they see anything else. Use that moment to teach them what this part of the product does and give them a clear path forward. Don't waste it with silence.

---

## Loading States

When something takes time, tell the user what's happening. A spinner with no words says "something is happening, maybe." A spinner with context says "I'm working on this specific thing for you."

### Rules

- Always tell them what's loading. "Finding your orders..." not just a spinning circle.
- Keep it short and specific to what they asked for.
- If it takes more than 2-3 seconds, add reassurance that it's still working. "This might take a moment — hang tight."
- Use skeleton screens (the gray shapes that mimic the layout of what's coming) instead of spinners when possible. They set expectations about what the screen will look like.
- Never show a loading state that could be mistaken for the final state. The user needs to know they're waiting.

### Before / After

| Before (bad) | After (good) |
|---|---|
| *(spinner with no text)* | "Finding your orders..." |
| "Loading..." | "Loading your dashboard — just a sec." |
| "Please wait" | "Pulling up this week's sales..." |
| *(blank screen for 3 seconds, then content appears)* | *(skeleton screen that fades into real content)* |
| "Processing..." (for 30 seconds with no update) | "Processing your payment... This usually takes about 10 seconds." |

### Why this matters

Silence during loading feels like something broke. Specific loading messages reassure the user that the system is doing what they asked. They also set expectations — "finding your orders" tells them orders are coming, so they know they're on the right track.

---

## Error Messages

When something goes wrong, the user needs to know two things: what happened and how to fix it. Most error messages only deliver bad news without a path forward. That's useless.

### Rules

- Say what went wrong in plain language. Not a code, not a technical description.
- Tell them how to fix it. If you can't suggest a fix, tell them who to contact.
- Place the error inline, right next to the thing that went wrong. Not in a banner at the top. Not in a toast that disappears.
- Don't blame the user. "That email doesn't look right" not "You entered an invalid email."
- Never expose error codes, stack traces, HTTP status codes, or internal identifiers to the user.
- If the error is on your end (server error, timeout), own it. "Something went wrong on our end. We're looking into it."

### Before / After

| Before (bad) | After (good) |
|---|---|
| "Error 422: Validation failed" | "That email doesn't look right — check for typos?" |
| "Invalid input" | "Phone numbers need at least 10 digits — try including the area code." |
| "Request failed" | "We couldn't save your changes. Check your connection and try again." |
| "500 Internal Server Error" | "Something went wrong on our end. Try again in a minute — if it keeps happening, contact support." |
| "Unauthorized" | "You'll need to sign in again to continue." |
| "TypeError: Cannot read property 'name' of undefined" | *(the user should never see this — catch it and show a human message)* |
| "An error has occurred. Reference: ERR-4829-XQ" | "We hit a snag saving your profile. Try again, or reach out to support if it keeps happening." |

### Why this matters

A cryptic error message makes the user feel helpless. A clear one makes them feel capable of fixing the problem. The difference between "Error 422" and "That email doesn't look right" is the difference between a user who gives up and one who corrects a typo and continues.

---

## Success Messages

When the user completes an action, confirm it. Then tell them what comes next. "Done" is not enough — they need to know the action landed and what to expect.

### Rules

- Confirm what happened, specifically. "Your order has been placed" not "Success."
- Tell them what happens next. "We'll email you a confirmation" or "Your changes are live now."
- If there's a next step, offer it. "View your order" or "Create another."
- Keep the tone warm but brief. Celebrate the win without being over-the-top.
- If the action has a delayed effect, say when. "Your new plan starts on August 1" or "Changes take effect within the hour."

### Before / After

| Before (bad) | After (good) |
|---|---|
| "Success" | "You're all set! We'll email you a confirmation shortly." |
| "Record created successfully" | "Your project has been created. Jump in and start adding tasks." |
| "Updated" | "Your profile has been updated. Changes are live now." |
| "Thank you" *(and nothing else)* | "Thanks for signing up! Check your inbox — we sent a verification link." |
| "Operation completed" | "Payment sent! It should arrive in 1-2 business days." |

### Why this matters

A success message is your chance to build confidence. The user just did something — they need to know it worked and that they're in a good place. A vague "Success" leaves them wondering. A specific message with next steps makes them feel taken care of.

---

## Helper Text

Helper text is the short hint that appears below or beside a form field. It answers the question the user is thinking right now: "What exactly do you want here?" or "Why are you asking me this?"

### Rules

- Keep it to one short sentence. If you need more, the field label or the form design needs work.
- Answer the user's most likely question about this field. Usually that's "why do you need this?" or "what format should I use?"
- Place it directly below the input, always visible. Not hidden behind a tooltip.
- If the information explains how you'll use their data, say so. This builds trust. "We'll only text you about your order" under a phone number field.
- Don't repeat the label. If the label says "Email" the helper text should not say "Enter your email address."

### Before / After

| Before (bad) | After (good) |
|---|---|
| *(no helper text on phone field)* | "We'll only text you about your order." |
| "Enter a valid URL" | "Link to your website or portfolio" |
| "Required field" | "We need this to send your receipt." |
| "Must be at least 8 characters" | "At least 8 characters — mix in a number or symbol to make it stronger." |
| *(no context on "Company" field)* | "Optional — only if you want an invoice in your company's name." |

### Why this matters

A tiny line of text below a field can prevent confusion, reduce errors, and build trust simultaneously. It's high-leverage copy — one sentence that answers a question before the user has to ask it.

---

## Placeholder Text

Placeholders are the gray text inside an input that disappears when you start typing. They have one job: showing format hints. They are terrible at everything else.

### Rules

- Never use placeholder text as a substitute for a label. It disappears on focus — the user can't see it while typing, which means they can forget what the field is for.
- Use placeholders only for format examples: "e.g., john@example.com" or "MM/DD/YYYY."
- Keep them short. They're hints, not instructions.
- Never put critical information in a placeholder. If the user needs to know it while typing, it needs to be visible helper text below the field.
- Prefix with "e.g.," to make it clear this is an example, not pre-filled data.

### Before / After

| Before (bad) | After (good) |
|---|---|
| Placeholder: "Email address" *(with no label)* | Label: "Email" / Placeholder: "e.g., john@example.com" |
| Placeholder: "Enter your full name as it appears on your government-issued ID" | Label: "Full name" / Helper text: "As it appears on your ID" |
| Placeholder: "We'll use this to send your receipt and order updates" | Label: "Email" / Helper text: "For your receipt and order updates" / Placeholder: "e.g., jane@example.com" |

### Why this matters

Placeholder-only fields are one of the most common UI mistakes. They look clean when the form is empty, but the moment a user starts filling it in, they lose context on every field they've already typed in. Labels are permanent. Placeholders are temporary. Don't put permanent information in a temporary place.

---

## Tooltips

Tooltips are the small popups that appear on hover (or tap on mobile). They should be your last resort, not your first instinct.

### Rules

- If the information is important enough to put in a tooltip, it's almost always important enough to show inline as helper text.
- Never put critical information (requirements, warnings, definitions of key terms) in tooltips. Most users won't hover to find them.
- Tooltips don't work well on touch devices. Users can't "hover" on a phone.
- If you must use a tooltip, keep it to one sentence. If you need more, use a help link or inline explanation.
- Use tooltips only for supplementary "nice to know" information — context that enhances understanding but isn't necessary to complete the task.

### Before / After

| Before (bad) | After (good) |
|---|---|
| Input label: "ARR" with tooltip: "Annual Recurring Revenue" | Label: "Annual recurring revenue (ARR)" |
| Tooltip on password field: "Must be 8+ characters with at least one number" | Helper text below field: "At least 8 characters with a number." |
| Tooltip on "Delete" button: "This action cannot be undone" | Confirmation dialog: "Delete this project? This can't be undone." |

### Why this matters

Tooltips are invisible by default. Anything invisible by default will be missed by most users. If the information matters, make it visible. Save tooltips for the rare case where extra context is helpful but not necessary.

---

## Confirmation Dialogs

When the user is about to do something significant — especially something destructive or irreversible — confirm it. But confirm it well.

### Rules

- Say what will happen, not just "Are you sure?" The user can't be "sure" if you don't tell them what they're agreeing to.
- Name the specific thing being affected. "Delete the project 'Website Redesign'?" not "Delete this item?"
- If the action is irreversible, say so clearly. "You can't undo this."
- If the action has consequences, name them. "All 12 tasks in this project will also be deleted."
- The confirm button should say what it does, not "OK" or "Yes." Use "Delete project" or "Cancel subscription."
- The cancel/dismiss button should be clearly lower-emphasis than the confirm button. Don't make the destructive action the visually dominant choice.
- For non-destructive confirmations, keep them brief. "Send this message to 1,200 subscribers?" [Send] [Go back]

### Before / After

| Before (bad) | After (good) |
|---|---|
| "Are you sure?" [OK] [Cancel] | "Delete 'Website Redesign'? All 12 tasks will also be deleted. You can't undo this." [Delete project] [Keep project] |
| "Confirm action?" [Yes] [No] | "Cancel your subscription? You'll have access until August 15." [Cancel subscription] [Keep subscription] |
| "Warning!" [Continue] [Back] | "Send this invoice to alex@company.com for $2,400?" [Send invoice] [Go back] |

### Why this matters

"Are you sure?" is a question that forces the user to remember what they were doing and figure out what will happen. That's your job, not theirs. A good confirmation dialog tells them exactly what they're about to do, what the consequences are, and gives them clearly labeled options.

---

## Tone Rules

All microcopy follows these principles:

**Conversational, not corporate.**
Write the way you'd explain something to a friend. Not the way a legal department would phrase it.
- No: "Your request has been submitted and is pending review by our team."
- Yes: "Got it! We'll take a look and get back to you soon."

**Helpful, not apologetic.**
Don't grovel. Solve the problem.
- No: "We're so sorry, but unfortunately we were unable to process your request at this time."
- Yes: "That didn't go through. Here's what to try."

**Confident, not hedging.**
If you know what happened, say it. Don't hide behind maybes.
- No: "It seems like there might have been an issue with your payment method."
- Yes: "Your card was declined. Try a different payment method."

**Brief, not verbose.**
Say it in as few words as possible without losing meaning. Every extra word dilutes the message.
- No: "Please be advised that the changes you have made to your account settings have been saved successfully and will take effect immediately."
- Yes: "Settings saved."

**Human, not robotic.**
Contractions are fine. Starting sentences with "And" or "But" is fine. Ending with a preposition is fine. Write the way people talk.
- No: "The item which you have selected has been added to your cart."
- Yes: "Added to cart."

---

## The Test

Before shipping any microcopy, run it through these checks:

1. **Read it out loud.** If it sounds weird coming out of your mouth, rewrite it.
2. **The friend test.** Would you say this to a friend? "Error 422: Validation failed" — no, you'd say "that email looks wrong."
3. **The blank screen test.** Is there any state where the user sees nothing — no data, no message, no guidance? Fill it.
4. **The "what now?" test.** After every message (error, success, empty state), does the user know what to do next? If not, add a next step.
5. **The disappearing test.** Is any critical information in a placeholder or tooltip that could be missed? Move it to permanent, visible text.
6. **The robot test.** Does any copy sound like it was written by a machine? "Operation completed successfully" — rewrite it as a human would say it.
