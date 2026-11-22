---
okf_version: "0.2"
---

# nexumia.de homepage knowledge bundle

An [Open Knowledge Format](https://github.com/GoogleCloudPlatform/knowledge-catalog/blob/main/okf/SPEC.md)
(OKF v0.2) bundle: one file per concept. Change history is in
[log.md](log.md). Shared rules and knowledge are in phosh-toolkit
(`../phosh-toolkit/agents/core.md`, `../phosh-toolkit/docs/`). How the
site is built, previewed and published is in the [README](../README.md).

# Workflows

* [Checks before deploy](checks.md) - The CI job `check` (REUSE, HTML validation, internal links, Worker configuration), how to run it locally, the ruleset and Dependabot.
* [Dependencies](dependencies.md) - Every tool and action the repository uses, with version source and licence; nothing of it is shipped.
* [Owner checks](owner-checks.md) - What only the owner can do: settings, legal details, things to confirm.

# Decisions

* [Decision records](decisions/index.md)
