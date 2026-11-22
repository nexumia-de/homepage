---
type: Playbook
title: Checks before deploy
description: The CI job check that gates every deploy, how to run it locally, and how the ruleset and Dependabot keep it in force.
tags: [ci, checks, html, links, reuse, dependabot, rulesets]
generated: { by: claude-code/2, at: 2026-11-22T00:00:00Z }
sources:
  - id: html-validate
    resource: https://html-validate.org/rules/
    title: html-validate rules
  - id: linkinator
    resource: https://github.com/JustinBeckwith/linkinator
    title: linkinator README
---

# Goal

Nothing reaches nexumia.de or a preview URL unless the job `check` in
`.github/workflows/deploy.yml` passed: `deploy` has `needs: check`.

# What `check` does

| Step | Tool | Fails on |
|---|---|---|
| Licence of every file | `fsfe/reuse-action` (`reuse lint`) | a file that `REUSE.toml` does not cover, a missing licence text |
| Valid HTML | html-validate, preset `html-validate:recommended`[^html-validate] | invalid or inaccessible markup in `site/**/*.html` |
| Internal links, assets and anchors | linkinator[^linkinator] serving `site/` and crawling from `index.html` and `404.html` | a link, image, stylesheet, icon or preload that returns 404, or a `#fragment` without a matching id |
| Worker configuration | `wrangler deploy --dry-run` | a `wrangler.jsonc` that wrangler rejects |
| Placeholders left for the owner | `grep data-owner-todo` | nothing; it prints a warning, see [owner checks](owner-checks.md) |

Choices:

- **External links are not checked** (`--skip` on everything that is not
  the local server). A deploy must not fail because another site is
  down or blocks the runner. Check them by hand when adding one.
- **`url()` in `style.css` is not checked**: linkinator's `--check-css`
  did not report a missing font in a test. The two fonts are covered
  through the `preload` links in `index.html`.
- `doctype-style` is set to lowercase (`<!doctype html>`), the form the
  site uses; both are valid HTML.
- linkinator instead of lychee (the issue's suggestion): it is pinned and
  updated through the same `tools/package.json` as the other tools and
  runs the same way locally and in CI.
- Node comes from the runner image; the tools need Node 22 or newer.

# Run it locally

```sh
reuse lint
```

```sh
npm --prefix tools ci
```

```sh
npm --prefix tools run check
```

`npm --prefix tools run config` runs the wrangler dry run.

# Pins and updates

Everything is pinned exactly (see [dependencies](dependencies.md)).
`.github/dependabot.yml` opens weekly grouped pull requests for the
actions and for `tools/`. The wrangler version exists once, as
`devDependencies.wrangler` in `tools/package.json`: the deploy job
reads it and passes it to `cloudflare/wrangler-action`, so a Dependabot
update changes the check, local runs and the deploy together.

Dependabot pull requests run `check` only; `deploy` is skipped for them
because they get no secrets.

# Ruleset

`.github/rulesets/main.json` (modelled on phosh-toolkit's, see its
`docs/branch-protection.md`) requires a pull request and the status
check `check`. `Deploy to Cloudflare` is not required: it is skipped
for Dependabot and forks and would block those merges. The check name
is the job id; rename the job and the ruleset entry together and
re-import. The owner imports the file once: [owner checks](owner-checks.md).

[^html-validate]: html-validate rules
[^linkinator]: linkinator README
