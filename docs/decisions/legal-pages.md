---
type: Decision Record
title: Legal notice and privacy notice
description: The homepage carries one legal notice (Impressum) for all nexumia.de sites and a privacy notice for nexumia.de only; the owner's identity stays a marked placeholder until the owner fills it in.
tags: [decision, legal, impressum, privacy, gdpr]
generated: { by: claude-code/2, at: 2026-11-22T00:00:00Z }
sources:
  - id: ddg5
    resource: https://www.gesetze-im-internet.de/ddg/__5.html
    title: § 5 DDG, Allgemeine Informationspflichten
  - id: mstv18
    resource: https://www.gesetze-bayern.de/Content/Document/MStV-18
    title: § 18 MStV, Informationspflichten und Auskunftsrechte
  - id: gdpr13
    resource: https://eur-lex.europa.eu/eli/reg/2016/679/oj
    title: Regulation (EU) 2016/679 (GDPR), Art. 13
  - id: cf-privacy
    resource: https://www.cloudflare.com/privacypolicy/
    title: Cloudflare privacy policy
---

# Status

Accepted (2026-11-22), decided by the agent on the owner's instruction
to settle issue #2 by best practice. Not legal advice.

# Context

Issue #2 asked for an Impressum and a privacy notice and left one
question open: do games.nexumia.de and flatpak.nexumia.de link to the
same pages or need their own? The issue's text was written when the
site was on GitHub Pages and had a Liberapay link; it is now on
Cloudflare Workers and has no support link.

§ 5 DDG requires provider details for digital services offered
"geschäftsmäßig, in der Regel gegen Entgelt";[^ddg5] § 18 MStV
requires name and address for sites that do not serve purely personal
or family purposes.[^mstv18] A public project site that distributes
apps is not purely personal, the apps link a support page, and a
missing notice is a common ground for warning letters. The GDPR
requires information on processing wherever personal data is
processed, and an IP address reaching the host is personal
data.[^gdpr13]

# Decision

1. **Provide both pages** (`site/imprint.html`, `site/privacy.html`),
   linked from the footer of every page as "Imprint" and "Privacy".
   The cost is one page each; arguing that the duty does not apply
   saves nothing and carries the risk.
2. **One legal notice for all sites.** The provider is the same person
   for nexumia.de, games.nexumia.de and flatpak.nexumia.de, so the
   notice names all three and the other sites link to
   `https://nexumia.de/imprint`. One place to keep correct.
3. **Privacy notices per site.** What is processed differs: this site
   is static on Cloudflare Workers; the games run code, connect phones
   peer to peer and are hosted separately; the Flatpak repository is on
   GitHub Pages. Each site describes its own processing; this
   repository's notice covers nexumia.de only and says so in its links
   section.
4. **The privacy text states only what the site really does**: request
   data processed by Cloudflare[^cf-privacy] (legal basis Art. 6 (1) (f)
   GDPR), no cookies, no scripts, no analytics, no third-party
   requests, outbound links, email contact, the rights of Art. 15–21
   and 77. A change to any of that changes the page in the same commit
   (rule in `AGENTS.md`).
5. **The owner's identity is never invented.** Name, address and
   contact are placeholders marked `data-owner-todo`, visible on the
   page with a notice that it is incomplete; CI prints a warning while
   one is left and does not fail. The owner fills them in
   ([owner checks](../owner-checks.md)).
6. Both pages are `noindex`: they must be reachable from every page,
   not findable by a search for the owner's name.
7. Pages are in English like the rest of the site; the heading carries
   the German word "Impressum" so that the page is recognisable.

# Consequences

- Until the owner fills in the placeholders, the published legal
  notice is visibly incomplete. That is honest, but it does not meet
  § 5 DDG; the owner should fill it in before or right after merging.
- games.nexumia.de (LocalGameGalaxy) and flatpak.nexumia.de
  (phosh-apps) each need a footer link to the legal notice and their
  own privacy text; that work is outside this repository and listed in
  the owner checks.
- Turning on Cloudflare Web Analytics, logs or any script makes the
  privacy notice wrong.

[^ddg5]: § 5 DDG, Allgemeine Informationspflichten
[^mstv18]: § 18 MStV, Informationspflichten und Auskunftsrechte
[^gdpr13]: Regulation (EU) 2016/679 (GDPR), Art. 13
[^cf-privacy]: Cloudflare privacy policy
