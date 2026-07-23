# Rigid Validators

Input validation that fights the user instead of helping them.

## What It Looks Like

```
Phone: (555) 867-5309
Error: Phone number must match format XXX-XXX-XXXX.
```

```
Name: O'Brien
Error: Name contains invalid characters.
```

```
Website: example.com
Error: URL must begin with http:// or https://
```

```
Password: correct horse battery staple
Error: Password must contain at least one uppercase letter,
one number, and one special character (!@#$%^&*).
```

```
ZIP: 90210-1234
Error: ZIP code must be exactly 5 digits.
```

The user entered perfectly valid information. The validator rejected it
because it doesn't match the developer's assumed format.

## Why It Happens

AI agents write validation with regex patterns that encode one specific
format. They validate the *shape* of the input, not the *meaning*. The
agent writes `^\d{3}-\d{3}-\d{4}$` for phone numbers, which rejects
parentheses, spaces, dots, country codes, and extensions -- all of which
are valid ways humans write phone numbers.

## Why It's Bad

- Users with apostrophes in their names (O'Brien, Al-Rashid) get told
  their name is "invalid." That's hostile.
- Phone number format varies by country and by personal preference.
  Rejecting valid formats tells international users they're unwelcome.
- Showing regex in error messages is incomprehensible to most people.
- Users resort to lying: entering fake data that passes validation
  rather than fighting with their real data.

## What to Do Instead

Normalize input instead of rejecting it. Strip formatting characters
on the backend. Accept liberal input and store a clean version.

### Before

```jsx
const validatePhone = (phone) => {
  if (!/^\d{3}-\d{3}-\d{4}$/.test(phone)) {
    return 'Phone number must match format XXX-XXX-XXXX.';
  }
};
```

### After

```jsx
const normalizePhone = (phone) => {
  const digits = phone.replace(/\D/g, '');
  if (digits.length < 10 || digits.length > 15) {
    return { error: 'Enter a phone number with 10-15 digits.' };
  }
  return { value: digits };
};

// Accepts: (555) 867-5309, 555.867.5309, +1 555 867 5309,
//          5558675309, 555-867-5309 ext 42
```

### Before

```jsx
const validateName = (name) => {
  if (!/^[a-zA-Z\s]+$/.test(name)) {
    return 'Name contains invalid characters.';
  }
};
// Rejects: O'Brien, Jose, Li-Wei, Muller
```

### After

```jsx
const validateName = (name) => {
  const trimmed = name.trim();
  if (trimmed.length < 1) {
    return 'Enter your name.';
  }
  if (trimmed.length > 200) {
    return 'Name is too long.';
  }
  // Accept whatever the user says their name is.
};
```

### Before

```
Error: URL must begin with http:// or https://
```

### After

```jsx
const normalizeUrl = (url) => {
  let normalized = url.trim();
  if (!/^https?:\/\//i.test(normalized)) {
    normalized = 'https://' + normalized;
  }
  return normalized;
};
// User types "example.com", system stores "https://example.com"
```

### The Validation Principles

1. **Normalize, don't reject.** Strip characters, add prefixes, fix case.
2. **Validate meaning, not format.** A phone number needs enough digits,
   not a specific dash pattern.
3. **Never tell someone their name is invalid.**
4. **Error messages should say what to do, not what went wrong technically.**
   "Enter at least 10 digits" beats "Input failed regex validation."
