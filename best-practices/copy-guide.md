# Copy Guide

A practical guide for writing every piece of text a user sees. Every word in your UI is a conversation between your product and a person. Write like a helpful friend, not a robot, not a marketing brochure, not a legal department.

---

## Tone

**Conversational and warm.** Write the way you'd explain something to a friend sitting next to you. Not how a corporation issues a press release. Not how a chatbot tries to be quirky.

- Friendly, not formal
- Warm, not cold
- Direct, not hedging
- Confident, not uncertain
- Helpful, not apologetic
- Brief, not verbose

**The test:** Read it out loud. If you'd feel weird saying it to someone's face, rewrite it.

---

## Reading Level

Aim for grade 6-8. That means:

- Short sentences. One idea per sentence.
- Common words. The word everyone knows, not the fancy synonym.
- No jargon. If a word wouldn't make sense to your parents, swap it.
- No acronyms without explanation (and usually just skip the acronym).
- No compound-complex sentences. If a sentence has a semicolon, it's probably two sentences.

**The test:** Could a 13-year-old understand this on the first read? If not, simplify.

---

## Voice

**Active voice always.** The user should know who's doing what.

| Passive (don't) | Active (do) |
|---|---|
| Your changes have been saved. | We saved your changes. |
| Email should be entered in the field below. | Enter your email. |
| An error was encountered. | Something went wrong. |
| The payment was processed successfully. | Your payment went through. |
| Your request has been submitted. | We got your request. |
| The file has been uploaded. | Your file is uploaded. |
| The account was created. | You're all set! Your account is ready. |
| This action cannot be undone. | You can't undo this. |
| Access has been denied. | You don't have access to this. |
| The form must be completed before proceeding. | Fill out the form to continue. |

---

## Contractions

Use them. They sound human. Writing without contractions sounds stiff and robotic.

| Without (stiff) | With (natural) |
|---|---|
| You are signed in. | You're signed in. |
| We will send you an email. | We'll send you an email. |
| You do not have permission. | You don't have permission. |
| It cannot be undone. | It can't be undone. |
| We have saved your changes. | We've saved your changes. |
| That is not a valid email. | That's not a valid email. |
| They are on your team. | They're on your team. |

---

## Numbers

Use numerals, not words. Numerals are easier to scan.

| Words (don't) | Numerals (do) |
|---|---|
| three items | 3 items |
| forty-nine dollars and ninety-nine cents | $49.99 |
| twelve orders | 12 orders |
| two hundred members | 200 members |
| one new message | 1 new message |
| zero results | 0 results (or better: "No results") |

Include units. "50GB" not "50." "3 days" not "3." Numbers without units force the user to hunt for context.

---

## Word Substitution Table

Map developer and corporate words to human words. When you encounter the left column in UI text, replace it with the right column.

| Developer / Corporate Word | Human Word |
|---|---|
| Submit | Save, Send, Book, Place order |
| Authenticate | Sign in |
| Authorization | Permission |
| Credentials | Sign-in info |
| Configuration | Settings |
| Preferences | Settings |
| Terminate | Cancel, End, Stop |
| Initialize | Set up, Start |
| Instantiate | Create |
| Invalid | "doesn't look right," "not quite right" |
| Deprecated | No longer available |
| Payload | Data |
| Query | Search |
| Repository | Project |
| Deploy | Publish, Launch, Go live |
| Execute | Run |
| Modify | Change, Edit, Update |
| Navigate | Go to |
| Utilize | Use |
| Commence | Start, Begin |
| Facilitate | Help |
| Implement | Add, Build, Set up |
| Parameters | Options, Settings |
| Propagate | Spread, Update, Sync |
| Enumeration | List, Options |
| Boolean | Yes/No, On/Off |
| Timestamp | Date, Time |
| Null / Nil | Empty, None, Nothing |
| Parse | Read, Understand |
| Render | Show, Display |
| Truncate | Shorten, Cut off |
| Toggle | Turn on/off, Switch |
| Fetch | Get, Load, Pull up |
| Cache | Saved copy |
| Sync / Synchronize | Update, Refresh, Keep up to date |
| Bandwidth | Space, Room, Capacity |
| Migrate | Move, Transfer, Switch |
| Iterate | Improve, Update, Refine |
| Verbose | Detailed |
| Granular | Detailed, Specific |
| Leverage | Use |
| Optimize | Improve, Speed up |
| Functionality | Feature, What it does |
| Scalable | Grows with you |
| Robust | Strong, Reliable |
| Seamless | Smooth, Easy |
| Pursuant to | Following, Based on |
| In order to | To |
| Prior to | Before |
| Subsequent to | After |
| Endeavor | Try |
| Methodology | Method, Approach |
| Workflow | Process, Steps |
| Actionable | Useful, Clear |
| Stakeholder | Team member, Person, Your team |
| Onboard | Get started, Set up |
| Offboard | Remove, Deactivate |
| Provision | Set up, Create, Add |
| Revoke | Remove, Take away |
| Endpoint | Address, Link, URL |
| Whitelist / Allowlist | Approved list |
| Blacklist / Blocklist | Blocked list |
| Regex / Pattern | Format, Rule |

---

## Button Labels

Every button uses the formula: **verb + what happens next.**

The user should be able to read the button and know exactly what clicking it will do.

### Good button labels

- Save changes
- Send message
- Book this class
- Place order
- Delete project
- Create account
- Add team member
- Download report
- Start free trial
- Cancel subscription
- Upload photo
- Copy link
- Share with team
- Sign in
- Sign out
- Apply filter
- Clear search
- Resend email
- Schedule post
- Publish page

### Bad button labels (never use these)

| Bad | Why it's bad | Better |
|---|---|---|
| Submit | Submit what? Where? | Save changes, Send message, Place order |
| OK | OK what? What just happened? | Got it, Close, Continue |
| Click here | Meaningless out of context | The specific action: "Download the report" |
| Yes | Yes to what? | The specific action: "Delete project" |
| No | No to what? | Keep project, Go back, Cancel |
| Confirm | Confirm what? | Place order, Send invite, Delete account |
| Continue | Where? | Go to payment, Review your order |
| Cancel | Ambiguous on confirmation dialogs | Keep project (to dismiss), Cancel subscription (to act) |
| Done | Done with what? | Save changes, Finish setup |
| Process | Process what? | Place order, Run report |
| Execute | Nobody talks this way | Run, Start, Send |
| Apply | Vague | Save settings, Apply filter |

### Confirmation dialog buttons

On confirmation dialogs, both buttons should say what they do. Never "Yes / No" or "OK / Cancel."

| Bad | Good |
|---|---|
| [Yes] [No] | [Delete project] [Keep project] |
| [OK] [Cancel] | [Send invoice] [Go back] |
| [Confirm] [Cancel] | [Cancel subscription] [Keep subscription] |
| [Continue] [Back] | [Place order] [Review cart] |

---

## Headings

Headings are task-oriented. They describe what the user can do here, not a category label from a database.

| Label heading (don't) | Task heading (do) |
|---|---|
| Order Management | Your orders |
| Team Member Creation | Add a team member |
| Account Configuration | Your settings |
| Project Administration | Your projects |
| Payment Processing | Payment |
| User Profile | Your profile |
| Notification Preferences | Notifications |
| Subscription Management | Your plan |
| Content Management | Your pages |
| Data Export | Download your data |
| Password Management | Change your password |
| Report Generation | Create a report |
| Access Control | Who can access this |

---

## Questions Over Statements in Forms

Frame form labels as questions when possible. Questions feel like a conversation. Statements feel like a government form.

| Statement (cold) | Question (warm) |
|---|---|
| Email address | What's your email? |
| Full name | What's your name? |
| Company name | What company are you with? |
| Phone number | What's your phone number? |
| Shipping address | Where should we ship this? |
| Date of birth | When's your birthday? |
| Password | Choose a password |
| Preferred language | What language do you prefer? |

Use this selectively. For short, fast forms (login, search), standard labels ("Email," "Password") are fine because speed matters more than warmth. For longer forms where the user needs encouragement (onboarding, applications, profiles), questions keep the tone inviting.

---

## Example Rewrites

### Headings

| Before | After |
|---|---|
| Inventory Management Dashboard | Your inventory |
| User Authentication Required | Sign in to continue |
| Subscription Plan Selection | Pick your plan |
| Error: Resource Not Found | We couldn't find that page |
| Transaction History | Your payments |

### Buttons

| Before | After |
|---|---|
| Submit Form | Save changes |
| Execute Query | Run search |
| Initiate Transfer | Send money |
| Terminate Session | Sign out |
| Confirm Deletion | Delete project |

### Error messages

| Before | After |
|---|---|
| Error 422: Validation failed for field 'email' | That email doesn't look right. Check for typos? |
| Authentication failed. Invalid credentials provided. | Wrong email or password. Try again or reset your password. |
| Request timeout. The server did not respond within the allotted time. | That took too long. Check your connection and try again. |
| Duplicate entry. A record with this identifier already exists. | That name is already taken. Try a different one. |
| Insufficient permissions to perform this action. | You don't have access to do this. Ask your admin for permission. |

### Descriptions and body text

| Before | After |
|---|---|
| This module facilitates the management of organizational team members and their associated permission levels. | Manage your team and control what each person can access. |
| Utilizing our proprietary algorithm, we analyze your data to provide actionable insights. | We look at your data and show you what's working. |
| Prior to commencing the onboarding process, please ensure all prerequisite information has been gathered. | Before you start, have your company info ready. |

### Tooltips and helper text

| Before | After |
|---|---|
| This field accepts alphanumeric characters with a minimum length of 8. | At least 8 characters, letters and numbers. |
| Enabling this option will propagate changes to all downstream dependencies. | Turning this on updates everything connected to it. |
| The specified value must conform to RFC 5322 email format. | Enter a valid email like name@example.com. |

### Empty states

| Before | After |
|---|---|
| No records found in the current dataset. | Nothing here yet. |
| There are currently no items matching the specified criteria. | No matches. Try different filters. |
| The requested resource collection is empty. | You haven't created any projects yet. Start your first one. |

---

## Quick Reference

When writing any UI copy, check these in order:

1. **Is it in the user's words?** Swap jargon using the substitution table.
2. **Is it active voice?** "We saved your changes" not "Changes have been saved."
3. **Is it short?** Cut every word that doesn't earn its place.
4. **Does it use contractions?** "You're" not "You are."
5. **Does it use numerals?** "3 items" not "three items."
6. **Does the button say what it does?** Verb + what happens.
7. **Does the heading describe the task?** "Your orders" not "Order Management."
8. **Would you say this to a friend?** If not, rewrite it.
