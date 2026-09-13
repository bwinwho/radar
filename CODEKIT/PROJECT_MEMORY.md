# PROJECT MEMORY

**Project:** RADAR (confirmed from `index.html` page title and heading)
**Last Updated:** 2026-09-13
**Current Stage:** Working single-file P2P file-transfer web app; deployed (owner-stated) to Cloudflare Pages
**Current Focus:** CODEKIT documentation brought back in sync with the actual application code

## What This Project Is

RADAR is a single-page, client-only web app that lets two browsers exchange a file directly over a WebRTC peer-to-peer connection, using [PeerJS](https://peerjs.com/) for connection signaling. Each visitor gets a random callsign (e.g. `NEON-42`); typing a peer's callsign and clicking "Establish Link" opens a direct P2P link, after which either side can send a file with a live speed/progress readout. The whole app is one file, `index.html`.

## Current Architecture

One HTML file (`index.html`) containing inline CSS and JavaScript, plus one CDN dependency (`peerjs@1.5.2`). No backend server, no database, no build step. See [AGENTS.md](AGENTS.md) for the full technical walkthrough.

## Important Locations

- [AGENTS.md](AGENTS.md): technical baseline and agent instructions.
- [DEVLOG.md](DEVLOG.md): dated findings and decisions, beginning 2026-09-12.
- [LANGUAGE.md](LANGUAGE.md): communication and teaching preferences.
- [DOCUMENTATION_RULES.md](DOCUMENTATION_RULES.md): required maintenance workflow.
- [README.md](README.md) and [MARKET.md](MARKET.md): human overview and product-story evidence boundary.
- `../index.html`: the application itself (repo root, one level up from this kit).

## Currently Working On

Getting CODEKIT's documentation to match the real, already-built RADAR app (it previously described an empty workspace from 2026-09-12, before the app code existed in this location). Next development task on the app itself has not been specified by the owner yet.

## Recently Changed

- **2026-09-13:** Rewrote all seven CODEKIT files to document the actual RADAR app (`index.html`) instead of the earlier "empty workspace" baseline. No application code was changed.
- **2026-09-12:** Inspected the empty workspace and confirmed local Git history was unavailable (this was true of the CODEKIT folder in isolation at that time, before it was joined with the RADAR app code in this repository).
- **2026-09-12:** Created all seven documentation files, including communication preferences and same-task documentation maintenance rules.

## Known Bugs

None confirmed through code inspection or testing. One code-review observation, not yet confirmed as a bug: the receiver buffers the entire incoming file in memory before saving it, which could be a problem for very large transfers (see [AGENTS.md](AGENTS.md#constraints-and-fragile-areas)).

## Known Risks / Fragile Areas

- Connectivity depends on PeerJS's default public signaling server and on plain STUN (no configured TURN server), so some network setups may fail to connect P2P. Not tested from this workspace.
- Two files named `NothingHere` (repo root and inside `CODEKIT/`) have unexplained purpose.
- Deployment details (Cloudflare Pages build/publish settings) are owner-stated, not confirmed by config files in the repo.

## Next Logical Steps

1. Confirm/document the Cloudflare Pages deployment setup for `radatit.pages.dev`.
2. Decide what to do with the two `NothingHere` placeholder files.
3. Beyond that, further RADAR feature work awaits explicit direction from the owner.

These are prerequisites identified by inspection, not an approved product roadmap.

## Important Decisions

- Meaningful code changes include relevant documentation updates before completion.
- Code (`index.html`) is the source of truth; label unknowns and inferences explicitly.
- Keep this briefing short and current; preserve older history in `DEVLOG.md`.

## Documentation Health

All statuses refer to the evidence available on **2026-09-13**, after inspecting `index.html` and the repository's Git history.

- LANGUAGE.md: current (unchanged; communication preferences do not depend on app specifics)
- AGENTS.md: current
- README.md: current
- MARKET.md: current
- DEVLOG.md: current
- PROJECT_MEMORY.md: current
- DOCUMENTATION_RULES.md: current (unchanged; process rules, not project-specific facts)
