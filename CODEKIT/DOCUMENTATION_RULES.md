# Documentation Rules

## Golden Rule

**Code changes and documentation changes are part of the same task.**

A feature or meaningful fix is not finished until the relevant project memory is updated. Do not leave documentation maintenance for later.

Required cycle: READ -> UNDERSTAND -> CHANGE -> TEST -> DOCUMENT -> REPORT.

## Before Starting Work

Read at minimum:

1. `PROJECT_MEMORY.md`
2. `AGENTS.md`
3. Relevant sections of `DEVLOG.md`
4. `LANGUAGE.md`

Then inspect the actual code related to the task. Documentation provides orientation; code remains the source of truth. Preserve existing useful notes and user changes.

## After Every Meaningful Code Change

### 1. Update DEVLOG.md

Append a dated account of meaningful additions, changes, fixes, removals, decisions, and newly discovered problems. Explain what changed and why, affected files when useful, verification, important side effects, and unfinished work. Tiny formatting edits do not need separate history entries.

Use explicit `YYYY-MM-DD` headings and relevant sections such as Added, Changed, Fixed, Removed, Bugs Found, Decisions, and Notes. Keep chronological order, oldest first. Add a new dated section at the end; same-day changes may be appended within the current day's entry. Never erase important bug history after a fix.

For a meaningful bug, record **Bug**, **Cause**, **Fix**, and **Status**. Mark a cause or fix unknown when investigation has not established it. For important decisions, record **Decision**, **Reason**, and **Impact**; do not invent reasons for older choices.

### 2. Update PROJECT_MEMORY.md

Refresh the date, focus, recent changes, unresolved bugs, next steps, relevant locations, architecture summary, and risks. Keep approximately the latest 5-10 meaningful changes once that much history exists. Remove stale current-state information; older history belongs in `DEVLOG.md`.

Next steps must come from explicit direction, actual TODOs, unfinished work, or observed prerequisites. Label suggestions and do not turn them into an approved roadmap.

### 3. Check AGENTS.md

Update technical facts when changes affect architecture, technology, dependencies, directories, APIs, data models, authentication, state, important flows, configuration, commands, deployment, tests, or constraints. Keep handoff notes current. Record versions only when confirmed and distinguish a declared version range from an exact installed or locked version.

### 4. Check README.md

Update changes to user-facing features, installation, setup, purpose, workflow, status, and limitations. Keep explanations accessible to a non-technical reader. Separate available features from plans.

### 5. Check MARKET.md

Review it when a change affects something users would care about. Explain real benefits supported by implementation. Internal refactors usually do not require new marketing copy. Never present unfinished work as available or invent achievements, users, benchmarks, comparisons, or testimonials.

### 6. Check LANGUAGE.md

Change it only when communication or teaching preferences change. It should normally be stable.

### 7. Verify and Report

Check documentation against the changed code and configuration. Confirm paths and commands, resolve contradictions, check links, and remove obsolete or duplicated information. Update documentation-health statuses in `PROJECT_MEMORY.md`; mark unfinished coverage as needing update rather than calling it current.

Run checks appropriate to the change and report their actual outcome. If code, tests, services, or credentials are unavailable, state the verification limit. Do not imply that documentation checks prove application behavior.

## When Documentation Disagrees With Code

Investigate before acting. If the code clearly establishes current behavior, follow it and correct the documentation. Record meaningful discrepancies in `DEVLOG.md`. If intended behavior remains unclear, explain the conflict and seek direction when needed; do not silently convert an assumption into a requirement.

## Each File Has One Job

| File | Responsibility |
| --- | --- |
| `LANGUAGE.md` | How to communicate with the owner |
| `AGENTS.md` | Deep technical facts and agent orientation |
| `README.md` | Human-friendly project explanation |
| `MARKET.md` | Product story and positioning |
| `DEVLOG.md` | Historical timeline |
| `PROJECT_MEMORY.md` | Concise current briefing |
| `DOCUMENTATION_RULES.md` | Rules for maintaining the kit |

Small overlap is useful. Link to detailed sections rather than copying them into every document.

## Evidence and Quality

- Be specific, current, useful, and easy to scan. Prefer concrete behavior to generic praise.
- Use **Unknown** or **Not confirmed yet** for missing facts. Prefix an inference with **Likely:**.
- Do not invent architecture, history, old bugs, decision rationale, versions, deployments, integrations, business claims, or future plans.
- Anchor important technical statements to real files, configuration, test results, or available history.
- Use explicit dates such as `2026-09-12`; avoid undated claims such as "yesterday" or "recently."
- Preserve historical entries. Add a dated correction when evidence changes an earlier understanding.
- Never judge implementation from filenames alone. Open the important files and trace the relevant behavior.

## Secrets and Security

Never place passwords, private keys, API secrets, access tokens, session tokens, or private credentials in these files. Environment-variable names and purposes are allowed; secret values are not. Review snippets and configuration examples before documenting them.
