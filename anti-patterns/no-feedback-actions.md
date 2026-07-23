# No-Feedback Actions

Buttons that do something but show nothing when clicked.

## What It Looks Like

The user clicks "Save." Nothing happens. No spinner, no toast, no color
change, no disabled state. The button just sits there. Did it work? They
wait. They click again. Now they've saved twice -- or submitted two
payments, or sent two invitations.

```jsx
// What the agent builds
<button onClick={() => saveData(formValues)}>
  Save
</button>
```

The function runs. The network request fires. The button looks exactly the
same the entire time. Success or failure, the UI is silent.

## Why It Happens

AI agents focus on making the action work, not on communicating that it
worked. The function call is the goal; the feedback is an afterthought.
The agent tests by checking the database or console, not by watching the
screen with human eyes.

## Why It's Bad

- Users don't know if their action succeeded, so they retry.
- Double submissions cause real damage: duplicate orders, double charges,
  repeated emails.
- Even when harmless, silence feels broken. The user loses trust.
- Slow operations (network calls, file uploads) feel frozen without
  progress indicators.

## What to Do Instead

Every user action needs a visible response. At minimum: a loading state
while processing, and a success/error state when done.

### Before

```jsx
<button onClick={() => saveData(formValues)}>
  Save
</button>
```

### After

```jsx
const [status, setStatus] = useState('idle');

<button
  disabled={status === 'saving'}
  onClick={async () => {
    setStatus('saving');
    try {
      await saveData(formValues);
      setStatus('saved');
      setTimeout(() => setStatus('idle'), 2000);
    } catch (e) {
      setStatus('error');
    }
  }}
>
  {status === 'saving' && 'Saving...'}
  {status === 'saved'  && 'Saved'}
  {status === 'error'  && 'Failed -- try again'}
  {status === 'idle'   && 'Save'}
</button>
```

### The Minimum Feedback Checklist

1. **While processing**: disable the button, show a spinner or "Saving..."
2. **On success**: show confirmation (toast, checkmark, text change)
3. **On failure**: show what went wrong and what to do next
4. **Prevent doubles**: disable the button during the request

### The Test

Click every button in your UI and look only at the screen. If you can't
tell whether the action worked without opening the console or refreshing
the page, the feedback is missing.
