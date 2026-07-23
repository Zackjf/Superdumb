# Buried Primary Input

## What It Looks Like

The app's dashboard shows beautiful output — metrics, charts, generated content, reports. But the thing that FEEDS the system (the data source, the configuration, the seed content) is buried 3+ clicks deep in a sub-menu.

The empty dashboard says "No data yet" or "First run pending" — but doesn't link to where you'd fix that.

## Example

A content engine that monitors industry sources, extracts trends, and generates articles:

```
Dashboard (home page)
├── "Production line" — shows generated content      ← prominent
├── "Needs review" — shows pending approvals          ← prominent
├── "What to write next" — shows research findings    ← prominent
├── "Market signals" — shows concerns                 ← prominent
│
│   But...
│
├── Research (nav) → Sources (sub-nav) → Add source   ← 3 clicks deep
│
│   "Sources" is the INPUT that makes everything above possible.
│   No sources = no research = no findings = no content = empty dashboard.
```

The app proudly displays its outputs but hides the input that makes them all work.

## Why It Happens

Developers build outward from the data model. The system has a Research module, and Sources are a sub-entity of Research, so Sources live under Research in the navigation. This makes sense from a data-architecture perspective but not from a user perspective.

The user's mental model is: "I need to tell this tool what to watch, and then it does its thing." The input (sources) is step 1 of their mental model, but step 3 of the navigation.

## Why It's Bad

- New users see an empty dashboard with no obvious way to populate it
- The most important setup action requires learning the navigation hierarchy
- Empty states say "data will appear after the first scan" but don't link to where you add the scan targets
- Returning users who want to add a new source have to navigate away from their work
- The app appears broken until the user discovers the buried input

## What to Do Instead

1. **Surface the primary input on the home page.** A "Sources" section on the dashboard, or at minimum a prominent "Add a source" button visible from home.
2. **Link empty states to the input action.** "No findings yet — [Add sources to start monitoring →]"
3. **Put the input in the top-level navigation.** If sources drive everything, they deserve a top-level nav item, not a sub-page under Research.
4. **First-time onboarding should lead with the input.** "Welcome! Let's add your first source so the engine can start finding trends." Not "Here's your empty dashboard."
5. **Show input status on the dashboard.** "Monitoring 12 sources" with a link to manage them — keeps the input visible and accessible.

## The Test

For every app, ask: "What does this system need from the user to produce value?" That thing should be reachable in 1-2 clicks from the home page, and every "no data yet" empty state should link directly to it.
