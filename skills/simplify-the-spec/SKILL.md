---
name: simplify-the-spec
description: "Use this when someone hands you a spec that's overcomplicated, over-specified, or full of implementation details disguised as requirements. Non-technical stakeholders often spec WHAT THEY BUILT LAST TIME instead of WHAT THEY NEED. This skill strips a spec down to its core goals and produces the simplest system that achieves them. Use whenever a spec feels too long, has too many modules, prescribes file paths or cron schedules, or mixes requirements with implementation."
---

# Simplify the Spec

When a non-technical person writes a spec, they describe what they built last time — not what they need. They spec cron schedules instead of "runs weekly." They spec file naming conventions instead of "images are findable by date." They hardcode Slack channel IDs instead of "notifies the design team." They split one system into 8 modules because that's how it was built, not because it needs to be 8 things.

Your job: find the actual goals buried in the implementation details, and produce the simplest system that achieves them.

---

## The Process

### Step 1: Extract the goals

Read the entire spec and answer in plain sentences:

1. **What does this system DO for the people who use it?** Not what modules it has — what value does it create? ("Generates 4 content pieces per week and delivers them to the right team members")
2. **Who are the humans involved and what does each person need?** ("Jason needs his video scripts Friday afternoon. The design team needs image briefs.")
3. **What triggers the system to do something?** ("Every Friday" or "When content is rejected")
4. **What are the actual outputs?** ("11 content formats per piece, delivered via Notion and Slack")

Write these as 3-5 plain sentences. If you can't summarize the spec in 5 sentences, you don't understand it yet.

### Step 2: Identify what's a requirement vs. what's implementation

Go through the spec line by line and categorize:

**Requirements** (WHAT the system must do):
- "Generate 4 content pieces per week"
- "Each piece produces 11 formats"
- "Jason and George alternate voices"
- "Rejected content triggers a rule improvement"
- "Weekly trend scanning feeds into generation"

**Implementation details** (HOW someone built it last time):
- Cron schedules (`07:00, 09:00, 11:00, 13:00 UTC`)
- File paths (`hooks_staging/`, `content_drafts/YYYY-MM-DD_...`)
- JSON state files (`rotation_state.json`, `feedback_state.json`)
- Naming conventions (`YYYY-MM-DD_POST-N_[PLATFORM]_[Article-Title]_[hook-slug].jpg`)
- Specific API IDs (`C0BCA7M0RFT`, `U3LBDENQ6`)
- Module boundaries (`Module 3 — Friday Hooks Batcher`)

**Configuration** (things that should be settings, not spec):
- Slack channel IDs and user IDs
- Notion database IDs
- API keys and endpoints
- Schedule times
- File storage locations

**The rule: requirements go in the spec. Implementation details go in the code. Configuration goes in settings.**

### Step 3: Merge modules that are really one thing

Look for modules that do the same type of work at different times or for different people. These are usually one system with routing, not separate modules.

**Common patterns:**

**"Deliver to Person A on Friday, Person B on Monday"** — that's one delivery system with a routing table, not two modules. The routing table says who gets what, when. Adding a new person or changing a schedule is a config change.

**"Process Type A, then separately process Type B"** — if the processing is the same but the input/output differs, that's one process with parameters.

**"Generate, then stage, then batch, then archive"** — if these always happen in sequence, that's one pipeline, not four modules. The staging/archiving is implementation detail.

### Step 4: Replace rigid mechanisms with flexible ones

| Rigid (from spec) | Flexible (simplified) |
|---|---|
| 74-entry fixed rotation, wraps at index 73 | Topic queue with drag-to-reorder, skip, pin |
| Voice alternates by odd/even index | Voice assigned per topic in the queue |
| Auto-apply rule changes, no review | Propose changes in Slack, human approves |
| Hardcoded schedule times | Configurable schedule in settings |
| Fixed file naming convention | Auto-generated, searchable by date/post/platform |
| Module per delivery recipient | One delivery system with a routing table |

The question for each mechanism: **"What if they want to change this?"**

- "What if they want to skip a topic?" → rigid rotation breaks, queue handles it
- "What if they want to add a team member?" → separate module needs new code, routing table needs a new row
- "What if they want to change the schedule?" → hardcoded cron needs a deploy, settings page needs a click
- "What if a bad rule gets auto-applied?" → auto-apply has no safety net, propose + approve does

### Step 5: Write the simplified spec

Structure:

```
# [System Name]

## What It Does (3-5 sentences)
[Plain-language summary a non-technical person would understand]

## The Jobs (not modules)
[Group by PURPOSE, not by implementation. Usually 2-4 jobs.]

### Job 1: [Verb phrase]
[What it does, what triggers it, what it produces]

### Job 2: [Verb phrase]
[Same]

## Outputs
[What the system produces — the actual deliverables]

## People & Routing
[Who gets what, when, through which channel]

## Feedback / Learning
[How the system improves over time]

## Configuration (not spec)
[Things that are settings, not requirements — listed so the developer
knows to make them configurable instead of hardcoding them]
```

---

## What to Cut

### Cut implementation details

| In the original spec | Should be | Why |
|---|---|---|
| `content_drafts/YYYY-MM-DD_[pillar]_[subtopic].md` | "Generated content is stored and retrievable by date and topic" | The developer picks the storage format |
| `rotation_state.json` tracking index 0-73 | "A topic queue that auto-advances" | The developer picks the state management approach |
| `07:00, 09:00, 11:00, 13:00 UTC` | "4 runs spread across Friday morning" | Exact times are configuration |
| 8-line image filename convention | "Images are auto-named and findable by date, post, and platform" | The developer picks the naming format |
| `hooks_staging/` → `hooks_archive/YYYY-MM/` | "Image briefs are batched and sent to the design team Friday afternoon" | Staging directories are implementation |

### Cut hardcoded IDs

Slack channel IDs, Notion database IDs, user IDs, API keys — these are environment configuration. The spec says "notifies the content bot channel" and the settings page has a field for which channel that is.

### Cut module boundaries

If the original spec has 8 modules but the core work is 3 jobs, spec 3 jobs. The developer decides how to structure the code. The spec describes behavior, not architecture.

### Cut repeated context

If the spec explains the same thing in multiple modules ("reads the manifest to determine voice assignment" appears in modules 4, 5, and 6), that's a sign those modules should be merged. State the rule once in the simplified spec.

---

## What to Keep

### Keep the actual outputs

If the system produces 11 content formats, list all 11. These are requirements — the developer needs to know exactly what to generate.

### Keep the routing

Who gets what, when, through which channel. This is a requirement, not implementation — but express it as a table, not as 4 separate modules.

### Keep the business rules

Voice alternation, ICP targeting, content rules, feedback triggers — these are domain logic the developer can't infer. Keep them, but express them simply.

### Keep the constraints

"US English post-August 2026", "no British spellings", "AI phrase exclusion list" — these are real requirements that affect output quality.

### Keep the "why" when it's not obvious

"George's scripts are delivered Monday, not Friday, because he reviews on weekends" — the reason matters. Without it, a developer might consolidate to Friday delivery and break the workflow.

---

## The Length Test

| Original spec length | Simplified spec length | Ratio |
|---|---|---|
| Under 50 lines | Probably fine as-is | 1:1 |
| 50-150 lines | Should be 30-80 lines | ~2:1 |
| 150-400 lines | Should be 60-120 lines | ~3:1 |
| 400+ lines | Almost certainly over-specified. Target 80-150 lines. | ~4:1 |

A 400-line spec that becomes 100 lines hasn't lost information — it's lost implementation details, repeated context, and module boundaries that shouldn't be in a spec.

---

## Anti-patterns

**"But that's how we built it last time."** The spec describes the last implementation, not the next one. File paths, state files, and module boundaries from the old system are its implementation, not your requirements. Spec the goals, let the developer pick the architecture.

**"We need 8 modules."** You need 8 modules if each does genuinely different work. If 5 of them are "deliver content to a person via Slack/Notion" with different schedules and recipients, you need 1 module with a routing table.

**"The image filename must be YYYY-MM-DD_POST-N_[PLATFORM]..."** Unless an external system depends on this exact format, this is implementation. The requirement is "images are identifiable by date, post number, and platform." Let the developer pick the format.

**Hardcoding IDs in the spec.** `C0BCA7M0RFT` means nothing to anyone reading this spec in 6 months. Say "the content bot Slack channel" and put the ID in configuration.

**Auto-applying changes without review.** Specs from non-technical people often describe automation without safety nets because the manual process didn't have them either. Add human checkpoints for anything that modifies rules, content, or configuration.

**Specifying the schedule to the minute.** "07:00 UTC" is configuration. "Every Friday morning" is a requirement. "Before the design team starts work" is a constraint that explains the requirement. Spec the constraint, configure the time.
