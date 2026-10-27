# Stima Smart — Guide

## Use it
1. Open https://claude.ai/artifact/LWsHUJWSRfFUfyCaJKetHh (share it from the page's Share menu so others can open it).
2. Press **Start my own audit** to clear the example household.
3. **Settings:** pick prepaid or postpaid meter.
4. **Appliances:** choose a common appliance (fills typical watts) or read the label; set hours/day and days/week.
5. **Token purchases:** paste the KPLC token SMS and press *Read SMS*, check the numbers, add.
6. **Meter readings:** read the meter at about the same time each day; two readings a few days apart unlock measured use.
7. Adjust appliance hours until coverage is near 100%, then follow the top tips.

## Develop
- Edit `index.html` (HTML + CSS + JS in one file, no dependencies besides Google Fonts).
- Syntax check: extract the `<script>` and run `node --check`.
- Republish: publish `index.html` again with the Artifact tool from this directory (same URL).
