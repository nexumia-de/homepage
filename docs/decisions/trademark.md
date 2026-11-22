---
type: Decision Record
title: No trademark registration for now
description: "Nexumia" and the couch logo are not registered as trademarks for now; the READMEs and the legal notice say that the code licences do not cover them, and named events reopen the question.
tags: [decision, trademark, name, logo, legal]
generated: { by: claude-code/2, at: 2026-11-22T00:00:00Z }
sources:
  - id: dpma-fees
    resource: https://www.dpma.de/english/services/fees/trade_marks/index.html
    title: DPMA, trade mark fees
  - id: euipo-fees
    resource: https://www.euipo.europa.eu/en/trade-marks/before-applying/fees-payments
    title: EUIPO, fees and payments for EU trade marks
  - id: markeng
    resource: https://www.gesetze-im-internet.de/markeng/
    title: Markengesetz (§§ 4, 5, 15)
---

# Status

Accepted (2026-11-22), decided by the agent on the owner's instruction
to settle issue #3 by best practice. Not legal advice; the owner can
overrule it at any time by filing an application.

# Context

The code is AGPL-3.0-or-later. A code licence does not protect the
name "Nexumia" or the couch logo; the READMEs only say that the
licence does not grant their use. Issue #3 asked whether to register
a word mark (classes 9 and 41) and what to do until then.

- Cost: a German mark at the DPMA is 290 € for ten years with up to
  three classes when filed online;[^dpma-fees] an EU mark at the EUIPO
  is 850 € for one class, 50 € for the second and 150 € for each
  further one.[^euipo-fees] A search and a lawyer cost extra, and a
  mark only helps if the owner is willing to enforce it.
- Without registration the name is not unprotected in Germany: titles
  of software and games are protected as work titles from first use,
  and a sign can gain protection through use
  (§§ 4 no. 2, 5, 15 MarkenG).[^markeng] That protection is narrower
  and harder to prove.
- The project is small, free of charge and has no income beyond
  voluntary support. Nobody is known to imitate the name.
- The larger risk for an unregistered name is the other direction: an
  older mark of someone else that "Nexumia" collides with. A
  registration does not remove that risk; a search shows it.

# Decision

1. **Do not register a trademark now.** The cost and the duty to watch
   and enforce a mark are out of proportion to a free project without
   income and without a known conflict.
2. **Keep the note in the READMEs** and say the same on the site: the
   legal notice gets a section "Name and logo" (the footer of every
   page links to it; a line in the footer itself would add legal text
   to every page for no gain). No ® and no ™: nothing is registered.
3. **Reopen the question when one of these happens**: someone uses the
   name or logo for another project or a modified build; the apps go
   to Flathub or another store under the Nexumia name; the project
   starts to earn money beyond voluntary support; the name is to be
   used for hardware, merchandise or a company. Then file the word
   mark at the DPMA first (classes 9, 41 and 42 fit into the base
   fee), and an EU mark only if the audience outside Germany matters.
4. The owner runs one free identity search for older "Nexumia" marks
   ([owner checks](../owner-checks.md)); a hit changes this decision.

# Consequences

- No fee and no deadline now; the DPMA route stays open, since a mark
  can be filed at any time as long as nobody else registered the sign
  first.
- If someone registers "Nexumia" for similar goods first, the project
  would have to rely on its earlier use, which is weaker. Accepted.

[^dpma-fees]: DPMA, trade mark fees
[^euipo-fees]: EUIPO, fees and payments for EU trade marks
[^markeng]: Markengesetz (§§ 4, 5, 15)
