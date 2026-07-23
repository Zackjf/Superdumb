---
name: scannable-not-readable
description: "Apply this to EVERY UI screen, page, and component. People scan — they do not read. Structure all content for scanning: headlines that summarize, bullets over paragraphs, bold key phrases, front-loaded information. If a user has to read a paragraph to understand what to do, the screen has failed."
---

# Scannable, Not Readable

People do not read websites. They scan them. Eye-tracking studies (Nielsen Norman Group, repeatedly, for decades) show the same thing: users scan in an F-pattern, reading the first line, skimming down the left edge, and stopping only when something catches their eye. Then they click or they leave.

This isn't laziness. It's rational behavior. The user has a goal. They're hunting for the thing that helps them reach it. Every word they have to read that isn't that thing is a delay.

Design every screen as if the user will spend 3 seconds scanning before deciding whether to engage or bail. Because that's what they do.

---

## Headlines That Tell You What's Below

A headline's job is to let the user skip the content beneath it — or decide to read it. If the headline doesn't convey the key point, the content below it becomes invisible because the user won't read it to find out.

### Good headlines summarize; bad headlines label

| Good | Bad | Why it's bad |
|---|---|---|
| 3 orders need your attention | Orders | Doesn't tell you what about them |
| Your trial ends in 5 days | Account Status | Hides the urgency |
| Free shipping on orders over $50 | Shipping Policy | Nobody reads "Shipping Policy" |
| We couldn't process your payment | Error | What error? |
| Set up your store in 3 steps | Getting Started | Vague — started with what? |
| No results for "blue shoes" | Search Results | Doesn't tell you the outcome |

### Rules

- **Include the number.** "3 items in your cart" not "Items in your cart." The number is the most scannable element.
- **Include the status.** "Payment failed" not "Payment." "Invite sent" not "Invite."
- **Include the action.** "Review and pay" not "Checkout step 3."
- **Front-load the most important word.** "Payment failed — update your card" not "There was a problem processing your most recent payment."

---

## Bullets Over Paragraphs

On a UI screen, paragraphs are the enemy. A paragraph looks like a block of work to the scanner. Bullets look like a list of quick facts. Same information, completely different engagement.

### When to convert

Any time you have 2 or more distinct points in a block of text, convert to bullets.

**Before (paragraph):**
> Your plan includes up to 10 team members, 50GB of storage, priority support, and access to advanced analytics. You can upgrade at any time to add more members or storage.

**After (bullets):**
> **Your plan includes:**
> - Up to 10 team members
> - 50GB of storage
> - Priority support
> - Advanced analytics
>
> You can upgrade anytime.

The bulleted version communicates the same information in half the time because the user can scan vertically instead of reading horizontally.

### Rules

- **Max 2 sentences of prose on any UI screen** before converting to a structured format (bullets, a table, a list, a set of cards). If you've written a third sentence, stop and restructure.
- **Each bullet is one idea.** If a bullet has a comma followed by a different thought, split it.
- **Start each bullet with the distinctive word.** "10 team members" not "Up to a maximum of 10 team members." The number and the noun are what the scanner's eye grabs.
- **Parallel structure.** Each bullet should follow the same grammatical pattern. If one starts with a noun, they all start with nouns. If one starts with a verb, they all start with verbs.

---

## Bold the Key Phrase

In any block of text the user must read (help text, explanations, confirmation messages), bold the single most important phrase. This gives the scanner an anchor — they read the bold text first and only read the surrounding text if they need more context.

**Before:**
> When you delete your account, all your data including projects, files, and team associations will be permanently removed. This action cannot be undone. Your team members will be notified.

**After:**
> When you delete your account, **all your data will be permanently removed** — including projects, files, and team associations. **This cannot be undone.** Your team members will be notified.

### Rules

- **One bold phrase per paragraph.** If everything is bold, nothing is bold.
- **Bold the conclusion, not the setup.** Bold "all data will be removed" not "when you delete your account."
- **Bold the action item, not the background.** Bold "update your payment method by Friday" not "we noticed an issue with your billing."
- **Don't use bold for emphasis on random words.** Bold is for the key takeaway, not for making things LOUD.

---

## Numbers Instead of Words

Numbers are more scannable than words. The visual shape of "3" is distinct from surrounding text. The visual shape of "three" blends in.

| Scannable | Less scannable |
|---|---|
| 3 items in your cart | Three items in your cart |
| 2 steps remaining | Two steps remaining |
| Saves you $12/month | Saves you twelve dollars per month |
| 99.9% uptime | Ninety-nine point nine percent uptime |
| Used 7 of 10 seats | Used seven of ten seats |

### Rules

- **Always use numerals in UI.** 1, 2, 3 — not one, two, three. The only exception is "one" when it reads more naturally in a sentence ("You have one new message" is fine — but "1 new message" in a badge is better).
- **Include units.** "50GB" not "50." "3 days" not "3." Numbers without units force the user to read surrounding context.
- **Use human-scale numbers.** "1.2k" not "1,247" in summaries. Show the exact number on hover or in detail views. On dashboards and summary screens, round to what matters.

---

## Front-Load Important Information

Put the most important information first. Not the background. Not the context. Not the "let me explain why." The thing the user needs to know, right up front.

This is the inverted pyramid from journalism: lead with the conclusion, follow with details, end with background. On the web, most people never reach the end — so what's at the top is the only thing that's guaranteed to be seen.

### Examples

**Before (buries the lead):**
> Due to scheduled maintenance on our payment processing infrastructure, which is being upgraded to improve reliability and security, your next payment may be delayed by 1-2 days. We apologize for any inconvenience.

**After (front-loaded):**
> Your next payment may be delayed by 1-2 days. We're upgrading our payment system this week. No action needed from you.

**Before (buries the action):**
> We've updated our privacy policy to reflect changes in how we handle third-party data sharing, in compliance with recent regulatory requirements. Please review and accept the new terms to continue using your account.

**After (front-loaded):**
> **Accept our updated privacy policy to continue.** We've updated how we handle data sharing. [Read the changes]

### Rules

- **First sentence = what the user needs to know or do.** Always.
- **Second sentence = context, if needed.** Often not needed.
- **Third sentence = you probably don't need a third sentence on a UI screen.** Cut it.
- **If there's an action required**, the action goes first, the explanation goes second.

---

## Visual Hierarchy

Size, weight, color, and spacing all communicate importance. They tell the scanner's eye where to look first, second, and third — without the user having to read a single word.

### The hierarchy stack (top = most prominent)

1. **Page title / primary heading** — largest, heaviest text. One per page.
2. **Section headings** — clearly smaller than the title but larger than body text.
3. **Primary action (CTA button)** — high contrast, prominent position, distinct from secondary actions.
4. **Key data / highlighted numbers** — larger font, bold, or contrasting color.
5. **Body text / supporting content** — standard size, normal weight.
6. **Secondary actions / links** — visually subordinate to the primary action.
7. **Help text / metadata / footnotes** — smallest, lightest, least prominent.

### The squint test

Blur the page (literally squint at it, or apply a Gaussian blur in your design tool). You should still be able to answer:

1. **What is this page about?** (the heading should be visible)
2. **What's the main thing I can do here?** (the primary action should stand out)
3. **How is the content organized?** (the section breaks should be apparent)

If squinting produces a uniform gray blob, the visual hierarchy is flat and the user has to read everything to find what matters.

### Rules

- **One primary action per screen.** Make it visually dominant (filled button, high contrast, prominent position). Secondary actions are visually quieter (outlined button, text link, muted color).
- **Size encodes importance.** The most important number on a dashboard should be the largest text on the page. Don't make the chart title bigger than the metric.
- **Spacing groups and separates.** Elements that belong together are close together. Elements that are different topics have space between them. This is Gestalt proximity — it works without lines or borders.
- **Color draws attention.** Use color sparingly for emphasis. If everything is colorful, nothing stands out. Reserve high-saturation colors for status indicators, alerts, and the primary action.

---

## Anti-Patterns

### Paragraphs of text on UI screens
If a screen has more than 2 sentences of prose, it will not be read. Convert to bullets, headings, or structured content. Save paragraphs for blog posts, help docs, and legal pages — not for the product UI.

### Walls of uniform text
A page where every element is the same size, weight, and color is a page where nothing stands out. The scanner's eye has nowhere to land. Add hierarchy: make something bigger, bold something, add spacing between sections.

### Burying the action
"After reviewing the information above and confirming that all details are correct, you may proceed by clicking the button below." The user has to read an entire sentence to discover there's a button. Put the button where they can see it. Make the label descriptive. Let the supporting text be secondary.

### "Click here" and "Learn more" as standalone links
These phrases are meaningless when scanned. "Click here" tells you nothing about where you'll go. "Learn more" tells you nothing about what you'll learn. Use descriptive link text: "View pricing details," "Read the privacy policy," "See all 12 reviews."

### Dense tables with no visual breaks
A table with 20 rows and no alternating row colors, no bold headers, and no grouping is a wall of data. Add zebra striping, bold the headers, group rows by category, highlight key columns, and consider whether a table is even the right format (sometimes cards or a list are better for scanning).

### Information-dense dashboards with no hierarchy
Every metric displayed at the same size and prominence. The user can't tell what matters. Pick 2-3 hero metrics and make them large. Put everything else in a supporting position.

---

## The Test

Before shipping any screen:

1. **Show it to someone for 3 seconds, then hide it.** Ask them what the page is about and what they're supposed to do. If they can't answer, your hierarchy has failed.
2. **Squint at it.** Can you identify the heading, the primary action, and the content sections without reading any text?
3. **Count your prose sentences.** More than 2 in a row on a UI screen? Convert to bullets or structured content.
4. **Check your headlines.** Do they summarize the content below, or just label it? Could you understand the page by reading only the headlines?
5. **Check your numbers.** Are they numerals (3, 50, 99) or words (three, fifty, ninety-nine)? Use numerals.
6. **Check your bold.** Is the key phrase in each block bolded? Is only the key phrase bolded?
7. **Find the primary action.** Is it visually dominant? Would a scanner's eye find it within 2 seconds?
