# Groundwork AI — AI Readiness Audit Tool

Free, instant AI readiness audit for SMB owners. No backend. No signup. Runs in any browser.

Built by [Catalyst Works](https://catalystworks.consulting).

---

## What it does

5-question form → instant AI readiness score (0–100) → radar chart across 5 dimensions → top 3 automation priorities with specific tool recommendations → hours-saved estimate → CTA to book a strategy call.

Scoring is fully deterministic (no API calls). Works offline after first load.

---

## Stack

- Vanilla HTML / CSS / JavaScript (no framework, no build step)
- [Chart.js 4.4.0](https://www.chartjs.org/) via CDN
- [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts CDN

---

## Files

```
groundwork-ai/
├── index.html                  # The entire app — deploy this file
├── replit-kickoff-prompt.md    # Prompt to rebuild this from scratch in Replit AI Agent
├── assets/
│   └── .gitkeep               # Placeholder — drop logo files here when ready
├── README.md
└── DEPLOY.md                  # Deploy instructions (Replit + Hostinger)
```

---

## Local preview

Open `index.html` in any browser. No server needed.

```bash
# macOS / Linux
open index.html

# Windows
start index.html
```

Or serve it locally:
```bash
npx serve .
# → http://localhost:3000
```

---

## Customization

| Thing to change | Where |
|---|---|
| Calendly booking link | `index.html` — search `calendly.com/boubacarbarry` |
| Brand name "Groundwork AI" | `index.html` — search `Groundwork AI` (4 occurrences) |
| Industry priority recommendations | `INDUSTRY_PRIORITIES` object in the `<script>` block |
| Color scheme | `:root` CSS variables at top of `<style>` block |
| Hourly rates for ROI | `INDUSTRY_HOURLY_RATE` object in the `<script>` block |

---

## Deploy

See `DEPLOY.md` for step-by-step instructions for Replit and Hostinger.
