# RADAR

A single-page web app for sending a file directly from one browser to another, peer-to-peer, with a live transfer speedometer.

"RADAR" is confirmed from the app's own page title (`RADAR // ACTIVE`) and on-screen heading (`Radar.`).

## What Is This?

RADAR lets two people connect their browsers directly to each other and send something — a file, a photo/video, or whatever's on your clipboard — without uploading it to a server first. Each visitor gets a callsign, random by default (like `NEON-42`) or a custom one you set yourself; one person shares their callsign with the other, who types it in to "Establish Link." If the other device isn't online yet, RADAR keeps trying for up to a minute before giving up, so you don't have to time it perfectly. Once connected, either side can send, and both sides watch a live speed and progress readout while it transfers.

The whole app is one file: `index.html`, in the repository root.

## Why Does It Exist?

**Not confirmed yet.** The code is self-explanatory about *what* it does (direct browser-to-browser file transfer), but the motivating problem, target audience, and any prior history of this project are not documented anywhere in the repository.

## What Can It Do?

### Available (confirmed from `index.html`)

- Generates a random, memorable "callsign" identity for each visitor (no sign-up or account) — and remembers it across visits, so it doesn't change every time you reload the page.
- A Settings panel (gear icon) lets you replace your callsign with your own custom one, as long as it's exactly 3 or 4 words (e.g. "apple river stone").
- Lets one visitor connect directly to another by typing their callsign. If the other device isn't online yet, RADAR automatically retries for up to 60 seconds, showing a countdown, before giving up — you can also cancel manually at any time.
- Remembers the last 3 peers you've connected to (in your browser only) so you can reconnect with one click.
- Three ways to send once connected: **File** (any file type), **Media** (opens your photo/video picker or camera on mobile), and **Paste** (sends whatever's currently on your clipboard — an image or text).
- Sends directly between the two connected browsers, in the background, over a direct peer-to-peer connection — nothing passes through a server that stores it.
- Shows a live transfer speed (KBPS and MB/s) and a progress bar with a percentage and byte count while something is sending or receiving.
- Automatically downloads the received item on the receiving side once the transfer completes.
- Works as a centered card on desktop and a naturally stacking, scrollable screen on mobile.

### Planned

No roadmap or planned features are confirmed anywhere in this repository.

## How It Works

Open `index.html` in a browser (or visit the deployed site). The page gets you a callsign automatically. To connect to someone else, they share their callsign with you (or vice versa), you type it into "Target Coordinates," and click "Establish Link." Once linked, click "Transmit Data" to pick and send a file — it goes straight to the other browser.

Under the hood, this uses a browser technology called WebRTC (via a helper library called PeerJS) that lets two browsers talk to each other directly once they've found each other, rather than routing your file through a server.

## Current Status

A working, deployed single-file app. The owner states it is live at **https://radatit.pages.dev** (Cloudflare Pages); this workspace has not independently verified that the deployed site matches the current `index.html` in this repository.

## Getting Started

There is nothing to install or build — `index.html` is a complete, self-contained web page (it loads its one dependency, PeerJS, from a CDN). Opening the file in a browser, or serving the repository with any static file server, runs the app locally.

Read [PROJECT_MEMORY.md](PROJECT_MEMORY.md) for the current situation, then [AGENTS.md](AGENTS.md) for the technical walkthrough, before making changes.

## Project Structure

| Document | What it tells you |
| --- | --- |
| [LANGUAGE.md](LANGUAGE.md) | How agents should explain their work |
| [AGENTS.md](AGENTS.md) | How the project works technically |
| [README.md](README.md) | What this project is (this file) |
| [MARKET.md](MARKET.md) | How to describe the product without unsupported claims |
| [DEVLOG.md](DEVLOG.md) | What happened and why |
| [PROJECT_MEMORY.md](PROJECT_MEMORY.md) | Where things stand now |
| [DOCUMENTATION_RULES.md](DOCUMENTATION_RULES.md) | How to keep these notes accurate |

## Important Notes and Current Limitations

- There is no server-side storage, accounts, or authentication — connections are only as trustworthy as the callsign exchange between the two people involved.
- Connectivity relies on a third-party signaling service (PeerJS's default public server) and plain STUN; some network setups may be unable to connect peer-to-peer. Not independently tested from this workspace.
- The receiving browser holds the whole incoming file in memory before saving it, so very large files could be demanding on the receiver's device (see [AGENTS.md](AGENTS.md) for detail).
- No passwords or access tokens are used by, or should ever be added to, this documentation.
