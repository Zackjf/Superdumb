# Developer Vocabulary

Using programmer jargon in user-facing interfaces.

## What It Looks Like

```
Error: Failed to authenticate. Invalid credentials supplied.
```

```
Initialize your workspace to get started.
```

```
This action will terminate your active session instance.
```

```
Configuration parameters have been deprecated.
Please update your query payload.
```

The user reads these and feels like they opened someone else's mail.

## Why It Happens

AI agents write code all day. The words "authenticate," "initialize,"
"instance," "payload," "query," "repository," "configuration," "terminate,"
"deprecated," and "parameter" are their native language. When generating
UI text, they reach for the words nearest at hand. Those words are
technically precise and unambiguous -- in a codebase. In a UI, they're
exclusionary.

## Why It's Bad

- Users don't know what "authenticate" means. They know "sign in."
- "Terminate session" sounds violent. "Sign out" is clear.
- "Deprecated" means nothing to a non-developer. "No longer available" does.
- Every unfamiliar word costs trust. The user feels like the product
  wasn't built for them.

## What to Do Instead

Translate every piece of user-facing text into the words a person would
use to describe the same thing to a friend.

### Before / After

| Developer word   | Human word                |
|------------------|---------------------------|
| Authenticate     | Sign in                   |
| Credentials      | Email and password        |
| Initialize       | Set up                    |
| Instance         | (just remove it)          |
| Payload          | Data / info               |
| Query            | Search                    |
| Repository       | Project                   |
| Configuration    | Settings                  |
| Terminate        | End / stop / sign out     |
| Deprecated       | No longer available       |
| Parameter        | Option / setting          |
| Execute          | Run                       |
| Propagate        | Spread / apply            |
| Instantiate      | Create                    |
| Persist          | Save                      |

### Before

```
Error: Authentication failed.
Please verify your credentials and retry.
```

### After

```
Wrong email or password. Try again.
```

### Before

```
Initialize a new repository to begin.
```

### After

```
Create a new project to get started.
```

### The Test

Read every string in your UI out loud. If you'd feel weird saying it to a
friend over coffee, rewrite it. "Hey, you need to authenticate with your
credentials" -- nobody talks like that. "Hey, sign in with your email and
password" -- that's human.
