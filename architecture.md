# Stima Smart — Architecture

## Data flow
```
User inputs ──► state {meterType, appliances[], tokens[], readings[]}
                  │
                  ├─► costPerUnit()   = Σ amount ÷ Σ units           (KES/kWh, incl. levies)
                  ├─► measuredDaily() = readings → kWh/day           (fallback: token spacing)
                  ├─► applianceDaily()= W × qty × h/day × days/7 ÷ 1000
                  ├─► runout()        = units left ÷ kWh/day         (prepaid only)
                  └─► tips            = keyword rules × appliance kWh × share saved
                  ▼
render: meter panel · itemised bill (+ "not explained" gap) · coverage % · tips · data tabs
```

## Key design decisions
- **No hardcoded tariff.** Cost per unit is derived from the user's own token purchases, so it reflects current tariffs, levies and taxes automatically.
- **Measured vs estimated kept separate.** Meter readings are ground truth; appliance figures are estimates. The gap between them is shown as "Not explained by your list" and a coverage %, so users can correct hours/wattage.
- **Prepaid meter maths.** Prepaid meters show units *left*, so use = first reading + tokens loaded after it (up to the last reading) − last reading. Postpaid uses last − first.
- **Storage fallback.** localStorage always; artifact `db` only when the viewer has an id and write access (outside/public-link viewers cannot write, so they stay device-only). Cloud writes are debounced and serialised (one write at a time).
- **Example household on first open**, clearly labelled, replaced by "Start my own audit".
- Immutable state updates (new arrays/objects on every change).
