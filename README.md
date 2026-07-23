# SuperDumb

Make AI-built websites radically simpler and more human.

SuperDumb is a framework for AI coding agents (Claude Code, Cursor, Copilot, Codex) that forces them to build for real, non-technical humans instead of imaginary PhD-level power users.

---

## The Problem

AI coding agents build technically correct UIs that feel wrong:

- Developer vocabulary everywhere ("entity", "initialize", "payload", "configuration")
- Raw database IDs, status enums, and timestamps shown to users
- Every field is a text input, even for dates, toggles, and media
- 20-field forms with no grouping, no smart defaults, no progressive disclosure
- Navigation organized by database tables, not user tasks
- No error handling, or `alert(error.message)` as the error handling
- Buttons that say "Submit", pages with no feedback, forms that clear on error
- `dangerouslySetInnerHTML` with no sanitization
- Links to pages that don't exist, search bars that don't work

SuperDumb fixes all of this. It's battle-tested against 4 real codebases (~520 files, 280+ issues found and catalogued).

---

## How It Works

**27 skills** organized into 4 phases:

### Before Building (3 Gate Skills)
Before writing any UI code, the agent defines who the user is, what they're trying to do, and how competitors solve it. No gates, no building.

### During Building (21 Build Skills)
Skills applied while coding — speak human, right input types, smart defaults, graceful error handling, cognitive load management, accessibility, and more. The agent picks the relevant ones based on what it's building.

### After Building (1 Review Skill)
Walk every screen as a first-timer, a rusher, a non-technical person, and a phone user. Find where they'd get stuck.

### Special Modes (2 Skills + 1 Redesign Skill)
- **Spec-to-UX**: Translate a tech spec into screen-by-screen wireframes with human copy
- **Audit**: Systematic review of an existing UI with a phased implementation plan
- **Simplify**: Reimagine an overcomplicated page with half the fields

---

## 14 Hard Rules

These are non-negotiable. The agent applies them to every piece of UI:

1. **No developer artifacts in the UI.** No IDs, hashes, UUIDs, raw timestamps, status codes, enum values, or raw `error.message`.
2. **Every button says what it does.** "Save changes", "Send message". Never "Submit", "OK", "Click here".
3. **One primary action per screen.** Two equally-weighted CTAs = zero.
4. **The user's word wins.** "Orders" not "transactions", "sign in" not "authenticate".
5. **Don't ask what you already know.** Infer it, pre-fill it, or skip it.
6. **No paragraph text in UI.** Rewrite as bullets, headings, or cut it.
7. **Every action gets feedback.** Click → loading state → success/error. Always.
8. **Forms never clear on error.** Show what's wrong. Preserve everything else.
9. **Never render raw error.message in production.** Log it. Show a human message with a recovery path.
10. **Never use alert() or confirm().** Use in-app toasts, banners, and dialogs.
11. **Never link to pages that don't exist.** Remove until implemented.
12. **Never show non-functional UI.** No fake search bars, no buttons without handlers, no placeholder data.
13. **Images are file uploads, not URL text fields.** Users have files, not CDN URLs.
14. **No raw HTML tags or Markdown syntax visible to users.** Sanitize all rendered content.

---

## Installation

### Option 1: Clone into your project

```bash
git clone https://github.com/Zackjf/Superdumb.git .superdumb
```

Or as a submodule:

```bash
git submodule add https://github.com/Zackjf/Superdumb.git .superdumb
```

### Option 2: Claude Code plugin (when published)

```bash
claude plugin install superdumb
```

### Option 3: Manual

Copy the directory into your project root. The `CLAUDE.md` file activates automatically when Claude Code detects it.

---

## Quick Start

**New project:** Just start building. The CLAUDE.md file tells the agent to run gate skills before any UI work, apply build skills during, and review after. No manual invocation needed.

**Existing project:** Ask the agent: "Audit this project's UX" or "Review the UI of this site." The agent runs the audit skill, walks every screen, and produces a prioritized fix table with a phased implementation plan.

**Simplify a page:** Ask: "This settings page is too complex, simplify it." The agent runs the simplify skill and produces a before/after redesign.

**Spec to UX:** Give the agent a product spec and ask: "Design the UX for this." The agent produces screen-by-screen wireframes with copy, empty states, error states, and mobile behavior.

---

## What's Inside

```
superdumb/
├── CLAUDE.md                          # The engine — auto-loaded by Claude Code
├── .claude-plugin/plugin.json         # Plugin manifest
├── skills/                            # 27 skills
│   ├── know-your-user/                # Gate: who is this person?
│   ├── define-the-task/               # Gate: what are they trying to do?
│   ├── study-the-landscape/           # Gate: how do competitors do it?
│   ├── speak-human/                   # No jargon, domain translation tables
│   ├── human-friendly-inputs/         # Right inputs, no dev artifacts, no raw HTML
│   ├── consistency/                   # Vocabulary registry, same patterns everywhere
│   ├── minimum-screens/              # Fewest screens, core functions 1-2 clicks from home
│   ├── scannable-not-readable/        # Headings + bullets, no paragraphs
│   ├── manage-cognitive-load/         # 3-4 choices max, nav max 8-10, group forms
│   ├── use-familiar-patterns/         # Solved problems use solved UI
│   ├── smart-defaults/                # Infer, pre-fill, default from org settings
│   ├── generous-inputs/               # Accept any format, parse it yourself
│   ├── prevent-errors/                # Constrain inputs, validate inline, no dead UI
│   ├── copy-and-microcopy/            # Empty states, loading, errors, confirmations
│   ├── action-feedback/               # Every action responds visibly
│   ├── trust-and-reassurance/         # Pricing, reversibility, trust near conversion
│   ├── graceful-failure/              # Every failure: human message + recovery path
│   ├── show-where-i-am/              # Progress, breadcrumbs, active nav
│   ├── first-time-vs-returning/       # Orient new, speed up returning, setup guides
│   ├── user-control-and-freedom/      # Undo, back, escape hatches
│   ├── peak-and-finish-strong/        # Great endings, one moment of delight
│   ├── recognition-over-recall/       # Show context, don't make users remember
│   ├── accessible-by-default/         # 44px targets, contrast, keyboard, one-handed
│   ├── simplify-the-page/            # Reimagine with half the fields
│   ├── outsider-review/              # Walk as first-timer, rusher, non-technical, phone
│   ├── spec-to-ux/                   # Tech spec → wireframes with human copy
│   └── audit-existing-ui/            # Systematic audit → phased implementation plan
├── anti-patterns/                     # 12 common mistakes with examples
│   ├── system-out-thinking.md         # Pages built around data models
│   ├── wall-of-options.md             # 15 settings, no grouping
│   ├── developer-vocabulary.md        # "Authenticate", "instance", "query"
│   ├── paragraph-ui.md               # Prose where bullets belong
│   ├── no-feedback-actions.md         # Click → nothing happens
│   ├── clever-over-familiar.md        # Novel UI for solved problems
│   ├── asking-what-you-know.md        # Forms requesting inferable data
│   ├── one-way-doors.md              # No undo, no back, no escape
│   ├── amnesia-screens.md            # Screens that forget context
│   ├── rigid-validators.md           # Rejecting valid input over formatting
│   ├── buried-primary-input.md        # System's key input hidden 3+ clicks deep
│   └── raw-content-rendering.md       # Visible HTML tags, unsanitized innerHTML
├── best-practices/                    # Reference material
│   ├── copy-guide.md                  # Tone, voice, word substitutions
│   ├── ui-patterns.md                 # 20 solved patterns with do/don't
│   ├── microcopy-examples.md          # Before/after for every context
│   ├── hierarchy-rules.md            # Primary action rules, squint test
│   └── consistency-checklist.md       # Vocabulary registry template, audits
├── README.md
└── LICENSE                            # MIT
```

---

## Battle-Tested

SuperDumb was developed by auditing 4 real production codebases:

| Project | Type | Files | Issues Found |
|---|---|---|---|
| Content engine (SaaS) | Internal tool | ~100 | 94 |
| Travel/trade site + CMS | Public site + admin | ~300 | 60+ |
| 2FA routing platform | Security SaaS | ~60 | 80 |
| SEO experimentation tool | Analytics SaaS | ~60 | 44 |

**280+ real issues** were catalogued and used to refine every skill. The patterns that appeared in every project became the 14 hard rules.

### Patterns that appear in every AI-built codebase:
1. Raw enums shown to users (DRAFT, RUNNING, APPROVED displayed as-is)
2. Domain jargon untranslated (TOTP, MFA, SSO, p-value, slug, cron)
3. Non-functional UI elements (search bars with no handler, links to unbuilt pages)
4. Missing trust signals (no testimonials, unsubstantiated stats, placeholder social links)
5. Components built but never wired (UnsavedChangesBanner exists, used nowhere)
6. `alert()`/`confirm()` instead of in-app dialogs
7. `dangerouslySetInnerHTML` without sanitization
8. Forms with 15-20 fields and no visual grouping
9. Post-signup redirect to empty dashboard instead of setup guide
10. Product concepts never explained to first-time users

---

## Compatibility

SuperDumb is designed for **Claude Code** but works with any agent that reads project-level instruction files:

- **Cursor** — place in `.cursor/rules/` or reference in project rules
- **GitHub Copilot** — reference in `.github/copilot-instructions.md`
- **Codex / OpenAI** — include in the agent's context
- **Any AI coding agent** that reads Markdown instruction files

---

## License

MIT. See [LICENSE](LICENSE).

---

## Contributing

Open an issue to propose a new skill, report a problem, or suggest an improvement. Each skill follows the skill-creator format: a directory under `skills/` with a `SKILL.md` containing instructions, examples, anti-patterns, and a checklist.

Built by [Zack](https://github.com/Zackjf). Refined by auditing real codebases. Powered by the belief that AI should build for humans, not for developers.
