# Agent Guide

## Required Workflow

READ -> UNDERSTAND -> CHANGE -> TEST -> DOCUMENT -> REPORT.

Before starting work, read [PROJECT_MEMORY.md](PROJECT_MEMORY.md), this file, the relevant entries in [DEVLOG.md](DEVLOG.md), and [LANGUAGE.md](LANGUAGE.md). Follow [DOCUMENTATION_RULES.md](DOCUMENTATION_RULES.md). Inspect the actual code related to the task before editing it. Code and configuration are the source of truth; this guide is an orientation aid.

Never invent facts, history, design rationale, commands, or roadmap commitments. Mark missing evidence **Unknown** or **Not confirmed yet**. Label inferences **Likely:**. Never put credentials or secret values in documentation.

## Project Identity

- Working label: **CodeKit**, derived only from the root folder name. Official product name: **Unknown**.
- Project root: the folder containing this file.
- Project type and main purpose: **Unknown**.
- Observed stage on **2026-09-12**: documentation-only workspace. No application implementation was present during the baseline inspection.
- Product maturity, previous development elsewhere, and release status: **Unknown**.

## Confirmed Baseline

Before this kit was created, a recursive listing including hidden entries found no files or subdirectories in the project root. No source, configuration, existing documentation, assets, scripts, tests, TODOs, or FIXME notes were available to inspect. Git status and log commands reported that this folder was not a Git repository. This describes the local workspace only; it does not establish whether a project exists elsewhere.

## Technology Stack

| Area | Evidence / status |
| --- | --- |
| Application languages, frameworks, libraries | **Unknown**; no source or dependency manifests |
| Runtime and package manager | **Unknown**; no runtime configuration or lockfiles |
| Database, authentication, storage | **Unknown**; no implementation or configuration |
| Hosting and external APIs | **Unknown**; no deployment or integration files |
| Build, lint, packaging, and testing tools | **Unknown**; no scripts or tool configuration |
| Documentation format | Markdown (`.md`) |
| Dependency and runtime versions | **Unknown** |

Do not select a stack or infer installed project dependencies from the tools available on an agent's machine.

## Architecture and Entry Points

**Not confirmed yet.** No frontend, backend, application entry, HTML entry, server entry, root component, router, state manager, database initialization, or authentication initialization exists in the inspected workspace.

There is no source-backed architecture or execution flow to describe. Once code is added, trace startup, user actions, state updates, network requests, persistence, and error handling through real files before documenting them.

## Repository Map

The current workspace contains this seven-file documentation kit:

| File | Responsibility |
| --- | --- |
| `LANGUAGE.md` | Communication and teaching preferences |
| `AGENTS.md` | Technical orientation and instructions for agents |
| `README.md` | Human-friendly project explanation |
| `MARKET.md` | Evidence-based product story |
| `DEVLOG.md` | Append-only history, findings, and decisions |
| `PROJECT_MEMORY.md` | Concise current briefing |
| `DOCUMENTATION_RULES.md` | Maintenance and verification rules |

## Major Modules and Data Model

No application modules, interfaces, schemas, tables, collections, local storage keys, or IndexedDB stores were found. Their responsibilities, dependencies, inputs, outputs, and interactions are **Unknown**.

## Important Flows

Startup, login, navigation, data loading, saving, synchronization, state restoration, uploads, payments, and search are **Not confirmed yet**. No implementation supports claims that any of these features are available.

## External Services and Configuration

No service integrations, environment files, or required environment-variable names were found. Required configuration is **Unknown**. When configuration becomes available, document variable names and purpose only, never secret values.

## Running and Deploying

There are no confirmed installation, development, build, test, lint, package, or deployment commands. No application can currently be run from this folder. Do not invent commands such as `npm install` or a deployment target without a matching manifest or configuration.

No Git repository was initialized as part of the documentation task. Local version history is unavailable; no remote or branch information could be confirmed.

## Conventions and Decisions

- Existing application coding conventions: **Unknown**, because no source was available.
- New documentation uses Markdown, relative links between kit files, explicit `YYYY-MM-DD` dates, and evidence-qualified statements.
- The owner requested a permanent seven-file memory kit. Meaningful code work must include the relevant documentation updates in the same task.
- Each document has a distinct audience and responsibility; avoid copying entire technical sections into the README or memory briefing.
- No application architecture or technology decision has been made in this workspace.

## Constraints and Fragile Areas

- Treat the current folder as the project root unless the owner changes that direction.
- The initial task authorized documentation, not application scaffolding or code changes.
- Do not treat this empty baseline as proof of missing features or bugs in a project that might exist elsewhere.
- Preserve useful documentation and user changes when updating this kit.
- When implementation arrives, replace unknowns with evidence and revisit all technical and product claims.

## Known Problems and Testing

Confirmed application bugs: none identified; there was no application to inspect. This is not evidence that an application is bug-free.

No automated tests or test configuration were found. Application behavior, security, performance, and regression risks cannot yet be assessed. The current verification scope is documentation: file presence, link targets, consistency, and claims checked against the observed workspace. Add actual test commands and manual regression requirements when implementation exists.

## Agent Handoff

- Current work: the initial documentation baseline is complete as of **2026-09-12**.
- Completed: inspected the empty root and Git availability; created the seven-file kit without application changes.
- Next logical work: establish whether application files need to be brought into this folder or whether the owner intends a new project. Product scope is **Unknown**.
- Caution: do not mistake the folder label for a confirmed brand, or the absence of local code for known product history.
