---
type: Checklist
title: Owner checks
description: What only the owner can do or confirm for this repository - settings, legal details, registrations.
tags: [owner, checklist, settings, legal]
generated: { by: claude-code/2, at: 2026-11-22T00:00:00Z }
---

Agents add to this list instead of asking; tick or delete an item when
it is done.

# Repository settings (#5)

- [ ] Import the ruleset: Settings → Rules → Rulesets → New ruleset →
  Import a ruleset → `.github/rulesets/main.json`. Do this after the
  pull request that adds it is merged, so that `check` has run once.
- [ ] Dependabot: Settings → Advanced Security → enable *Dependabot
  version updates* if it is off (the file `.github/dependabot.yml` is
  there).
