# Hierarchy Rules

Rules for visual and information hierarchy. Every screen must answer: "What should the user do first?"

---

## Rule 1: One Primary Action Per Screen

Every screen has exactly ONE thing you most want the user to do. Everything else is secondary or tertiary.

| Layer | Visual treatment | Example |
|-------|-----------------|---------|
| **Primary** | Large, high-contrast, filled button. Prominent position. | "Place order" |
| **Secondary** | Outlined or muted button. Near the primary but visually quieter. | "Save as draft" |
| **Tertiary** | Text link or icon. Low visual weight. | "Cancel", "Learn more" |

**Test:** Cover the screen with your hand and reveal it slowly. The primary action should be the first thing you notice. If two things compete for attention, one of them needs to be demoted.

---

## Rule 2: The Squint Test

Blur your eyes or step back from the screen. You should still be able to identify:

1. What this screen is about (headline)
2. Where the primary action is (button)
3. How the content is grouped (sections)

If everything blurs into a uniform gray, your hierarchy is flat. Fix it by increasing contrast between levels.

**How to apply:**
- Take a screenshot, apply a 10px Gaussian blur
- Or literally squint at your screen from arm's length
- The visual "hot spots" that survive the blur are your hierarchy

---

## Rule 3: Visual Weight

Four tools control what gets noticed first. Use them deliberately, not accidentally.

| Tool | More weight | Less weight |
|------|------------|-------------|
| **Size** | 24px+ heading | 14px body text |
| **Color** | Brand color, high saturation | Gray, low saturation |
| **Contrast** | Dark on light (or light on dark) | Gray on light gray |
| **Whitespace** | Surrounded by space (isolated) | Packed tightly with other elements |

**Hierarchy formula:** Size first, then color, then contrast, then whitespace. Changing size has the biggest impact. Changing whitespace has the most subtle impact.

**Common mistake:** Making something bold AND colored AND large AND underlined. One signal is usually enough. If you need three signals, the surrounding content is too noisy.

---

## Rule 4: Above the Fold

The first viewport (before scrolling) must contain:

| Element | Required? | Notes |
|---------|-----------|-------|
| Screen title / headline | Yes | Users must know where they are. |
| Primary action | Yes | If users must scroll to find the main CTA, most won't. |
| Value statement or key content | Yes | One sentence or metric that justifies being on this screen. |
| Full form / all details | No | Content below the fold is fine if users know it's there. |

**Exception:** Long-form content pages (articles, docs) don't need a CTA above the fold. The content IS the value.

**Scroll indicator:** If critical content is below the fold, make sure something is visually "cut off" at the fold line so users know to scroll.

---

## Rule 5: Secondary vs. Tertiary Actions

| | Secondary | Tertiary |
|---|-----------|----------|
| **Purpose** | Alternative to the primary | Escape hatch, auxiliary |
| **Examples** | "Save draft," "Export," "Share" | "Cancel," "Skip," "Learn more" |
| **Appearance** | Outlined button or muted fill | Text link or small icon |
| **Position** | Adjacent to primary | Away from primary (top-left, bottom-left) |
| **Risk if clicked accidentally** | Low (non-destructive) | Low (reversible or navigational) |

**Anti-pattern:** Putting "Cancel" and "Delete" as equal-weight buttons. "Delete" is destructive and should be styled as a danger action (red, outlined). "Cancel" is tertiary (text link).

---

## Rule 6: Mobile Hierarchy

Mobile screens have less space, so hierarchy matters even more.

**Stack, don't shrink.** Don't try to fit a desktop layout into 375px. Stack elements vertically in priority order.

| Desktop | Mobile |
|---------|--------|
| Two-column layout | Single column, most important column first |
| Inline secondary actions | Hidden in "..." overflow menu |
| Sidebar nav | Bottom tab bar or hamburger menu |
| Horizontal button row | Full-width stacked buttons (primary on top) |

**Sticky CTA:** On mobile, the primary action button should be sticky at the bottom of the viewport if:
- The page is scrollable
- The CTA is the main purpose of the page (checkout, sign up, submit)
- The user needs to scroll past content before acting

**Do not** make the sticky CTA too tall. 48-56px height max. It should not eat more than 10-15% of the viewport.

---

## Rule 7: The Competing CTAs Problem

When two buttons look equally important, users choose neither.

**Symptoms:**
- Two filled, colored buttons side by side
- "Sign up free" and "Book a demo" both full-width and bright
- A page where your eye bounces between two focal points

**Fixes:**

| Problem | Fix |
|---------|-----|
| Two primary buttons | Decide which matters more. Make the other secondary (outlined). |
| CTA in hero AND CTA in nav | Make the nav CTA smaller or text-only. The hero CTA owns attention. |
| Banner CTA competing with page CTA | Remove the banner or make it dismissible. |
| "Learn more" link same size as "Sign up" | Drop "Learn more" to a text link below the primary CTA. |

---

## Rule 8: Good vs. Bad Hierarchy Examples

### Example A: Signup Page

| | Bad | Good |
|---|-----|------|
| Headline | "Welcome to our platform" (generic) | "Start building in 2 minutes" (specific, value-driven) |
| Primary CTA | Same size as "Learn more" | Large, filled, only colored button on screen |
| Social login | Below the form, small text links | Above the email form, equal-weight buttons (Google, GitHub) |
| Legal text | Same size as form labels | 12px, muted gray, below the CTA |

### Example B: Dashboard

| | Bad | Good |
|---|-----|------|
| Metrics | 12 equal-sized cards | 3 large metrics up top, secondary stats below |
| Quick actions | Buried in a dropdown | 2-3 buttons directly below the metrics |
| Navigation | 20 sidebar items, no grouping | 6 grouped sections, icons + labels |
| Alerts | Red banner at top, same weight as metrics | Inline alert within the relevant metric card |

### Example C: Pricing Page

| | Bad | Good |
|---|-----|------|
| Plans | 5 plans, all same visual weight | 3 plans, middle one highlighted ("Most popular") |
| Feature list | Wall of text under each plan | Checkmark comparison table |
| CTA buttons | All say "Get started," same color | Recommended plan has a filled button; others are outlined |
| Toggle | No annual option | Monthly/Annual toggle with savings badge ("Save 20%") |

---

## Hierarchy Cheat Sheet

When in doubt, rank every element on the screen from 1 to N by importance, then assign visual weight accordingly:

| Rank | Treatment |
|------|-----------|
| 1 | Largest, boldest, most colorful, most whitespace |
| 2 | Large but less colorful, or colorful but smaller |
| 3 | Medium size, neutral color |
| 4+ | Small, gray, minimal space |

If two elements share the same rank, one of them is wrong. Decide which matters more.
