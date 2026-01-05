# Discr Presentations

Investor pitch decks and product demos for Discr, built with Marp.

## Quick Start

```bash
npm install
npm run dev
```

Open http://localhost:8080 to view presentations.

## Commands

| Command | Description |
|---------|-------------|
| `npm run dev` | Start dev server with hot reload |
| `npm run build` | Build HTML to dist/ |
| `npm run build:pdf` | Build PDFs to dist/ |
| `npm run preview` | Serve built files |

## Adding GIFs

1. Record from iOS Simulator: `xcrun simctl io booted recordVideo demo.mov`
2. Convert to GIF (see CLAUDE.md for full command)
3. Add to `public/images/`
4. Reference in slides: `![](../public/images/demo.gif)`

## Decks

- `decks/investor-pitch.md` - Main investor pitch deck
- `decks/customer-demo.md` - Product walkthrough (coming soon)

## Deployment

Automatically deploys to Cloudflare Pages on push to main.
