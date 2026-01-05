# Discr Presentations - Project Memory

This file contains persistent context for Claude Code sessions on this project.
It will be automatically loaded at the start of every session.

## Project Overview

This repository contains presentation decks for Discr, built with Marp
(Markdown Presentation Ecosystem). Decks are used for investor pitches,
customer demos, and product announcements.

**Key Details:**

- **Tool:** Marp CLI (Markdown to HTML/PDF)
- **Syntax:** Markdown with Marp directives
- **Deployment:** Cloudflare Pages
- **Domain:** pitch.discrapp.com (or similar)
- **Linting:** Pre-commit hooks for markdown quality

## Repository Structure

```text
presentations/
├── decks/                 # Presentation markdown files
│   ├── investor-pitch.md  # Main investor deck
│   ├── customer-demo.md   # Product walkthrough
│   └── feature-updates.md # What's new presentations
├── public/                # Static assets
│   ├── images/            # Screenshots, mockups, logos
│   └── videos/            # Demo recordings, GIFs
├── dist/                  # Build output (gitignored)
├── .github/workflows/     # CI/CD
├── package.json
└── CLAUDE.md
```

## Marp Syntax Reference

### Slide Separation

```markdown
---
# Slide 1

Content here

---

# Slide 2

More content
```

### Front Matter (First Slide)

```markdown
---
marp: true
theme: default
paginate: true
backgroundColor: #fff
---
```

### Directives

```markdown
<!-- _class: lead -->       # Apply class to current slide
<!-- _backgroundColor: #123 -->  # Slide-specific background
<!-- _color: white -->      # Slide-specific text color
```

### Images

```markdown
![width:500px](./public/images/screenshot.png)
![bg right:40%](./public/images/hero.gif)  # Background image
```

### Columns (using HTML)

```markdown
<div style="display: flex; gap: 2rem;">
<div>

Left column content

</div>
<div>

Right column content

</div>
</div>
```

## Development Workflow

### Running Locally

```bash
npm run dev          # Start dev server with hot reload
npm run build        # Build HTML to dist/
npm run build:pdf    # Build PDFs to dist/
npm run preview      # Serve dist/ folder
```

### Adding New Slides

1. Edit the appropriate deck in `decks/`
2. Add images/GIFs to `public/images/`
3. Reference images with relative paths: `./public/images/demo.gif`
4. Preview with `npm run dev`

### Recording iOS Simulator GIFs

```bash
# Record video from simulator
xcrun simctl io booted recordVideo demo.mov

# Convert to GIF (requires ffmpeg + gifsicle)
ffmpeg -i demo.mov -vf "fps=15,scale=320:-1" -c:v gif demo.gif
gifsicle --optimize=3 demo.gif -o demo-optimized.gif
```

## Git Workflow

**CRITICAL:** All changes MUST go through Pull Requests.

1. **Create feature branch:** `git checkout -b deck/description`
2. **Make changes** to deck markdown
3. **Run pre-commit:** `pre-commit run --all-files`
4. **Commit:** `git commit -m "deck: update investor pitch with new feature"`
5. **Create PR:** `gh pr create`

**Commit Format:**

- `deck:` - Deck content changes
- `asset:` - New images/GIFs
- `chore:` - Build/config changes
- `docs:` - README/CLAUDE.md updates

## Keeping Decks Updated

When new features are added to the mobile app:

1. Record a GIF demo from the iOS simulator
2. Add the GIF to `public/images/`
3. Update relevant decks (investor-pitch, customer-demo)
4. Consider updating the web landing page with the same GIF

### Shared Assets with Web Repo

GIFs created for presentations can also be used in the web landing page.
Consider storing canonical versions here and copying to web when needed,
or setting up a shared asset pipeline.

## Deck Guidelines

### Investor Pitch

- Focus on problem, solution, traction, market, team
- Use metrics and social proof
- Keep slides minimal - one idea per slide
- Include product demos via GIFs

### Customer Demo

- Focus on user flows and benefits
- Show the app in action
- Highlight key differentiators
- End with clear CTA

## Pre-commit Hooks

**Installed hooks:**

- Markdown linting
- Trailing whitespace
- End of file fixer
- YAML validation

**Setup:**

```bash
pre-commit install
pre-commit run --all-files
```

## References

- Marp Documentation: <https://marp.app/>
- Marp CLI: <https://github.com/marp-team/marp-cli>
- Mobile app: `../mobile/`
- Web landing: `../web/`

---

**Last Updated:** 2025-01-05

This file should be updated whenever:

- Deck structure changes
- New presentation types are added
- Asset workflows change
