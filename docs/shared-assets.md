# Shared asset repository integration

The website consumes presentation-ready exports from the private repository `pedro7161/Portal-Siege-Assets` during GitHub Pages deployment.

## Why this is not a plain submodule

A normal Git submodule only stores a commit pointer. Because the asset repository is private and this website repository is public, GitHub Pages still needs credentials to clone the asset repository. The deployment workflow therefore performs an authenticated second checkout and assembles a public Pages artifact.

Only the curated website export folder is published. Raw generations, project files, process history, manifests, and game-only assets remain private.

## Asset contract

The workflow checks these source paths in order:

1. `final/web/assets/`
2. `assets/website/`

The selected folder is copied into the deployed site as:

```text
assets/game/
```

Website HTML should therefore use paths such as:

```html
<img src="assets/game/units/humans/knight/tier1.webp" alt="Human Knight tier 1">
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
