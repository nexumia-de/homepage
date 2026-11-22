---
type: Reference
title: Dependencies
description: Tools and actions used to check and deploy the site, with pin location and licence; none of them is part of the published site.
tags: [dependencies, licences, ci]
generated: { by: claude-code/2, at: 2026-11-22T00:00:00Z }
---

# Shipped with the site

| What | Where | Licence |
|---|---|---|
| Figtree (variable, latin subset, from Fontsource) | `site/assets/fonts/figtree.woff2` | OFL-1.1 |
| Bricolage Grotesque (same) | `site/assets/fonts/bricolage-grotesque.woff2` | OFL-1.1 |

# Used to check and deploy, not shipped

Licences read from each package's or repository's own files on
2026-11-22. They only run in CI or locally, so they do not affect the
licence of the site.

| What | Pinned in | Licence |
|---|---|---|
| html-validate 11.21.1 | `tools/package.json` | MIT |
| linkinator 8.1.0 | `tools/package.json` | MIT |
| wrangler 4.151.3 | `tools/package.json` | MIT OR Apache-2.0 |
| actions/checkout | workflow, commit SHA | MIT |
| fsfe/reuse-action | workflow, commit SHA | GPL-3.0-or-later |
| cloudflare/wrangler-action | workflow, commit SHA | MIT OR Apache-2.0 |

Transitive npm packages are fixed by `tools/package-lock.json`.
Updates: [checks](checks.md#pins-and-updates).
