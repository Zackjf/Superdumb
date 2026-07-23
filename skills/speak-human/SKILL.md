---
name: speak-human
description: "Apply this to EVERY piece of user-facing text — labels, buttons, headings, errors, tooltips, empty states, notifications, everything. Replaces developer and system vocabulary with the words real people use. This is the single most important build skill and applies to every UI task without exception."
---

# Speak Human

Every word the user sees is a conversation with a real person. Not a developer. Not a product manager. A person who has never read your docs, doesn't know your data model, and will close the tab if something sounds like a robot wrote it.

This matters because language is the primary interface. Before users process your layout, colors, or animations, they read (or scan) your words. If those words sound like a database error or a government form, you've already lost them — even if the visual design is beautiful.

---

## The Vocabulary Substitution Table

Developer/system words have no place in user-facing text. Translate them.

| Developer word | Human word(s) |
|---|---|
| Submit | **Save**, **Send**, **Book**, **Place order**, **Sign up** (pick the one that describes what actually happens) |
| Query | **Search** |
| Authenticate / Auth | **Sign in**, **Log in** |
| Configuration | **Settings** |
| Initialize | **Set up**, **Get started** |
| Terminate | **Cancel**, **End**, **Stop** |
| Execute | **Run**, **Start** |
| Parameters | **Options**, **Settings** |
| Payload | **Data**, **Content**, **Message** |
| Invalid | **doesn't look right**, **isn't correct**, **needs fixing** |
| Repository | **Project** |
| Deploy | **Publish**, **Go live**, **Launch** |
| Instance | **Account**, **Site**, **App** (whatever it actually is) |
| Tenant | **Account**, **Organization**, **Team** |
| Token | **Code**, **Link**, **Key** (context-dependent) |
| Deprecated | **No longer available**, **Replaced by [X]** |
| Callback | **Response**, **Reply** (or hide it entirely) |
| Endpoint | Hide this. Users don't need to know. |
| Boolean | **Yes/No**, **On/Off** |
| Null / Nil | **None**, **Not set**, **Empty** |
| Webhook | **Notification**, **Alert** (or describe what it does: "Send me updates when...") |
| Cron / Scheduled task | **Recurring**, **Automatic**, **Runs every [time]** |
| Regex / Pattern | **Format**, **Rule** |
| Pagination | **Show more**, **Next page**, or just infinite scroll |
| CRUD | Never say this. Use the specific action: **Create**, **View**, **Edit**, **Delete** |
| Sync | **Update**, **Refresh**, **Connect** |
| Parse | **Read**, **Process** (or don't mention the mechanism) |
| Render | **Show**, **Display** (or don't mention the mechanism) |
| Propagate | **Apply**, **Update**, **Spread** |
| Truncate | **Shorten**, **Cut off** (or just do it without announcing it) |
| Instantiate | **Create**, **Set up** |
| Mutation | **Change**, **Update** |
| Schema | **Structure**, **Format**, **Template** |
| Migrate | **Move**, **Transfer**, **Upgrade** |
| Verbose | **Detailed** |
| Abort | **Cancel**, **Stop** |
| Flush | **Clear**, **Reset** |
| Invoke | **Run**, **Start**, **Use** |
| Persist | **Save** |
| Fetch | **Get**, **Load** (or just do it silently) |

When in doubt: if the word wouldn't appear in a text message between friends, it doesn't belong in the UI.

---

## Domain-Specific Jargon

Every industry has its own vocabulary that insiders use but customers don't. Before writing any UI copy, build a translation table for YOUR domain:

### Security / Auth products
| Jargon | Human equivalent |
|---|---|
| TOTP | Authenticator app, authenticator code |
| OTP | Verification code, login code |
| MFA / 2FA | Two-step verification, login verification |
| SSO / SAML | Single sign-on, sign in with your company account |
| SIEM | Security monitoring tools (Splunk, Datadog, etc.) |
| Provisioning | Setting up, configuring |
| Issuer | Service name, app name |
| TTL (Time To Live) | Time limit, expiration |
| Masking | Hiding, partial visibility |
| Base32 / Base64 | (don't show encoding names — just say "secret key") |
| Manifest | (don't show — just say "connect your workspace") |
| Tenant | Organization, workspace, team |

### Finance / Payments
| Jargon | Human equivalent |
|---|---|
| ACH | Bank transfer |
| APR | Annual interest rate |
| Escrow | Held securely until delivered |
| Ledger | Transaction history |
| Reconciliation | Matching payments |

### Healthcare
| Jargon | Human equivalent |
|---|---|
| PHI | Personal health information |
| Encounter | Visit, appointment |
| Intake | Check-in, registration |
| Referral | Doctor recommendation |

Build your own table at the start of the project. Check every word in every label against it.

---

## Button Labels: Verb + What Happens

Every button must tell the user what will happen when they click it. A button is a promise: "click me and this specific thing will occur."

### The formula

**[Verb] + [Object]** = good button label.

| Good | Bad | Why it's bad |
|---|---|---|
| Save changes | Submit | Submit what? To whom? |
| Send message | OK | OK what? |
| Place order | Confirm | Confirm what? |
| Delete account | Yes | Yes to what question? |
| Book this class | Proceed | Proceed to what? |
| Sign in | Authenticate | Robot word |
| Create project | Add | Add what? |
| Download report | Go | Go where? |
| Cancel subscription | Continue | Continue doing what? (This is the worst — "Continue" on a cancel flow is genuinely ambiguous) |
| Upload photo | Choose file | That's step 1, not the whole action |

### Special cases

- **Destructive buttons**: name the destruction. "Delete project" not "Delete." "Remove team member" not "Remove." The user needs to know exactly what they're destroying.
- **Cancel buttons**: "Cancel" as a button to dismiss a dialog is fine — it's universally understood. But a button that cancels a subscription should say "Cancel subscription," not just "Cancel" (which could mean "cancel this dialog").
- **Form save buttons**: "Save changes" for editing, "Create [thing]" for new things. Not just "Save" for both — the user should know if they're updating something or making something new.
- **Loading state**: change the button text to describe what's happening. "Saving..." not a spinner with no text. "Sending message..." not "Please wait."

---

## Headings: Describe the Task, Not the System

Headings tell users where they are and what they can do here. They should sound like something a person would say, not something a system architect would label.

| Good heading | Bad heading | Why it's bad |
|---|---|---|
| Your orders | Order Management Module | The user isn't managing a module |
| Team members | User Administration | "Administration" is a system word |
| Settings | Configuration Panel | "Configuration" and "Panel" are both system words |
| Add a product | Product Creation Interface | Everything after "Product" is a system word |
| Search results for "blue shoes" | Query Results | "Query" is a dev word; also, echo back what they searched |
| Recent activity | Activity Log | "Log" is a system word |
| Your plan | Subscription Tier Management | Three system words in a row |
| Sign in | Authentication | Nobody says "I need to authenticate" |
| Choose a date | Date Selection | Unnecessarily formal |
| What's new | Changelog | Dev word |

### Rules for headings

- **Use "your" when showing the user their own stuff.** "Your orders," "Your projects," "Your team." Not "Orders," "Projects," "Team." The possessive makes it personal.
- **Use a verb when the page is an action.** "Add a team member," "Choose a plan," "Set up your store." Not "Team Member Addition," "Plan Selection."
- **Don't include the word "page" or "screen."** "Settings," not "Settings Page." The user knows it's a page.
- **Match what the user clicked to get here.** If the navigation link says "Orders," the page heading should say "Your orders" — not "Purchase History" or "Transaction Records."

---

## The Friend Test

For every piece of user-facing text, apply this test:

> "Would the user say this word when describing this task to a friend?"

- "I need to **submit** my form." -- No. "I need to **send** my application."
- "I need to **authenticate**." -- No. "I need to **sign in**."
- "Let me check the **configuration**." -- No. "Let me check my **settings**."
- "I need to **query** the database." -- No. "I need to **search** for something."
- "The **payload** was **invalid**." -- No. "The **info I sent** **wasn't right**."

If you can't imagine a person saying it out loud in a casual conversation, rewrite it.

This test also catches overly formal language that isn't technically jargon but still feels robotic:
- "Your request has been successfully processed" -- "Done! Your order is on its way."
- "An error has occurred" -- "Something went wrong"
- "Please be advised that" -- (just say the thing)
- "In order to" -- "To"
- "At this time" -- "Right now" or "Currently"
- "Please note that" -- (just say the thing)

---

## Reading Level

Aim for a grade 6-8 reading level. This isn't about dumbing things down — it's about clarity. Clear writing serves PhDs and first-time users equally. Complex writing only serves people willing to work hard at reading, which is nobody using a UI.

### How to stay at grade 6-8

- **Short sentences.** 15-20 words max. If a sentence has a comma, consider splitting it.
- **Common words.** "Use" not "utilize." "Help" not "facilitate." "Start" not "commence." "Show" not "indicate."
- **Active voice.** "We sent your receipt" not "Your receipt has been sent."
- **One idea per sentence.** If you're using "and" to connect two different ideas, make them two sentences.

---

## Anti-Patterns

### Passive voice
- Bad: "Your password has been updated."
- Good: "We updated your password." / "Password updated."

Passive voice hides who did what. It sounds bureaucratic. Active voice is clearer and shorter.

### Double negatives
- Bad: "Don't forget to not leave this unchecked."
- Good: "Check this box to receive updates."

Any sentence where the user has to work out the logic of multiple negations will be misread.

### Conditional language that creates confusion
- Bad: "If you would like to optionally configure advanced notification preferences, you may do so below."
- Good: "Set up notifications" (with a link or section below)

Conditional phrasing ("if you would like to," "you may want to," "should you choose to") adds words without adding meaning. Just tell them what's there and let them decide.

### Internal terminology leaking
This is the most common offense. It happens when different developers write different pages without a shared vocabulary, or when someone copies text from a product spec or API doc directly into the UI.

Signs of leakage:
- The same thing is called different names on different pages ("workspace" here, "project" there)
- Words appear that match your code variable names (`user_status`, `plan_type`)
- Error messages reference internal systems ("the payment gateway returned an error")
- Help text assumes knowledge of your architecture ("this webhook fires when the entity state changes")

### Jargon as a shortcut
Sometimes developers use jargon because it's shorter than the plain explanation. "Configure your webhook" is shorter than "Set up automatic notifications." But the extra words are worth it because 100% of users understand the second version and approximately 5% understand the first.

---

## The Test

Before shipping any screen, read every word on it out loud. Every label, every button, every heading, every error message, every tooltip.

1. **Did you stumble on any word?** Rewrite it.
2. **Did any word sound like it belongs in documentation, not conversation?** Replace it.
3. **Could a 12-year-old understand every sentence?** If not, simplify.
4. **Is any button just one generic word (Submit, OK, Continue, Go)?** Make it a verb + object.
5. **Does any heading describe the system instead of the task?** Reframe it around the user.
6. **Is there any passive voice?** Make it active.
7. **Would the user say any of these words when describing this task to a friend?** If not, those words don't belong.
