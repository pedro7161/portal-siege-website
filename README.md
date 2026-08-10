# Portal Siege — Website

Static GitHub Pages website for **Portal Siege**, a dark-fantasy strategy autobattler currently in development.

The website content is synchronized against:

- Game repository: `pedro7161/Portal-Siege`
- Stable implementation reference: `main`

## Project structure

```text
portal-siege-website/
├── .github/workflows/deploy-pages.yml
├── assets/
│   ├── portal-siege-emblem.svg
│   └── game/units/...        # presentation sprites, committed directly (see docs/shared-assets.md)
├── docs/shared-assets.md
├── index.html
├── privacy-policy.html
└── README.md
```

## Content represented

The landing page reflects repository-backed features including:

- Story Mode and Infinite Mode
- 3×3 active army grid and reserve bench
- merging and class-specific unit tiers
- seven recruitable Human classes
- multi-race enemy armies
- eleven configured bosses and signature moves
- run research and permanent research
- structures, portals, projectiles, and siege encounters
- active-development status without an unsupported release date

## Local preview

No build tool is required for the base site. Open `index.html` directly, or serve the repository root with any static file server.

Example:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080/`.

All images the site needs (including `assets/game/`) are committed directly to this repository, so a local preview shows exactly what deploys.

## Deployment

Deployment is handled by `.github/workflows/deploy-pages.yml`: it checks out this repository, assembles a static `_site/` (excluding `.git/`, `.github/`, `docs/`, and `README.md`), and uploads it to GitHub Pages. No other repository, secret, or external dependency is involved.

**Settings → Pages → Source** must be set to **GitHub Actions**.

## Asset policy

Only a small, curated set of presentation sprites lives in `assets/game/` — one hero-tier sprite per playable Human class, plus one flagship unit per implemented enemy race. See `docs/shared-assets.md` for the exact path convention and how to add or swap an image.
