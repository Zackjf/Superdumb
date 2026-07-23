---
name: accessible-by-default
description: "Apply to EVERY screen, component, and interaction you build. Accessibility is not a checklist bolted on at the end — it's a baseline for respecting the full range of humans who use your product. Large tap targets, high contrast, keyboard navigation, works one-handed, works stressed, works on a bad connection. Use whenever building any user-facing UI."
---

# Accessible by Default

Accessibility isn't about compliance checklists or screen reader edge cases. It's about building for real humans in real conditions: people with poor vision, shaky hands, one hand occupied, bright sunlight washing out their screen, slow internet, stress, distraction, fatigue.

When you build for these conditions, EVERYONE benefits. Large tap targets help people with motor impairments AND people on a bumpy bus. High contrast helps low-vision users AND people in direct sunlight. Clear focus states help keyboard users AND power users who never touch a mouse.

## Visual

### Contrast
- Text must have at least 4.5:1 contrast ratio against its background (WCAG AA). Use a contrast checker — your eye is not reliable.
- Large text (18px+ or 14px+ bold) needs at least 3:1.
- Interactive elements (buttons, links, form borders) need at least 3:1 against their background.
- Don't rely on color alone to convey meaning. A red error needs more than color: add an icon, bold text, or a label. A status dot needs a text label too: "● Active" not just a green dot.

### Text
- Body text: minimum 16px on web. Never smaller for anything the user needs to read.
- Don't disable browser zoom. Ever. Some people need it.
- Line height: at least 1.5x the font size for body text. Cramped text is hard to read for everyone.
- Avoid all-caps for more than a few words. It's harder to read and screen readers may spell it out letter by letter.
- Don't justify text (align left). Justified text creates uneven word spacing that makes reading harder.

### Motion
- Respect `prefers-reduced-motion`. If the user has set this OS preference, skip animations, parallax, and auto-playing videos.
- Never use flashing or strobing content. It can trigger seizures.
- Auto-playing carousels and slideshows are hostile to everyone. If you must use them, provide pause controls and never auto-advance faster than 5 seconds.

## Interactive

### Tap/click targets
- Minimum 44×44px for any tappable element (buttons, links, checkboxes, radio buttons).
- At least 8px spacing between adjacent tap targets so a mis-tap doesn't hit the wrong one.
- Don't put important actions next to destructive actions without spacing.
- Make the entire row/card tappable in lists, not just the text label.

### Keyboard navigation
- Every interactive element must be reachable and operable with keyboard (Tab, Enter, Space, arrows).
- Focus order must follow visual order (top to bottom, left to right in LTR layouts).
- Focus must be visible. Use a clear focus ring/outline. Don't remove `:focus` styles — restyle them if the default is ugly, but never hide them.
- Modals must trap focus inside them (tabbing shouldn't escape behind the modal) and return focus to the trigger element when closed.
- Skip-to-content link at the top of each page for keyboard users to bypass navigation.

### Touch
- Support touch gestures where expected (swipe to go back, pull to refresh) but never make them the ONLY way to do something. Always have a button alternative.
- Don't use hover-dependent interactions (tooltips, dropdown menus that open on hover). Touch devices don't have hover. Use click/tap triggers instead.
- Long-press actions need a visible alternative. Don't hide functionality behind gestures with no visual indicator.

## Semantic HTML

Using the right HTML elements gives you accessibility for free:
- `<button>` for actions (not `<div onclick>`). Buttons are keyboard-focusable and announced correctly.
- `<a>` for navigation (not `<span onclick>`). Links are keyboard-navigable and announced as links.
- `<input>`, `<select>`, `<textarea>` for form controls. Not custom divs.
- `<label>` connected to every form input. Either wrapping the input or using `for`/`id`.
- `<h1>` through `<h6>` in order. Don't skip heading levels. Screen readers use heading structure for navigation.
- `<nav>` for navigation, `<main>` for main content, `<footer>` for footer. Landmarks help screen reader users orient.
- `<img alt="description">` for meaningful images. `alt=""` for decorative images.
- `<table>` with `<th>` for tabular data. Not divs styled as tables.

## Forms

- Every input has a visible label. Placeholder text is NOT a label — it disappears on focus.
- Required fields are indicated (either mark all required, or mark optional ones — pick one approach consistently).
- Error messages are associated with their fields using `aria-describedby` or by placing them inside the `<label>`.
- Group related fields with `<fieldset>` and `<legend>` for radio groups and checkbox groups.
- Auto-focus the first field on the page (or the first error field after validation).

## Real-World Conditions

### One-handed use
- Primary actions should be reachable with one thumb on a phone (bottom half of screen, not top corners).
- Consider bottom navigation bars for mobile instead of top hamburger menus.
- Don't require two-hand gestures (pinch to zoom is fine — it's a standard OS gesture).

### Bad connections
- Pages should be usable before JavaScript fully loads (progressive enhancement).
- Show loading states, not blank screens.
- Don't make the user lose their work if the connection drops mid-form. Auto-save or show a warning.

### Stress and distraction
- Timed interactions are hostile. If you must use a timer (for security, not for pressure), warn before time expires and offer to extend.
- Don't auto-dismiss important messages (error toasts that disappear after 3 seconds). Errors must persist until the user dismisses them or fixes the problem.
- CAPTCHAs and complex verification flows should be a last resort, not a default.

## Anti-patterns

**"We'll add accessibility later."** If it's not accessible when built, it won't become accessible later. The cost of retrofitting is 10x the cost of building it right.

**Removing focus outlines for aesthetics.** `:focus { outline: none }` is one of the most common accessibility violations. If the default outline is ugly, replace it with a custom one. Never remove it.

**Icon-only buttons with no label.** A trash can icon with no text and no `aria-label`. Some users can't identify the icon. Always add at minimum an `aria-label` for icon-only buttons, and prefer visible text labels where space allows.

**Custom controls built from divs.** A `<div>` styled to look like a dropdown, but with no keyboard support, no ARIA roles, and no focus management. Use native HTML elements. If you must build custom, implement full ARIA patterns.

**Tiny tap targets.** 24×24px buttons with 2px spacing between them. On a phone, on a moving bus, with cold fingers — this is unusable. 44×44px minimum, 8px spacing.
