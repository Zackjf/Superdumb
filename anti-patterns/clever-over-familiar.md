# Clever Over Familiar

Inventing novel UI components for problems that already have standard solutions.

## What It Looks Like

- A radial/circular date picker instead of a standard calendar widget.
- A drag-to-reorder interface when a simple numbered list or checkboxes
  would do.
- A custom color-coded tag system when a dropdown with labels would work.
- A swipe-to-navigate carousel for what should be tabs.
- A node-based visual flow editor for a three-step settings form.

```jsx
// AI builds a custom "priority wheel" component
<PriorityWheel
  segments={['Low', 'Medium', 'High', 'Critical']}
  onRotate={handlePriorityChange}
  animationDuration={300}
/>
```

When all the user needed was:

```jsx
<select>
  <option>Low</option>
  <option>Medium</option>
  <option>High</option>
  <option>Critical</option>
</select>
```

## Why It Happens

AI agents have seen thousands of creative UI components in their training
data. When given freedom to "build a way to pick X," they sometimes reach
for the most interesting solution rather than the most familiar one.
Novel components also look impressive in demos.

## Why It's Bad

- Users have to learn how it works before they can use it. A standard
  dropdown takes zero learning.
- Novel components break accessibility. Screen readers, keyboard
  navigation, and touch devices all expect standard patterns.
- Custom widgets have more bugs. A battle-tested `<select>` has decades
  of fixes behind it.
- "Creative" interactions often fail on mobile, on slow connections,
  or with assistive technology.
- Maintenance cost is higher. Every custom component is code you own forever.

## What to Do Instead

Use the most boring, standard component that solves the problem. Save
creativity for the product's actual differentiating features, not for
picking a date.

### Before

```
Choose a date:   [custom radial date picker with draggable hands]
Choose a color:  [custom HSL wheel with click-to-sample]
Set priority:    [draggable slider with snap points and haptic labels]
```

### After

```
Choose a date:   [standard calendar picker]
Choose a color:  [grid of 8 preset colors, or type a hex code]
Set priority:    [dropdown: Low / Medium / High / Critical]
```

### The Decision Rule

Before building a custom component, ask:

1. Does a native HTML element or standard library component do this?
2. Will the user understand it without instructions?
3. Does it work with keyboard, screen reader, and touch?
4. Is the "creative" version solving a real problem, or just looking cool?

If the answer to #1 is yes, use it. Boring UI that works beats clever UI
that confuses.
