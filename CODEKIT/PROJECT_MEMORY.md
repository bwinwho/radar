# PROJECT MEMORY

**Project:** RADAR (confirmed from `index.html` page title and heading)
**Last Updated:** 2026-09-13
**Current Stage:** Working single-file P2P file-transfer web app; deployed (owner-stated) to Cloudflare Pages
**Current Focus:** Just reworked the UI/UX (responsive layout, settings/custom callsign, File/Media/Paste, connect retry); CODEKIT kept in sync in the same task

## What This Project Is

RADAR is a single-page, client-only web app that lets two browsers exchange a file directly over a WebRTC peer-to-peer connection, using [PeerJS](https://peerjs.com/) for connection signaling. Each visitor gets a callsign — random by default (e.g. `NEON-42`), or a custom 3-4 word one set in Settings — that now persists across reloads. Typing a peer's callsign and clicking "Establish Link" opens a direct P2P link (retrying for up to 60 seconds if the target isn't online yet, with a live countdown and a Cancel option), after which either side can send a file, a media item, or their clipboard contents, with a live speed/progress readout. The whole app is one file, `index.html`.

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

Just finished a UI/UX rework requested by the owner (see Recently Changed). Next development task on the app itself has not been specified beyond that.

## Recently Changed

- **2026-09-13:** UI/UX rework: responsive `100dvh`-safe layout for desktop and mobile; a Settings panel to set a persistent custom callsign (exactly 3-4 words); own callsign now persists across reloads (`localStorage['radar_my_id']`); replaced the single send button with File / Media / Paste (clipboard) actions; connecting now retries for up to 60 seconds with a live countdown before auto-cancelling if the target is offline, plus a manual Cancel option. Found and fixed two layout bugs along the way (a flex/word-break bug that stacked the callsign display one letter per line, and a `justify-content: center` overflow bug that made the header unreachable) — see [DEVLOG.md](DEVLOG.md).
- **2026-09-13:** Rewrote all seven CODEKIT files to document the actual RADAR app (`index.html`) instead of the earlier "empty workspace" baseline.
- **2026-09-12:** Inspected the empty workspace and confirmed local Git history was unavailable (this was true of the CODEKIT folder in isolation at that time, before it was joined with the RADAR app code in this repository).
- **2026-09-12:** Created all seven documentation files, including communication preferences and same-task documentation maintenance rules.

## Known Bugs

None currently open. Two layout bugs introduced during the 2026-09-13 UI rework were found and fixed in the same session (see [DEVLOG.md](DEVLOG.md) "Bugs Found"). One code-review observation, not a confirmed bug: the receiver buffers the entire incoming file in memory before saving it, which could be a problem for very large transfers (see [AGENTS.md](AGENTS.md#constraints-and-fragile-areas)).

## Known Risks / Fragile Areas

- Connectivity depends on PeerJS's default public signaling server and on plain STUN (no configured TURN server), so some network setups may fail to connect P2P. Not tested against the real service from this workspace (see DEVLOG "Notes" for why).
- Two files named `NothingHere` (repo root and inside `CODEKIT/`) have unexplained purpose.
- Deployment details (Cloudflare Pages build/publish settings) are owner-stated, not confirmed by config files in the repo.
- The connect/retry/timeout logic and Paste-from-clipboard were verified against a stub `Peer`/UI state machine in headless Chromium, not against real PeerJS signaling or a real clipboard permission prompt — a real two-device test against the deployed site is recommended.

## Next Logical Steps

1. Real-device verification of the new connect-retry/timeout flow and all three send actions (especially clipboard permission prompts on mobile) against the deployed site.
2. Confirm/document the Cloudflare Pages deployment setup for `radatit.pages.dev`.
3. Decide what to do with the two `NothingHere` placeholder files.
4. Beyond that, further RADAR feature work awaits explicit direction from the owner.

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
