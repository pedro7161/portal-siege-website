# Portal Siege — Website

Static GitHub Pages website for **Portal Siege**, a dark-fantasy strategy autobattler currently in development.

The website content is synchronized against:

- Game repository: `pedro7161/Portal-Siege`
- Shared asset repository: `pedro7161/Portal-Siege-Assets`
- Primary game content branch used: `feature/ai-sprite-assets`
- Stable implementation reference: `main`

## Project structure

```text
portal-siege-website/
├── .github/workflows/deploy-pages.yml
├── assets/
│   └── portal-siege-emblem.svg
├── docs/shared-assets.md
├── index.html
├── privacy-policy.html
└── README.md
```

During deployment, curated files from the private asset repository are copied into the generated site at:

```text
assets/game/
```

The private source repository itself is never published.

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

Shared images are not committed to this repository. For a full local preview, populate `assets/game/` from the curated website export in `Portal-Siege-Assets`.

## Deployment

Deployment is handled by `.github/workflows/deploy-pages.yml`.

The workflow:

1. checks out this public website repository;
2. checks out the private `Portal-Siege-Assets` repository using the `ASSETS_REPO_TOKEN` secret;
3. copies only `final/web/assets/` or `assets/website/` into `assets/game/`;
4. uploads the assembled static site to GitHub Pages.

After merging this setup:

- add the `ASSETS_REPO_TOKEN` Actions secret;
- set **Settings → Pages → Source** to **GitHub Actions**.

See `docs/shared-assets.md` for the token and folder contract.

## Asset policy

The website consumes only lightweight, presentation-ready exports. Raw generation batches, layered project files, processing history, duplicated sprites, and game-only assets remain in the private shared asset repository.
