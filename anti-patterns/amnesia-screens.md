# Amnesia Screens

Screens that forget context the user already established.

## What It Looks Like

A confirmation dialog:

```
+----------------------------------+
|  Are you sure?                   |
|                                  |
|  This action cannot be undone.   |
|                                  |
|       [Cancel]  [Confirm]        |
+----------------------------------+
```

Sure about *what*? The user clicked "Delete" on "Q3 Marketing Report"
three seconds ago, but the dialog has already forgotten the noun.

More examples:

- A checkout page that says "Complete your purchase" but doesn't show
  what's being bought or the total.
- An edit form that loads with blank fields instead of the current values.
- An error page that says "Something went wrong" with no indication of
  what the user was trying to do or how to recover.
- A search results page that clears the search box after navigating back.

## Why It Happens

AI agents build components in isolation. The confirmation dialog is a
generic `<ConfirmDialog>` that takes `onConfirm` and `onCancel` props
but not a `description` prop. The edit form fetches on mount but doesn't
pre-populate. Each screen is built without thinking about what the user
was looking at one second ago.

## Why It's Bad

- "Are you sure?" without context forces the user to remember what they
  clicked. Under pressure, they guess wrong.
- Blank edit forms make users think their data is gone.
- Context-free errors leave users stuck with no next step.
- Cleared search boxes force re-typing and punish exploration.

## What to Do Instead

Every screen should carry forward the context that led to it. Name the
thing. Show the state. Remind the user where they are.

### Before

```
Are you sure?
This action cannot be undone.
[Cancel] [Confirm]
```

### After

```
Delete "Q3 Marketing Report"?

This will permanently remove the report and its 14 comments.
Can't be undone.

[Cancel] [Delete Report]
```

### Before

```jsx
// Edit form loads blank
const EditProfile = () => {
  const [name, setName] = useState('');
  const [bio, setBio] = useState('');
  return <form>...</form>;
};
```

### After

```jsx
// Edit form loads with current values
const EditProfile = ({ user }) => {
  const [name, setName] = useState(user.name);
  const [bio, setBio] = useState(user.bio);
  return <form>...</form>;
};
```

### Before

```
Something went wrong. Please try again.
```

### After

```
Couldn't save your changes to "Project Alpha."
The server didn't respond. Check your connection and try again.

[Retry]  [Go back to project]
```

### The Context Checklist

For any screen transition, verify:

1. Does the new screen name the thing being acted on?
2. Does it show the current state (not a blank slate)?
3. If something failed, does it say what and suggest a next step?
4. If the user goes back, is their previous input still there?

If any answer is no, the screen has amnesia.
