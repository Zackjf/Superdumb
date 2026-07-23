# Wall of Options

A settings page with every option in a flat list, no grouping, no hierarchy.

## What It Looks Like

```
Settings
-------------------------------------------------
Language:              [English v]
Theme:                 [Light v]
Email notifications:   [x]
Push notifications:    [x]
SMS notifications:     [ ]
Auto-save interval:    [5 min v]
Default currency:      [USD v]
Date format:           [MM/DD/YYYY v]
Time zone:             [UTC-5 v]
Two-factor auth:       [Disabled v]
Session timeout:       [30 min v]
API rate limit:        [1000/hr v]
Export format:          [CSV v]
Page size:             [25 v]
Profile visibility:    [Public v]
Compact mode:          [ ]
Show tooltips:         [x]
Keyboard shortcuts:    [x]
```

Eighteen options. No sections. No indication of which ones matter. The user
who just wants to turn on dark mode has to scan the entire list.

## Why It Happens

AI agents enumerate every configurable value and render them sequentially. It's
the most literal implementation of "make these things configurable." There's no
decision about what to group, what to hide, or what matters most.

## Why It's Bad

- Users can't find what they need without reading everything.
- Important settings (like two-factor auth) sit next to trivial ones (tooltips).
- It signals that the app doesn't know what matters.
- Users avoid the page entirely because it feels overwhelming.

## What to Do Instead

Group by concern. Lead with the most-changed settings. Hide advanced options
behind a toggle or a separate section.

### Before

```
Settings
  [18 options in a flat list]
```

### After

```
Settings

Appearance
  Theme:             [Light v]
  Compact mode:      [ ]
  Language:           [English v]

Notifications
  Email:             [x]
  Push:              [x]
  SMS:               [ ]

Security
  Two-factor auth:   [Enable]
  Session timeout:   [30 min v]

Advanced               [Show]
  (collapsed by default: API rate limit, export format,
   date format, auto-save interval, page size)
```

Three to four options per group. Scannable headings. The user finds what they
need in seconds. The rarely-touched options are still accessible but not
competing for attention.

### Rule of Thumb

If a settings page has more than 5-7 visible options without a heading,
it needs grouping. If it has more than 10 visible options total, some
should be collapsed or moved to a sub-page.
