# Game art on the website

Game art shown on the website is committed directly to this repository under:

```text
assets/game/units/<race>/<category>/tier<N>/sprite.png
```

(or `assets/game/units/<race>/<name>/sprite.png` for special/bonus units that don't
use a tiered category — e.g. the goblin and vampire archetypes).

This mirrors the path layout under `public/assets/units/` in the game repository
(`pedro7161/Portal-Siege`), so an image can be copied over as-is without renaming.

## Adding or swapping an image

1. Pick the sprite from the game repo, e.g. `public/assets/units/humans/knight/tier4/sprite.png`.
2. Copy it into this repo at the matching path under `assets/game/units/...`.
3. Add (or update) an `<img>` card in `index.html`'s `#game-art` section:
   ```html
   <figure><div class="game-art-card"><img loading="lazy" decoding="async" src="assets/game/units/humans/knight/tier4/sprite.png" alt="Human Knight"></div><figcaption class="game-art-meta">Human Knight</figcaption></figure>
   ```
4. Commit both the image and the HTML change together.

## Why not pull from the private asset repository at deploy time

An earlier version of this workflow authenticated into the private
`pedro7161/Portal-Siege-Assets` repository during each deploy and copied a curated
(or, for a while, blindly-selected) set of images into the build. That added a
private-repo checkout, a Git LFS pull, and a token dependency (`ASSETS_REPO_TOKEN`)
to every deploy, and the images it produced weren't showing up reliably on the
live site. Committing the handful of presentation images this site actually needs
directly into the repo removes all of that — the deploy workflow is now a plain
static-site upload with no external dependencies.
