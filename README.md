# Stima Smart

A no-hardware household electricity audit for Kenyan homes. Stima Smart turns your KPLC token purchases and meter readings into an itemised, appliance-level monthly bill, then ranks energy-saving tips by how many shillings each would save you.

Built as a working prototype for an IRENA application (energy efficiency theme).

## Features

- **Appliance list** with typical-wattage presets (kettle, iron, TV, fridge, bulbs…) and hours/day, days/week.
- **Token purchases** — paste a KPLC token SMS and the app reads the amount and units for you to confirm.
- **Meter readings** for prepaid (units left) or postpaid (cumulative kWh) meters.
- **Your real cost per unit**, worked out from what you paid for tokens, so it already includes levies and taxes. No hardcoded tariff.
- **Measured daily use**, estimated monthly cost and **token run-out date** (prepaid).
- **Itemised monthly bill** per appliance, plus usage not explained by your list and a coverage %.
- **Ranked savings tips** with KES/month estimates from your own data.

Meter readings and token purchases are measured; appliance figures are estimates. The gap between them is shown so you can fine-tune hours and wattage until coverage is near 100%.

## Quick start

No install, no build step, no account.

```bash
git clone https://github.com/socilate47/stima-smart.git
cd stima-smart
xdg-open index.html   # or just open index.html in any browser
```

Works on phone browsers. Data is saved in your browser's `localStorage`.

## How to use

1. Press **Start my own audit** to clear the example household.
2. **Settings:** choose prepaid or postpaid meter.
3. **Appliances:** pick a common appliance or read the wattage off its label; set hours/day and days/week.
4. **Tokens:** paste the KPLC token SMS, press *Read SMS*, check the numbers, add.
5. **Meter readings:** read the meter at about the same time each day — two readings a few days apart unlock measured use.
6. Adjust appliance hours until coverage is near 100%, then follow the top tips.

## How it works

| Figure | Calculation |
|---|---|
| Cost per unit (KES/kWh) | total paid for tokens ÷ total units received |
| Daily use, prepaid | (first reading + tokens loaded since − last reading) ÷ days |
| Daily use, postpaid | (last reading − first reading) ÷ days |
| Appliance kWh/day | watts × qty × hours/day × days/week ÷ 7 ÷ 1000 |
| Token run-out | units left ÷ kWh/day |

More detail in [`architecture.md`](architecture.md), [`requirements.md`](requirements.md) and [`gude.md`](gude.md).

## Development

Everything lives in `index.html` (HTML, CSS and plain JavaScript; the only external resource is Google Fonts). To syntax-check the script, extract the `<script>` block and run `node --check` on it.

## Roadmap

- Phase 2: optional low-cost sensors for real-time, appliance-level data.
