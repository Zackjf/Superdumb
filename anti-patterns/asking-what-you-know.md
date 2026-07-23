# Asking What You Know

Forms that demand information the system already has or could easily infer.

## What It Looks Like

The user is logged in. Their profile has their name, email, and timezone.
They click "Create Event" and see:

```
Create Event
------------------------------
Your name:     [              ]
Your email:    [              ]
Time zone:     [Select...   v]
Country:       [Select...   v]
Currency:      [Select...   v]
Event title:   [              ]
Event date:    [              ]
```

Five of seven fields could be filled automatically. The user is typing
information the system already knows, just to satisfy a form.

## Why It Happens

AI agents build forms from data requirements. The function needs a name,
email, timezone, country, and currency -- so the agent puts an input for
each. It doesn't think about what's already available from the session,
the user profile, the browser, or the request context.

## Why It's Bad

- Every unnecessary field is friction. Friction causes abandonment.
- Asking for known information feels disrespectful of the user's time.
- It signals that the system isn't paying attention.
- More fields mean more validation errors, more time, more drop-off.

## What to Do Instead

Pre-fill from what you know. Only ask for what's genuinely new.

### Before

```
Shipping Address
------------------------------
Full name:     [              ]
Email:         [              ]
Country:       [Select...   v]
Address:       [              ]
City:          [              ]
State:         [Select...   v]
ZIP:           [              ]
Phone:         [              ]
```

### After

```
Shipping Address
------------------------------
Full name:     [Jamie Chen         ]  <- from profile
Email:         jamie@example.com      <- shown, not editable (from session)

Address:       [              ]
City:          [              ]
State:         [              ]
ZIP:           [              ]

Country:       United States          <- from IP / browser locale
Phone:         [              ]       <- only if required for shipping
```

### Common Things You Can Infer

| Instead of asking for... | Get it from...                     |
|--------------------------|------------------------------------|
| Email                    | Logged-in session                  |
| Name                     | User profile                       |
| Time zone                | `Intl.DateTimeFormat().resolvedOptions().timeZone` |
| Country                  | IP geolocation or browser locale   |
| Language                 | `navigator.language`               |
| Currency                 | Country or user preference         |
| Date format              | Locale                             |
| Device type              | User agent / viewport              |

### The Rule

For every form field, ask: "Do we already know this?" If yes, pre-fill
it. If the user needs to change it, let them -- but don't make them
re-enter it. The best form field is the one the user never has to touch.
