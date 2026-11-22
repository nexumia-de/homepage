# Directory Update Log

## 2026-11-22
* **Creation**: [Checks before deploy](checks.md), [Dependencies](dependencies.md), [Owner checks](owner-checks.md), #5: the workflow gets a job `check` that `deploy` needs (REUSE, html-validate, linkinator for internal links, assets and anchors, `wrangler deploy --dry-run`); tools pinned in `tools/package.json`, which is also the one place for the wrangler version; Dependabot for actions and tools; `.github/rulesets/main.json` requiring `check`; `AGENTS.md` importing the toolkit's core rules. The new HTML check found one real error (`aria-label` on a `pre`), fixed in its own commit.
