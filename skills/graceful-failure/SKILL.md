---
name: graceful-failure
description: "Apply when building ANY feature that can fail — API calls, form submissions, authentication, payments, file uploads, integrations, data loading, or third-party services. Every failure mode needs a human-readable message, a recovery path, and preserved user state. Use whenever writing error handling, catch blocks, error boundaries, 404 pages, timeout handling, or offline states. Claude commonly exposes raw error.message to users, uses alert() for errors, shows blank screens on API failure, and forgets to build error states entirely."
---

# Graceful Failure

Every feature you build will fail. The API will be down. The network will drop. The payment will be declined. The token will expire. The file will be too large. The third-party service will return garbage. The user will land on a page that doesn't exist.

The question isn't whether your app will fail — it's whether, when it fails, the user knows what happened, what they can do about it, and that their work is safe.

Claude's default approach to errors is: `catch (error) { alert(error.message) }` or `<p>{error}</p>`. This exposes raw server errors, stack traces, and technical messages to users. It provides no recovery path. It often loses the user's unsaved work. This skill fixes all of that.

---

## The Error Hierarchy

Not all errors are equal. Handle them differently:

### 1. Validation errors (user made a fixable mistake)
The user entered something wrong — bad email format, missing required field, password too short.

**What to show:** Inline error message directly below the field, explaining what's wrong and how to fix it.
**What NOT to show:** A banner at the top, a toast that disappears, a generic "Form has errors."
**Recovery:** The user fixes the field and resubmits. Everything else they entered is preserved.
**Never:** Clear the form. Scroll away from the error. Show the error somewhere other than the field.

```
Good: "That email doesn't look right — check for typos"
Bad:  "Validation error: field 'email' failed format check"
Bad:  "Error 422"
Bad:  alert("Invalid input")
```

### 2. Action errors (something the user did failed on the server)
The user submitted a valid form, but the server rejected it — duplicate email, payment declined, quota exceeded, permissions denied.

**What to show:** A clear message explaining what happened and what to do next. Show it inline on the same page, near the action they took.
**Recovery:** Depends on the error — "Try a different email", "Check your card details", "Upgrade your plan", "Ask an admin for access."
**Never:** Show raw API responses. Navigate away from the page. Lose their form input.

```
Good: "That email is already registered. Try signing in instead, or use a different email."
Good: "Your card was declined. Please check your card details or try a different card."
Bad:  "Error: UNIQUE_CONSTRAINT_VIOLATION on field 'email'"
Bad:  alert(error.message)
Bad:  "Something went wrong" (with no guidance)
```

### 3. System errors (the infrastructure is broken)
Server 500, database down, network timeout, third-party service unreachable. The user did nothing wrong.

**What to show:** A friendly message acknowledging the problem. The user's work status (saved or not). A way to retry or get help.
**Recovery:** "Try again in a moment" + retry button, or "Contact support" with a link.
**Never:** Show stack traces, raw error.message from the server, HTTP status codes, or database errors. Never show "Error: fetch failed" or "TypeError: Cannot read properties of undefined."

```
Good: "Something went wrong on our end. Your changes were saved up to [X]. Try again in a moment, or contact support if this keeps happening."
Good: "We couldn't connect to the server. Check your internet connection and try again." [Retry button]
Bad:  "Error: ECONNREFUSED 127.0.0.1:5432"
Bad:  "Internal Server Error"
Bad:  {error.message}  ← NEVER render raw error.message in production
```

### 4. Not found errors (404)
The user followed a dead link, typed a wrong URL, or the thing they're looking for was deleted.

**What to show:** A friendly page that stays within your app's layout (don't break the navigation). Suggest what they might have been looking for. Link back to a useful starting point.
**Recovery:** Search, link to home, link to the most likely section.
**Never:** Show the default framework 404. Drop them out of the app shell (no sidebar, no nav). Show a blank page.

```
Good: "We couldn't find that page. It may have been moved or deleted. Try searching, or go back to [Dashboard]."
Bad:  "404 Not Found"
Bad:  Next.js default 404 page (breaks app layout)
Bad:  Blank screen
```

### 5. Permission/auth errors (403, expired session)
The user's session expired, they don't have access, or they're trying to reach something they shouldn't.

**What to show:** Clear explanation of why they can't access this. A path to fix it.
**Recovery:** "Sign in again" for expired sessions. "Ask an admin for access" for permission issues. Don't just say "Forbidden."

```
Good: "Your session has expired. Sign in again to continue." [Sign in button — redirects back after auth]
Good: "You don't have access to this page. Contact your admin to request access."
Bad:  "403 Forbidden"
Bad:  "Unauthorized"
Bad:  Redirect to login with no explanation
```

### 6. Partial failures (some things worked, some didn't)
A bulk operation where 47 of 50 items succeeded. An import where 3 rows had errors. A multi-step process where step 2 failed.

**What to show:** What succeeded AND what failed. Don't report only the failure. Don't say "Failed" when 94% succeeded.
**Recovery:** Fix the failures, retry just the failed items.

```
Good: "47 of 50 items imported successfully. 3 items had errors:" [show the specific errors with the specific items]
Bad:  "Import failed" (when 47 items actually worked)
Bad:  "Error occurred during import" (which items? what error?)
```

---

## The Rules

### Rule 1: Never render raw error.message in production

```typescript
// WRONG — raw server error shown to user
catch (error) {
  setError(error.message)
}

// WRONG — alert with raw error
catch (error) {
  alert(error.message)
}

// RIGHT — human message with raw error logged
catch (error) {
  console.error('API call failed:', error)
  setError("Something went wrong. Please try again.")
}

// BETTER — map known errors to human messages
catch (error) {
  console.error('Save failed:', error)
  const message = errorToHumanMessage(error)
  toast({ title: message, tone: "error" })
}
```

Server errors can contain: stack traces, file paths, database queries, internal IP addresses, library names, environment variables. None of these should reach the user. Log them for debugging. Show the user a human message.

### Rule 2: Never use alert() or confirm() for errors

Browser `alert()` is:
- Unstyled and jarring
- Impossible to customize
- Blocking (freezes the page)
- Inconsistent across browsers
- Inaccessible (no ARIA, no keyboard trap management)

Use in-app error states: toast notifications, inline error messages, error banners, or error dialogs that match your design system.

### Rule 3: Every error needs a recovery path

An error message without a next step is a dead end. Every error must tell the user what to do:

| Error type | Recovery path |
|---|---|
| Network error | "Check your connection and try again" [Retry button] |
| Server error | "Try again in a moment" [Retry button] or "Contact support" [link] |
| Auth expired | "Sign in again" [Sign in button that redirects back] |
| Permission denied | "Contact your admin for access" |
| Payment declined | "Check your card details or try a different card" [link to billing] |
| Quota exceeded | "Upgrade your plan to continue" [Upgrade button] |
| Not found | "Go back to [Dashboard]" or "Search for what you need" |
| Token expired | "Request a new link" [Resend button] — not just "Go to login" |
| Rate limited | "Too many attempts. Wait a few minutes and try again." |
| File too large | "Maximum file size is 10 MB. Try compressing the image." |
| Unsupported format | "We accept JPG, PNG, and WebP files." |
| Duplicate entry | "That [email/name] is already in use. Try a different one." |
| Feature not implemented | Don't show it at all. Remove the UI until it works. |

### Rule 4: Preserve user state on error

When an error occurs:
- **Form data must survive.** If the API call fails, the form still has everything the user typed. They fix one thing and resubmit.
- **Navigation state must survive.** If a save fails, the user is still on the same page, not redirected somewhere else.
- **Selection state must survive.** If a bulk action partially fails, the user can see what succeeded and retry what didn't.
- **Scroll position must survive.** Don't scroll to the top on error. Stay where the user was.

### Rule 5: Error states are screens, not afterthoughts

Every screen that loads data needs THREE states designed:
1. **Loading state** — skeleton, spinner, or progressive loading
2. **Loaded state** — the normal view with data
3. **Error state** — what happens when data fails to load

If you only design the loaded state, the loading and error states will be blank screens or raw error dumps. Design all three.

---

## Common Claude Error Handling Mistakes

| What Claude builds | The problem | The fix |
|---|---|---|
| `catch (e) { alert(e.message) }` | Raw error in browser dialog | Toast with human message, log raw error |
| `{error && <p>{error}</p>}` where error is `error.message` | Raw server text shown to user | Map to human message first |
| `catch { return null }` (component returns nothing) | Blank screen with no explanation | Return an error state component |
| No error handling at all (no try/catch) | Unhandled promise rejection → blank screen or crash | Always wrap API calls in try/catch |
| `if (!res.ok) throw new Error(data.error)` → shown to user | API error strings are developer-facing | Map API errors to human messages |
| Error boundary shows `error.message` | Raw JS error shown in production | Generic message in prod, details in dev only |
| Forgot password fails → user sees "Error" with no action | No recovery path | "Request a new link" button |
| Token expired → redirect to login with no explanation | Silent redirect confuses user | Show "Your session expired. Sign in to continue." |
| 404 page breaks app layout (no sidebar, no nav) | User loses navigation context | Create in-app not-found page within the app layout |
| Loading fails → empty component, no error state | User sees blank area, thinks content doesn't exist | Show "Couldn't load [X]. [Retry] or [Contact support]" |
| Partial failure reported as total failure | "Import failed" when 47 of 50 succeeded | Show what worked AND what failed |

---

## Error Message Writing Guide

### Structure: What happened → Why → What to do

```
[What happened]. [Why, briefly]. [What to do next].
```

Examples:
- "Your changes couldn't be saved. The server didn't respond. Try again in a moment."
- "We couldn't load your orders. Check your internet connection and refresh the page."
- "This verification link has expired. Request a new one and we'll send it right away."
- "Your card was declined by your bank. Try a different card or contact your bank."

### Tone

- **Direct, not apologetic.** "We couldn't save your changes" not "We're so sorry, but unfortunately we were unable to process your request at this time."
- **Honest, not vague.** "The server didn't respond" not "An unexpected error occurred." Tell them what actually happened in plain words.
- **Helpful, not blaming.** "Check your internet connection" not "You appear to be offline." Frame it as a suggestion, not an accusation.
- **Brief.** One to two sentences max for the main message. Details in a collapsible section if needed.

### What NOT to write

- "An unexpected error occurred." — Every error is "unexpected" to the user. This says nothing.
- "Something went wrong." — As a standalone message with no next step, this is useless.
- "Please try again later." — When is "later"? A minute? An hour? Tomorrow? Be specific: "Try again in a moment" or "Our team is working on it. Check back in an hour."
- "Contact support." — As the only recovery path for a common error, this is a failure. Most errors should have a self-service recovery path. Support is the last resort, not the first suggestion.
- "Error: [raw technical message]" — Never.

---

## The Unhappy Path Checklist

Before shipping any feature, walk through every failure mode:

1. **What if the API returns 500?** → User sees a human error message with retry option. Their form data is preserved.
2. **What if the network is down?** → User sees "Check your connection" with retry. No data is lost.
3. **What if the user's session expired?** → User sees "Sign in again" and is returned to where they were after re-authentication.
4. **What if the thing they're looking for was deleted?** → 404 page within the app layout with navigation intact.
5. **What if they don't have permission?** → Clear message explaining why and who to ask.
6. **What if the payment fails?** → Specific reason + specific recovery ("Try a different card").
7. **What if a token/link has expired?** → "Request a new one" button, not just "Invalid link."
8. **What if an import/bulk action partially fails?** → Show what succeeded AND what failed.
9. **What if a required third-party service is down?** → Explain which part isn't working and whether they can continue using other features.
10. **What if they hit a rate limit?** → Tell them to wait, and how long. Don't just fail silently.
11. **What if JavaScript fails to load?** → Critical content is visible via SSR. Forms degrade gracefully.
12. **What if the page they're on doesn't exist yet?** → Don't show it in the navigation. No links to unbuilt pages.
