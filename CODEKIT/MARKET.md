# RADAR

Confirmed product name, from the app's page title and heading in `index.html`.

## One-Line Pitch

Send a file straight from your browser to someone else's — no upload, no account, just a callsign.

This is a direct, evidence-based description of the implemented feature set (direct P2P transfer, callsign-based connect, no accounts), not a claim about market positioning, competitors, or customer validation.

## The Problem

The intended customer and validated problem are **Unknown** — no product brief, customer research, or positioning notes exist in this repository.

What the code itself solves: sending a file from one browser to another without routing it through, or storing it on, a third-party server.

## The Idea

Two people each open the page, get a randomly generated callsign, and connect directly using WebRTC. Once linked, a file transfer goes straight between their browsers, with a live speed/progress readout styled like a "radar telemetry" interface.

## Signature Features

Confirmed, implemented features only (see [AGENTS.md](AGENTS.md) for code references):

- **Instant identity, no sign-up:** a random callsign (e.g. `NEON-42`) is generated on load — nothing to register.
- **Direct peer-to-peer transfer:** files move browser-to-browser over WebRTC once connected, not through a storage server.
- **Live telemetry:** real-time speed (KBPS/MB per second) and a progress bar during transfer.
- **Recent targets:** the last 3 peers connected to are remembered locally for one-click reconnect.

## Feature Stories

- **Instant identity, no sign-up** — *What it does:* generates a memorable code name the moment the page loads. *Why it matters:* nothing to create or remember beyond one code, no email or password. *What the user experiences:* opening the page and immediately having something to share with the other person.
- **Direct peer-to-peer transfer** — *What it does:* opens a direct WebRTC connection between two browsers and streams the file in 256 KB chunks. *Why it matters:* the file doesn't sit on a third-party server in between. *What the user experiences:* pick a file, watch it fly to the other side, done.
- **Live telemetry** — *What it does:* calculates and displays live throughput and progress while sending or receiving. *Why it matters:* the transfer isn't a black box — you can see it working. *What the user experiences:* a speed readout and progress bar in the app's "radar" visual style.

## Product Philosophy

Confirmed from the UI itself: a stripped-down, high-contrast "military telemetry / radar" visual identity (dark background, red accents, monospace status lines, callsigns, uplink/transmission language) and a workflow with no accounts or sign-up friction. Broader product values (privacy stance, target audience, long-term philosophy) are **Unknown** beyond what the working app demonstrates.

## Who Is It For?

**Unknown.** No target audience is documented. The app's design (no accounts, technical "callsign"/"uplink" framing) suggests it targets technically comfortable users who want quick ad-hoc file transfer, but this is an inference from the interface only — **Likely:**, not a confirmed positioning decision.

## Why It Feels Different

Not a claim this workspace can validate against competitors. Observably, the app skips the "upload to a server, share a link" pattern common to many file-sharing tools in favor of a live, direct connection — but no comparison research exists in this repository.

## Short Launch Description

Not confirmed as an approved launch/marketing statement — this is an accurate description of the current implementation only:

> RADAR is a single-page web app where two browsers connect directly and send a file peer-to-peer, with a live speed and progress readout. No accounts, no file uploads to a server — just a shared callsign and a direct link.

## Evidence Boundary

Baseline inspected on **2026-09-13** against the live `index.html` in this repository. Do not publish unsupported claims about user counts, performance benchmarks, security guarantees, uptime, or comparisons to other tools — none of that is established anywhere in this repository. Revisit this document if the app's feature set or the owner's positioning changes.
