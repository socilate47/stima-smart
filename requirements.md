# Stima Smart — Requirements

## Functional
- Record appliances (name, watts, quantity, hours/day, days/week) with typical-wattage presets.
- Record token purchases (date, KES paid, kWh); parse values from a pasted KPLC token SMS for the user to confirm.
- Record meter readings for prepaid (units left) or postpaid (cumulative kWh) meters.
- Show: cost per unit, measured daily use, estimated monthly cost, token run-out date.
- Show an itemised monthly bill per appliance, plus unexplained usage and coverage %.
- Rank savings tips with KES/month estimates from the user's own data.
- Persist data per user; clear-all with in-page confirmation.

## Constraints
- No hardware, no paid APIs, works on a phone browser.
- No fabricated tariff figures; all prices come from user-entered token purchases.
- Appliance costs are labelled as estimates; meter data as measured.

## Dependencies
- Google Fonts (Archivo, Source Sans 3, IBM Plex Mono) with system fallbacks.
- claude.ai Artifact runtime (`db`, `user` capabilities) — optional; app works without them.
