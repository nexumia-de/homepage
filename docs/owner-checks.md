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

# Legal notice and privacy notice (#2)

Why: [decision](decisions/legal-pages.md). Not legal advice; have the
texts checked if in doubt.

- [ ] `site/imprint.html`: replace every `<span class="todo"
  data-owner-todo>…</span>` with your first and last name, a postal
  address where mail reaches you (no P.O. box), an email address and a
  second quick contact (phone number or contact form). Then delete the
  `<p class="notice" data-owner-todo>` paragraph. CI warns while a
  placeholder is left. Best done before merging the pull request, or
  right after.
- [ ] Decide whether "Responsible for the content (§ 18 (2) MStV)"
  stays; it is only required for journalistic-editorial content and
  harmless otherwise.
- [ ] Cloudflare dashboard: keep Web Analytics, Logpush and Workers
  Logs off for `nexumia.de`, or tell an agent to update
  `site/privacy.html`. Confirm that the Cloudflare data processing
  addendum applies to your account (it is part of the self-serve
  terms) and that Cloudflare is still listed under the EU–US Data
  Privacy Framework.
- [ ] games.nexumia.de (LocalGameGalaxy) and flatpak.nexumia.de
  (phosh-apps): add a footer link to `https://nexumia.de/imprint` and a
  privacy text of their own that describes their hosting and what they
  process. Not done here because it is outside this repository.
