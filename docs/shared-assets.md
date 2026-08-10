# Shared asset repository integration

The website consumes presentation-ready exports from the private repository `pedro7161/Portal-Siege-Assets` during GitHub Pages deployment.

## Why this is not a plain submodule

A normal Git submodule only stores a commit pointer. Because the asset repository is private and this website repository is public, GitHub Pages still needs credentials to clone the asset repository. The deployment workflow therefore performs an authenticated second checkout and assembles a public Pages artifact.

Only the curated website export folder is published. Raw generations, project files, process history, manifests, and game-only assets remain private.

## Asset contract

The deploy workflow pulls an explicit, curated list of file paths directly from
`final/game/assets/units/...` in the asset repository — one hero-tier sprite per
playable Human class, plus one flagship unit per implemented enemy race. That list
lives in `.github/workflows/deploy-pages.yml`'s "Select and download gallery images"
step, alongside a matching `CAPTIONS` map in "Build shared asset gallery" (every
source file is literally named `sprite.png`, so captions can't be derived from the
filename).

`final/web/assets/` and `assets/website/` were an earlier plan for a pre-curated
export folder the workflow would pull wholesale; that folder was never populated
(still just a `.gitkeep`), so the workflow was changed to select specific paths
instead. If a curated export folder gets built later, prefer switching back to it
over maintaining a hand-picked file list here.

The selected files are copied into the deployed site as:

```text
assets/game/
```

Website HTML should therefore use paths such as:

```html
<img src="assets/game/units/humans/knight/tier4/sprite.png" alt="Human Knight">
```

## Required repository secret

Create a fine-grained personal access token with read-only access to `pedro7161/Portal-Siege-Assets`, then add it to the website repository as an Actions secret named:

```text
ASSETS_REPO_TOKEN
```

Required token permission:

- Repository contents: Read-only

Do not place the token in source files, workflow YAML, HTML, or repository variables.

## GitHub Pages setting

After this workflow is merged, set the website repository's Pages source to **GitHub Actions** rather than **Deploy from a branch**.

## Local development

For local previews, clone the asset repository separately and copy its curated website export to `assets/game/`, or use a local symlink that is excluded from commits.

The deployed website never receives the entire private asset repository; only the approved export directory is copied into the Pages artifact.
