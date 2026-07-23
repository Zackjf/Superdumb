---
name: generous-inputs
description: "Apply when building any input that accepts user-typed data — forms, search, filters, URLs, phone numbers, names, dates, or any free-text field. The system should accept any reasonable human input and parse it, rather than demanding a specific machine format. Postel's Law: be liberal in what you accept, conservative in what you output. Use whenever building forms, search, data entry, or any field where the user types something."
---

# Generous Inputs

Postel's Law: "Be liberal in what you accept, and conservative in what you send."

When a user types their phone number as `(555) 123-4567` and your system wants `5551234567`, your system should do the conversion — not reject the input and demand the "correct" format. The user typed a valid phone number. Your job is to understand it, not to teach them your preferred format.

## Accept Every Reasonable Format

### Phone numbers
Accept all of these — they're all the same number:
```
(555) 123-4567
555-123-4567
555.123.4567
5551234567
+1 555 123 4567
+1 (555) 123-4567
1-555-123-4567
```
Parse them all. Store a normalized version. Display a formatted version. Never reject a valid phone number because of formatting.

### Names
Accept all of these — they're all real names:
```
José García            ← accented characters
O'Brien                ← apostrophes
Smith-Jones            ← hyphens
van der Berg           ← spaces and lowercase particles
McDonald               ← mid-word capitals
Li                     ← two characters
Björk                  ← non-English characters
Nguyễn Thị Minh Khai   ← Vietnamese with diacritics
سارة                   ← Arabic
田中太郎               ← Japanese
```
Never reject a name because it's "too short," has "invalid characters," or "contains numbers" (some cultures include numbers in names). The only validation for a name field: it's not empty (if required).

### Email
Accept all valid emails:
```
user@example.com          ← standard
user+tag@example.com      ← plus addressing (common for filtering)
user@subdomain.example.com ← subdomains
user@example.co.uk        ← multi-part TLDs
very-long-email-address@very-long-domain-name.example.com ← long but valid
```
Validate format loosely: contains `@`, has text before and after it, domain has a dot. Don't get clever with regex that rejects valid but unusual addresses.

If the domain looks like a common typo, suggest — don't reject: "Did you mean @gmail.com instead of @gmal.com?"

### URLs
Accept with or without protocol:
```
example.com
www.example.com
https://example.com
https://www.example.com/path?query=value
http://example.com    ← accept, but upgrade to https internally if appropriate
```
If they type `example.com`, prepend `https://` yourself. Don't error with "Please enter a valid URL including the protocol."

### Dates (when text input is used)
If you're using a text fallback (date picker should be preferred):
```
7/20/26
07/20/2026
July 20, 2026
Jul 20, 2026
20 July 2026        ← European order
2026-07-20          ← ISO format
20/07/2026          ← DD/MM/YYYY
```
Parse what you can. If ambiguous (is `01/02/2026` January 2nd or February 1st?), use the user's locale to decide, or ask for clarification — don't just pick one and fail silently.

### Currency
```
$49.99
49.99
$49
49,99        ← European decimal separator
49.990       ← trailing zero, treat as $49.99
USD 49.99
```
Parse the number. Apply the correct currency from context (the page, the user's locale, or a currency selector).

### Search queries
- Ignore leading/trailing whitespace
- Handle multiple spaces between words
- Don't require quotes for exact phrases — try both interpretations
- Handle common misspellings with "Did you mean?"
- Don't return empty results for small typos — fuzzy match

## Display Consistently

Accept messy input, but display clean output:

| User types | You store | You display |
|---|---|---|
| `(555) 123-4567` | `+15551234567` | `(555) 123-4567` |
| `joe@GMAIL.COM` | `joe@gmail.com` | `joe@gmail.com` |
| `www.Example.com` | `https://www.example.com` | `example.com` |
| `$49.990` | `4999` (cents) | `$49.99` |

The pattern: normalize for storage, format for display, never show the raw storage format.

## Validation Messages That Help

When input truly can't be parsed, tell the user what's wrong and what you expected — without being rigid about format:

**Good:**
- "That phone number looks too short — try including the area code"
- "We need a valid email so we can send your receipt"
- "Did you mean @gmail.com?" (for `@gmal.com`)
- "That doesn't look like a URL — try something like example.com"

**Bad:**
- "Invalid format. Expected: +1XXXXXXXXXX"
- "Error: Phone number must match pattern ^\\+1\\d{10}$"
- "Invalid email address" (with no indication of what's wrong)
- "URL must start with https://"

## Anti-patterns

**Rigid format enforcement.** "Phone must be in format (XXX) XXX-XXXX." Why? Parse the digits out of whatever they type. The user's job is to give you their phone number. Your job is to understand it.

**Rejecting valid but unusual input.** Rejecting `O'Brien` because apostrophes are "special characters." Rejecting `Li` because the minimum length is 3. Rejecting `user+tag@gmail.com` because `+` is "invalid." These are all real human inputs. Your validation is wrong, not their data.

**Showing the storage format.** Displaying `+15551234567` to the user when they entered `(555) 123-4567`. Accept their format, store your format, display a human format.

**Error messages that show regex.** "Input must match ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$". The user doesn't know what this means. They just want to type their email.

**Clearing the field on rejection.** The user typed 10 characters and one was wrong. Don't clear the field — highlight the problem and let them fix it.
