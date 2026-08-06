# Portal Siege — Website

Static GitHub Pages website for **Portal Siege**, a dark-fantasy strategy autobattler currently in development.

The website content is synchronized against the game repository:

- Game repository: `pedro7161/Portal-Siege`
- Primary content branch used: `feature/ai-sprite-assets`
- Stable implementation reference: `main`

## Project structure

```text
portal-siege-website/
├── assets/
│   └── portal-siege-emblem.svg
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

No build tool is required. Open `index.html` directly, or serve the repository root with any static file server.

Example:

```bash
python3 -m http.server 8080
```

Then open `http://localhost:8080/`.

## Deployment

The repository remains compatible with GitHub Pages deployed from the repository root. In repository settings, select **Pages**, choose **Deploy from a branch**, and publish the `main` branch from `/ (root)` after changes are reviewed and merged.

## Asset policy

Only lightweight, presentation-ready website assets should be added here. Raw generation batches, processing artifacts, duplicated sprites, and internal asset-working folders from the game repository should not be copied wholesale.
