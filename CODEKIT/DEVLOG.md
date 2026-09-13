# Development Log

Append new dated entries in chronological order, oldest first. Preserve earlier decisions and bug history; add a dated correction or resolution when facts change. No history before the inspection below is confirmed.

# 2026-09-12

## Added

Created the initial seven-file project memory kit at the owner's request: `LANGUAGE.md`, `AGENTS.md`, `README.md`, `MARKET.md`, `DEVLOG.md`, `PROJECT_MEMORY.md`, and `DOCUMENTATION_RULES.md`.

The kit separates communication preferences, technical orientation, human explanation, product storytelling, historical records, current context, and maintenance rules so future sessions can continue from documented evidence.

## Decisions

**Decision:** Keep documentation updates part of each meaningful code task.

**Reason:** The owner explicitly requested persistent project memory that stays synchronized with implementation.

**Impact:** Future agents must read the briefing and relevant history, inspect code, make and verify changes, update affected documents, and report the result before declaring work complete.

**Decision:** Record an empty-workspace baseline without selecting a stack or inventing a product.

**Reason:** Inspection found no implementation or product brief, and the owner instructed that this folder be treated as the root and that code remain unchanged during documentation setup.

**Impact:** Product identity, architecture, commands, capabilities, and roadmap remain explicitly unknown until evidence is available. `CodeKit` is only a folder-derived working label.

## Notes

- Confirmed the working directory was `CodeKit`; a recursive listing including hidden entries found no existing files or subdirectories before creation of this kit.
- No existing documentation required preservation or correction.
- Git status and log queries reported that the folder was not a Git repository. Earlier history, branches, and remotes are **Unknown**.
- No source, manifests, environment configuration, scripts, tests, TODOs, or FIXME notes were available to examine. Application flows and bugs could not be assessed.
- No application code was created or changed, no dependencies were installed, and Git was not initialized.
- Documentation verification is limited to the local workspace baseline, file presence, link targets, and consistency. No application tests were available to run.
- Outstanding prerequisite for development: establish whether application files should be brought into this root or whether the owner intends a new project. This is not a confirmed product roadmap.

# 2026-09-13

## Changed

Rewrote `AGENTS.md`, `PROJECT_MEMORY.md`, `README.md`, and `MARKET.md` to describe the RADAR application that now exists in this repository, replacing the 2026-09-12 baseline that documented an empty workspace. `DOCUMENTATION_RULES.md` and `LANGUAGE.md` were reviewed and left unchanged — both are process/communication rules, not project-specific facts, so nothing in them was stale.

## Notes

- The repository root now contains `index.html` (the full RADAR app: a single-file, client-only P2P file-transfer tool built on PeerJS/WebRTC), a root-level `NothingHere` placeholder file, and this `CODEKIT/` documentation folder. `CODEKIT/` is a subfolder, not the project root, as it was when the 2026-09-12 baseline was recorded.
- Git history in this workspace shows commits `Create NothingHere`, `Add files via upload`, `Rename gemini-code-1789323854310.html to index.html`, and `Update index.html`, plus a separate, unmerged commit that introduced this `CODEKIT/` kit. The two histories were combined manually in this task by checking out the `CODEKIT/` folder from its commit into the current branch. Earlier project history beyond these commits remains **Unknown**.
- The owner states RADAR is deployed at `https://radatit.pages.dev` (Cloudflare Pages). This was not independently verified by fetching the URL from this workspace; no Cloudflare Pages config files exist in the repo to confirm deployment settings from code.
- Full technical detail (architecture, data flow, wire protocol, constants) is in the rewritten `AGENTS.md`; this entry intentionally avoids duplicating it.
- No application code was changed as part of this documentation update.

## Changed (later same day)

Reworked RADAR's UI/UX in `index.html` at the owner's request:

- **Responsive 100vh layout:** restructured the page into a single `.app` column, changed `body` to `min-height: 100dvh; display:flex; align-items:center; justify-content: safe center;` so the app is vertically centered like a card on desktop and stacks/scrolls naturally on mobile, and made typography/spacing responsive (`clamp()` sizes, a `min(250px, 55vw)` radar box, safe-area bottom padding).
- **Settings panel with a persistent custom callsign:** added a gear-icon button opening a modal where the user can set a callsign of exactly 3-4 words (`parseCustomCallsign()`); own identity (random or custom) is now persisted to `localStorage['radar_my_id']` via `loadOrCreateMyId()`/`saveMyId()` so it survives reloads, whereas previously a new random ID was generated on every page load. Saving a new callsign destroys and recreates the `Peer` (`createPeer()`) with the new ID.
- **Three send actions (File / Media / Paste):** replaced the single "Transmit Data" button with File, Media (`accept="image/*,video/*"`), and Paste (clipboard) buttons, all funneling into a shared `sendFile(file)` function. Paste (`sendFromClipboard()`) reads an image from the clipboard first, falling back to clipboard text sent as `clipboard.txt`.
- **60-second connect wait/retry/cancel:** `initiateConnection()` now retries `peer.connect()` every 3 seconds for up to 60 seconds when the target callsign isn't currently online (PeerJS `peer-unavailable` error), showing a live countdown and a Cancel button, instead of failing immediately on the first attempt.
- Added a Copy button for the user's own callsign, and a `conn.on('close')` handler that reverts the UI to the connect panel if an active link drops.

## Bugs Found

**Bug:** the callsign display, laid out in a flex row next to a Copy button, shrank and wrapped one character per line under `word-break: break-word`, inflating page height well past the viewport. **Cause:** a flex item can shrink below its content's natural width, and `break-word` then allows breaking anywhere, including mid-word. **Fix:** removed the flex row; the callsign is now a normal block element with `overflow-wrap: anywhere`, and the Copy button sits below it as its own full-width button. **Status:** fixed and verified with a headless-browser screenshot at both a 1280x800 and a 390x844 viewport.

**Bug:** with `body { justify-content: center }`, the inflated height from the bug above overflowed symmetrically and pushed the header (including the new Settings button) above the visible/scrollable area, making it permanently unreachable. **Cause:** centered flex/grid content that overflows its container is not scrollable into the "before start" direction by default in Chromium/Firefox. **Fix:** changed to `justify-content: safe center`. **Status:** fixed; kept in place as a defensive measure against any future overflow, not just this specific bug.

## Notes

- Verified with headless Playwright (Chromium) against a local static server, at desktop (1280x800) and mobile (390x844) viewports: no console/page errors, settings validation (rejects fewer/more than 3-4 words, accepts e.g. "apple river stone" → `APPLE-RIVER-STONE`), persisted-callsign save/reload, the 60-second connect retry countdown and manual cancel, and the transfer panel's File/Media/Paste buttons all rendering and functioning correctly.
- Real PeerJS (`unpkg.com`) could not be loaded from this sandboxed workspace's network (outbound to that host is blocked here), so verification used a small local stub `Peer` class standing in for the library to exercise the app's own state machine (connect retry/timeout/cancel, UI transitions). This does not verify actual WebRTC/signaling behavior — that depends on the real PeerJS library and network, which a visitor's browser has access to but this workspace does not. A real two-device test against the deployed site (`radatit.pages.dev`) is recommended before considering the connect/retry/transfer flows fully verified.
- No changes were made to the core chunked-transfer wire protocol (`header`/`chunk`/`eof` messages, 256 KB chunks, 16 MB backpressure threshold).
