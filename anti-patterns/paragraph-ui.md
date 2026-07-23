# Paragraph UI

Writing walls of explanatory text where fewer words or better structure would do.

## What It Looks Like

```
Welcome to your dashboard! This is where you'll find an overview
of all your recent activity including orders, messages, and
notifications. You can use the sidebar on the left to navigate
to different sections of the application. If you need help at
any time, click the help icon in the top right corner of the
screen. We recommend starting by setting up your profile, which
you can do by clicking on the Settings link below.
```

Nobody reads this. The user's eyes hit the block of text, glaze over,
and start looking for something to click.

## Why It Happens

AI agents are trained on prose. They explain things in full, grammatical
sentences with context, caveats, and transitions. That's great in a
conversation. In a UI, it's noise.

## Why It's Bad

- Users scan, they don't read. Research consistently shows people skip
  paragraph text in interfaces.
- Important information gets buried in the middle of a block.
- It takes up screen space that could show actual content.
- It makes the interface feel heavy before the user has done anything.

## What to Do Instead

Cut ruthlessly. Use structure instead of sentences. If you must explain,
use bullets, bold the key phrase, and cut everything that isn't essential.

### Before

```
To export your data, first select the date range you'd like to
export using the date picker below. Then choose the format you
would like your data exported in. We support CSV, JSON, and PDF
formats. Once you've made your selections, click the Export
button to begin the download. Please note that large exports
may take a few minutes to process, and you will receive an
email notification when your export is ready.
```

### After

```
Export Data

Date range:  [Last 30 days v]
Format:      [CSV v]

[Export]

Large exports are emailed when ready.
```

Same information. One-third the words. The form fields *are* the
explanation -- the user doesn't need to be told "select the date range"
when there's a date range picker right there.

### Before

```
Are you sure you want to delete this project? Deleting a project
will permanently remove all associated data including files,
comments, and activity history. This action cannot be undone.
Please type the project name below to confirm deletion.
```

### After

```
Delete "Acme Redesign"?

This removes all files, comments, and history.
Can't be undone.

Type "Acme Redesign" to confirm:
[                    ]

[Cancel]  [Delete Project]
```

### The Rule

If your UI text is more than two lines, ask: can this be a label, a
placeholder, a tooltip, or just removed entirely? The best UI text
is the text you didn't write.
