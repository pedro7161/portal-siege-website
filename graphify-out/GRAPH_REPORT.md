# Graph Report - .  (2026-07-22)

## Corpus Check
- Corpus is ~2,258 words - fits in a single context window. You may not need a graph.

## Summary
- 28 nodes · 38 edges · 5 communities
- Extraction: 92% EXTRACTED · 5% INFERRED · 3% AMBIGUOUS · INFERRED: 2 edges (avg confidence: 0.85)
- Token cost: 0 input · 0 output

## Community Hubs (Navigation)
- Privacy Policy Page
- Landing Page Sections
- Overview & Features
- GitHub Pages Deploy
- README & Structure

## God Nodes (most connected - your core abstractions)
1. `Portal Siege main page (index.html)` - 16 edges
2. `Privacy Policy page (privacy-policy.html)` - 12 edges
3. `Sticky navigation (Overview, Modes, Features, Screenshots, Contact)` - 6 edges
4. `Deploy static content to Pages (GitHub Actions workflow)` - 5 edges
5. `Portal Siege Website README` - 3 edges
6. `Live URLs table (main page, privacy policy)` - 3 edges
7. `Project structure listing (index.html, privacy-policy.html, README.md)` - 3 edges
8. `Deploying to GitHub Pages instructions` - 2 edges
9. `Game Overview section` - 2 edges
10. `Game Modes section (Story Mode, Infinity Mode, Research Systems)` - 2 edges

## Surprising Connections (you probably didn't know these)
- `Deploying to GitHub Pages instructions` --conceptually_related_to--> `Deploy static content to Pages (GitHub Actions workflow)`  [AMBIGUOUS]
  README.md → .github/workflows/static.yml
- `Deploy static content to Pages (GitHub Actions workflow)` --references--> `Portal Siege main page (index.html)`  [INFERRED]
  .github/workflows/static.yml → index.html
- `Deploy static content to Pages (GitHub Actions workflow)` --references--> `Privacy Policy page (privacy-policy.html)`  [INFERRED]
  .github/workflows/static.yml → privacy-policy.html
- `Live URLs table (main page, privacy policy)` --references--> `Portal Siege main page (index.html)`  [EXTRACTED]
  README.md → index.html
- `Live URLs table (main page, privacy policy)` --references--> `Privacy Policy page (privacy-policy.html)`  [EXTRACTED]
  README.md → privacy-policy.html

## Import Cycles
- None detected.

## Hyperedges (group relationships)
- **GitHub Pages site deployment: workflow publishes index.html and privacy-policy.html** — index, privacy_policy, _github_workflows_static_deploy_workflow [INFERRED 0.85]
- **Privacy policy as Google Play Console submission requirement for the Android/Capacitor app** — readme_project_structure, privacy_policy, index_get_section [INFERRED 0.75]

## Communities (5 total, 0 thin omitted)

### Community 0 - "Privacy Policy Page"
Cohesion: 0.22
Nodes (9): Footer (copyright + Privacy Policy link), Privacy Policy page (privacy-policy.html), Changes to This Policy section, Children's Privacy section (safe for under 13), Contact section (portalsiege@outlook.com), Data Collection section (no name/email/device ID/location/telemetry collected), Data Storage section (progress stored locally on device only), Overview section (no personal data collected, stored, or shared) (+1 more)

### Community 1 - "Landing Page Sections"
Cohesion: 0.33
Nodes (6): Portal Siege main page (index.html), Get the Game section (Web Demo, Android/Capacitor, Source), Hero section (title + tagline), How to Play section (Merge, Grid & Bench, Summons, Research), Progression section (story missions, chapter bosses), Status section (in development, coming soon to Google Play)

### Community 2 - "Overview & Features"
Cohesion: 0.33
Nodes (6): Contact section (portalsiege@outlook.com), Features section (merge, survive waves, upgrades, bosses, missions), Game Modes section (Story Mode, Infinity Mode, Research Systems), Sticky navigation (Overview, Modes, Features, Screenshots, Contact), Game Overview section, Screenshots section (placeholders)

### Community 3 - "GitHub Pages Deploy"
Cohesion: 0.50
Nodes (4): Deploy job (checkout, configure-pages, upload-pages-artifact, deploy-pages), Deploy static content to Pages (GitHub Actions workflow), Workflow triggers (push to main, workflow_dispatch), Deploying to GitHub Pages instructions

### Community 4 - "README & Structure"
Cohesion: 0.67
Nodes (3): Portal Siege Website README, Live URLs table (main page, privacy policy), Project structure listing (index.html, privacy-policy.html, README.md)

## Ambiguous Edges - Review These
- `Deploy static content to Pages (GitHub Actions workflow)` → `Deploying to GitHub Pages instructions`  [AMBIGUOUS]
  README.md · relation: conceptually_related_to

## Knowledge Gaps
- **14 isolated node(s):** `Workflow triggers (push to main, workflow_dispatch)`, `Deploy job (checkout, configure-pages, upload-pages-artifact, deploy-pages)`, `Hero section (title + tagline)`, `How to Play section (Merge, Grid & Bench, Summons, Research)`, `Progression section (story missions, chapter bosses)` (+9 more)
  These have ≤1 connection - possible missing edges or undocumented components.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **What is the exact relationship between `Deploy static content to Pages (GitHub Actions workflow)` and `Deploying to GitHub Pages instructions`?**
  _Edge tagged AMBIGUOUS (relation: conceptually_related_to) - confidence is low._
- **Why does `Portal Siege main page (index.html)` connect `Landing Page Sections` to `Privacy Policy Page`, `Overview & Features`, `GitHub Pages Deploy`, `README & Structure`?**
  _High betweenness centrality (0.649) - this node is a cross-community bridge._
- **Why does `Privacy Policy page (privacy-policy.html)` connect `Privacy Policy Page` to `Landing Page Sections`, `GitHub Pages Deploy`, `README & Structure`?**
  _High betweenness centrality (0.478) - this node is a cross-community bridge._
- **Why does `Deploy static content to Pages (GitHub Actions workflow)` connect `GitHub Pages Deploy` to `Privacy Policy Page`, `Landing Page Sections`?**
  _High betweenness centrality (0.205) - this node is a cross-community bridge._
- **Are the 2 inferred relationships involving `Deploy static content to Pages (GitHub Actions workflow)` (e.g. with `Portal Siege main page (index.html)` and `Privacy Policy page (privacy-policy.html)`) actually correct?**
  _`Deploy static content to Pages (GitHub Actions workflow)` has 2 INFERRED edges - model-reasoned connections that need verification._
- **What connects `Workflow triggers (push to main, workflow_dispatch)`, `Deploy job (checkout, configure-pages, upload-pages-artifact, deploy-pages)`, `Hero section (title + tagline)` to the rest of the system?**
  _14 weakly-connected nodes found - possible documentation gaps or missing edges._