---
name: peak-and-finish-strong
description: "Apply when building any multi-step flow, onboarding, checkout, or task completion experience. The Peak-End Rule means users judge the whole experience by its best moment and its final moment. Don't build flat experiences where every screen gets the same energy — invest in a great ending and at least one moment of delight. Use for checkout confirmation, onboarding completion, task success screens, and any flow with a defined start and finish."
---

# Peak & Finish Strong

The Peak-End Rule (from psychologist Daniel Kahneman) states that people judge an experience primarily by two moments: the most intense point (the peak) and the final moment (the end). Everything in between fades in memory.

This means two things for UI:
1. Your success/completion/confirmation screen matters more than any screen before it
2. Including at least one moment of genuine delight makes the whole experience feel better in retrospect

Most AI-built UIs are flat — every screen gets the same neutral energy. This skill fixes that.

## The Ending: Make It Great

The last thing the user sees after completing a task is what they'll remember. This is usually a confirmation screen, a success state, or a "you're done" moment. Don't phone it in.

### What a good ending includes

1. **Clear confirmation** that the thing is done. Not ambiguous — definitive. "Your order is placed." "You're all set." "Subscription cancelled."
2. **Key details** the user might need: order number, date, what happens next, when to expect something.
3. **Next step** if there is one: "We'll email you tracking info" or "Your team can start using the workspace now."
4. **A moment of warmth.** This doesn't mean confetti on every screen. But the tone should shift from transactional to human: "Thanks for your order, Maria" beats "Order #4521 confirmed."

### Examples

**Good — order confirmation:**
> ### Thanks for your order!
> Your running shoes are on their way.
>
> **Order #1234** — Blue Running Shoes (Size 10)
> Estimated delivery: July 25-27
>
> We'll email you tracking info at maria@example.com.
>
> [Continue shopping]  [View your orders]

**Bad — order confirmation:**
> Order submitted successfully.
> Reference: ORD-a8f3c91b-2d4e-47c1
> [OK]

The good version has warmth, useful details, and clear next steps. The bad version has a UUID and a button that goes nowhere specific.

### Other ending moments to invest in

- **Onboarding completion**: "You're all set! Here's what you can do first:" with 2-3 suggested starting actions
- **Form/application submission**: "We received your application. Here's what happens next..." with a timeline
- **Account setup**: "Welcome to [product]!" with a personalized starting point, not a blank dashboard
- **Cancellation**: even negative endings deserve care. "We're sorry to see you go. Your access continues until [date]. If you change your mind, you can resubscribe anytime."
- **Export/download completion**: "Your export is ready!" with a prominent download link and info about what was exported

## The Peak: One Moment of Delight

Somewhere in the flow, include one moment that's unexpectedly good. This becomes "the peak" in the user's memory and elevates the entire experience.

### Delight that works

- **Progress celebration**: when the user hits a milestone (first order, 100th post, profile complete), acknowledge it. Not a modal that blocks them — a brief, warm acknowledgment.
- **Personality in microcopy**: one piece of copy that makes them smile. An empty state that's playful. A loading message that's clever. A 404 page that's charming. Don't overdo it — one moment of personality is delightful, personality on every screen is exhausting.
- **Speed as delight**: something that loads instantly when they expected to wait. Instant search results. Instant saving. This is an underrated form of delight.
- **Smart anticipation**: showing them exactly what they need before they ask. "Looks like you left something in your cart" with the item visible. Auto-filling a form they expected to be manual.

### Delight that doesn't work

- **Confetti/animation on everything**: the first time is fun, the 50th time is annoying
- **Forced celebration for trivial actions**: "Amazing! You updated your email address!" feels patronizing
- **Delight that slows them down**: a cute loading animation that takes 3 seconds when the data was ready instantly
- **Delight at inappropriate moments**: don't celebrate when the user is canceling their account or reporting an error

### The calibration test

Match the intensity of the delight to the significance of the moment:
- **Completed setup after 10 minutes of effort** → celebration, congratulations, maybe a brief animation
- **Saved a settings change** → a quiet checkmark and "Saved." That's it.
- **First sale on their new store** → a genuine moment of congratulations with specifics ("Your first order! Someone in Austin just bought Blue Widgets.")
- **Deleted an item** → absolutely no celebration

## Building the Emotional Arc

Think of a multi-step flow as having an emotional shape:

```
Engagement ↑
            ╱╲           ╱╲  ← peak moment
           ╱  ╲         ╱  ╲
     ╱╲   ╱    ╲       ╱    ╲  ← strong ending
    ╱  ╲ ╱      ╲     ╱      ╲
───╱    ╳        ╲   ╱        ╲───
  start         middle        end
```

Not every step needs to be a peak. Most steps are functional — enter shipping, pick a date, confirm details. That's fine. But the experience should not be a flat line:

```
Engagement ↑
    ──────────────────────────  ← flat = forgettable
  start         middle        end
```

Identify the one step that can feel special, and the ending. Put your energy there.

## Anti-patterns

**The dead-end success screen.** "Done." with a single "OK" button that goes to... where? The home page? A blank dashboard? Success screens should have clear next steps.

**The anticlimactic ending.** The user completes a 5-minute checkout flow and sees "Order placed" in small text, no details, no warmth. This is the most important screen in the flow and it looks like an error page.

**Celebration overkill.** Confetti, animations, and "AMAZING!" on every single action. When everything is celebrated, nothing feels special. Reserve strong positive feedback for genuinely meaningful moments.

**Ignoring negative endings.** Cancellation and deletion flows still need good endings. "Your account has been deleted" should include what happens next, how long data is retained, and how to come back if they change their mind. Don't make them feel punished for leaving.
