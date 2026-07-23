# One-Way Doors

Actions with no undo, no back button, and no escape hatch.

## What It Looks Like

- A multi-step wizard where clicking "Back" resets all your progress.
- A "Delete" button with no undo, no trash, no recovery.
- An "Apply Changes" that overwrites the previous state with no way to revert.
- A form where navigating away silently discards everything you entered.
- An onboarding flow where you can't skip a step or return to fix one.

```
Step 1 of 4:  Company Details     [Next ->]
Step 2 of 4:  Team Members        [<- Back] [Next ->]

// User clicks Back. Step 1 is blank again.
// Everything they entered in Step 2 is also gone.
```

## Why It Happens

AI agents build the happy path: forward, forward, forward, done. Undo,
back-navigation, and state preservation are extra work that doesn't show
up in a basic demo. The agent writes `setState({})` on back-navigation
because it's the simplest implementation, not because it's the right one.

## Why It's Bad

- Users are afraid to explore. If every action feels permanent, they
  hesitate before clicking anything.
- Mistakes become catastrophic instead of recoverable.
- Multi-step forms that lose data on "Back" cause rage and abandonment.
- Users develop coping mechanisms (copying text to a notepad before
  submitting) that signal the UI has failed them.

## What to Do Instead

Make actions reversible wherever possible. Preserve state across steps.
Use soft deletes. Add undo.

### Before

```jsx
// Deleting a project -- instant and permanent
const handleDelete = async (projectId) => {
  await db.projects.delete(projectId);
  navigate('/projects');
};
```

### After

```jsx
// Soft delete with undo window
const handleDelete = async (projectId) => {
  await db.projects.update(projectId, {
    deletedAt: new Date(),
    deleteScheduledFor: addDays(new Date(), 30)
  });
  toast({
    message: 'Project moved to trash.',
    action: { label: 'Undo', onClick: () => restoreProject(projectId) },
    duration: 8000
  });
};
```

### Before

```jsx
// Multi-step form -- back button clears state
<WizardStep onBack={() => setCurrentStep(step - 1)} />
// Each step owns its own state, lost on unmount
```

### After

```jsx
// Multi-step form -- state preserved across all steps
const [formData, setFormData] = useState({});

<WizardStep
  initialValues={formData[step]}
  onNext={(values) => {
    setFormData({ ...formData, [step]: values });
    setCurrentStep(step + 1);
  }}
  onBack={(values) => {
    setFormData({ ...formData, [step]: values }); // save before going back
    setCurrentStep(step - 1);
  }}
/>
```

### The Spectrum of Safety

| Risk level | Pattern                                      |
|------------|----------------------------------------------|
| Low risk   | Just do it, with undo (e.g., archive email)  |
| Medium     | Confirm, then do it, with undo (e.g., delete) |
| High risk  | Confirm with friction, 30-day soft delete     |
| Irreversible | Type to confirm, explain consequences       |

Default to the safest option. Only escalate friction for truly
irreversible, high-impact actions.
