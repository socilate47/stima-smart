# Stima Smart — System

## Purpose
A no-hardware household electricity audit for Kenyan homes. It turns KPLC token purchases and meter readings into an itemised, appliance-level monthly bill and ranks savings tips by how much they would save. Built as the working prototype for an IRENA application (energy efficiency theme).

## Main components
- **Single-page web app** (`index.html`): inputs, calculations and rendering in plain JS, no build step.
- **Storage**: browser `localStorage` on every device; when the viewer is signed in to claude.ai and allowed to write, the household is also saved to the artifact `db` at `data/users/<id>/household` (private per viewer).
- **Hosting**: published as a claude.ai Artifact — https://claude.ai/artifact/LWsHUJWSRfFUfyCaJKetHh (private until shared from the page's Share menu).

## Operating context
- Users: households on KPLC prepaid (token) or postpaid meters.
- Runs on any phone browser; no accounts, sensors or AI calls required.
- Phase 2 (planned, not built): optional low-cost sensors for real-time appliance-level data.
