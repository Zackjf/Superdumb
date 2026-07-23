---
name: outsider-review
description: "REVIEW SKILL. Run this AFTER building any UI, before presenting it as done. Walk every screen as four different people: a first-time visitor, someone in a rush, a non-technical person, and someone on their phone. Find where they'd get stuck, confused, or lost. This is the final quality gate — nothing ships without it. Use after completing any UI build, page, flow, or component."
---

# Outsider Review

You just built something. You know how it works because you built it. That knowledge is now blinding you to every problem a real user would hit. This skill forces you to forget what you know and walk the UI as an outsider.

## The Four Walks

Walk every screen four times, as four different people. Each one catches different problems.

### Walk 1: The First-Timer

You've never seen this product before. You don't know the terminology, the navigation, or the flow. You just arrived.

Ask at each screen:
- **What is this page for?** Can I tell within 5 seconds? If I have to read a paragraph to understand, the heading has failed.
- **What am I supposed to do?** Is there one clear action, or am I choosing between 5 equally-weighted options?
- **Do I understand every word?** Any word I wouldn't use in conversation with a friend? Any jargon, any technical terms, any internal product language?
- **Where do I go next?** Is the path forward obvious, or do I need to hunt?
- **Am I lost?** Do I know where I am in the site? Is something highlighted in the nav? Is there a breadcrumb? Can I get back to where I started?

### Walk 2: The Rusher

You're in a hurry. You have 30 seconds. You know roughly what you want but you need to find it and do it fast.

Ask at each screen:
- **Can I find the thing I need in 3 seconds?** If I'm scanning (not reading), does the visual hierarchy guide me to the right spot?
- **Can I complete the action without reading anything?** Are button labels clear enough that I can just click? Or do I need to read surrounding text to understand what each button does?
- **Is there anything blocking me?** A modal I have to close? A cookie banner covering the action? A loading spinner with no indication of how long?
- **How many clicks to done?** Can it be fewer?

### Walk 3: The Non-Technical Person

You're someone's parent or grandparent. You use your phone for photos, messages, and maybe online shopping. You don't know what a "dashboard" is, what "syncing" means, or why there are so many settings.

Ask at each screen:
- **Would I know what to do here?** If the answer requires any technical knowledge, the UI has failed.
- **Would any word confuse me?** "Settings" is OK. "Configuration" is not. "Your orders" is OK. "Order management" is not. "Sign in" is OK. "Authenticate" is absolutely not.
- **Would I be afraid to click anything?** If I'm not sure what a button does and it might do something scary (delete, charge, send), I won't click it. Are destructive actions clearly labeled and separated from safe actions?
- **Would I know if it worked?** After I click the main button, is it obvious that the thing happened? Or does the page just... sit there?

### Walk 4: The Phone User

You're on a phone. Maybe on a bus. Maybe in bed. One hand. Scrolling with your thumb.

Ask at each screen:
- **Can I reach the primary action with my thumb?** Bottom half of screen = easy. Top corners = stretch. Is the important stuff in the easy zone?
- **Can I read everything?** Any text below 16px? Any text that requires landscape mode or zooming?
- **Can I tap the right thing?** Are buttons and links at least 44×44px? Is there enough spacing between tappable elements that I won't mis-tap?
- **Does the page work in portrait?** Don't assume landscape. Most people hold their phone upright.
- **Is any content hidden behind hover?** Hover doesn't exist on touch. Tooltips, hover menus, hover previews — all invisible here.
- **Does anything take forever to load?** Large images with no lazy loading? Heavy scripts? On a 3G connection, does this page still work?

## The Five-Second Test

Before the detailed walks, do this quick test:
1. Look at the screen for exactly 5 seconds
2. Look away
3. Answer: What was this page about? What was I supposed to do?

If you can't answer both questions, the page fails. The headline, visual hierarchy, or primary action isn't clear enough.

## How to Record Findings

For each issue found, note:

| Screen | Walk | Issue | Fix | Severity |
|---|---|---|---|---|
| Checkout step 2 | Rusher | Can't find the "Continue" button — it's below the fold | Move above fold or make sticky at bottom | Critical |
| Settings | Non-technical | "Webhook configuration" heading means nothing | Rename to "Notifications" or "Connections" | Major |
| Dashboard | Phone | Stats cards require horizontal scroll | Stack vertically on mobile | Major |
| Profile edit | First-timer | No indication that changes auto-save | Add "Changes saved" feedback | Minor |

Present findings to the user ordered by severity: Critical → Major → Minor.

## After the Review

- Fix all Critical issues before presenting the work as done
- Fix Major issues if time allows, or flag them clearly
- Log Minor issues for future improvement
- If you find more than 3 Critical issues, the UI needs a rethink, not a patch

## Anti-patterns

**Skipping the review for "simple" pages.** Simple pages still have a primary action, headings, and labels. They can still use jargon, hide the CTA, or fail on mobile. Every page gets reviewed.

**Reviewing your own work from your own perspective.** You know the product. You know what every button does. You know the data model. You are the worst possible reviewer of your own UI. The four walks force you to simulate ignorance. Take them seriously.

**Fixing problems by adding more text.** If the user didn't understand the page, the fix is rarely "add an explanation paragraph." The fix is: simplify the heading, clarify the button label, reduce the number of options, or change the layout. More text is almost never the answer in a UI.
