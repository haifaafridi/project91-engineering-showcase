# Project 91 — Demo Walkthrough

This is a **public-facing storyboard**, not a live-trading instruction guide. Record only permission-cleared, sanitized material. A recorded or mock interface is sufficient; no fresh transaction or funded activity is necessary.

## Suggested 75–90-second video

| Time | On screen | Voiceover idea |
|---|---|---|
| 0–10s | Project title and a sanitized application overview | “Project 91 is an event-driven Solana engineering project I worked on, built around a Rust backend and Windows operator interface.” |
| 10–25s | Static/sanitized operator dashboard | “It brings wallet-event observation, classification, configurable policy, and operational status into one interface.” |
| 25–45s | Conceptual architecture diagram from the README | “The key challenge was reliable state transitions when observations, networks, or on-chain outcomes are uncertain.” |
| 45–65s | Approved, redacted activity/status or position UI, ideally synthetic data | “Durable journals and reconciliation distinguish pending, uncertain, and confirmed outcomes instead of guessing.” |
| 65–80s | The public validation summary (not private runtime logs) | “The reviewed scope includes a successful no-spend mainnet buy simulation, a confirmed reconciled manual-sell test, and Windows launcher self-tests.” |
| 80–90s | GitHub showcase link | “The implementation remains private; I documented the architecture and lessons learned here.” |

## Suggested recording format

- Landscape, ideally 1920 × 1080; use readable zoom and a clean desktop.
- Use a short MP4 if possible. Optional captions make it easier to watch muted.
- Prefer static screenshots or a mock/sanitized demo over connecting to production.
- Label simulated/mock data clearly. Do not present simulated outputs as fresh real trades.
- Include an explicit “historical validation” label where showing past test results.
- Do not claim guaranteed returns, sub-millisecond performance, or universal support.

## Publication checklist

Before recording or posting, confirm approval under the relevant client agreement. **Hide or replace** wallet addresses, balances, tracked wallets, transaction signatures, API/provider credentials, local file paths, notifications, private chat messages, internal issue identifiers, client branding, and commercially sensitive strategy parameters.

Do not open secret configuration, source files, keypairs, live logs, or production databases while recording. Cropping and using mock data **before recording** is safer than relying only on post-production blur.

## What to share for README integration

When the recording and screenshots are ready, add only the approved, sanitized copies. Recommended assets:

- `media/project91-overview.png`: approved interface overview.
- `media/project91-activity.png`: approved or synthetic activity/reconciliation states.
- `media/project91-architecture.png`: an optional exported public architecture image (the README already includes a Mermaid diagram).
- A video link or an approved small video file; link it prominently from the README.

Nothing in this document requires running Live mode or spending SOL.
