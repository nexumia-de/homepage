@../phosh-toolkit/agents/core.md

# nexumia.de homepage

Static site in `site/` (plain HTML and CSS, no build step, no
JavaScript, no external requests), deployed to Cloudflare Workers.
Knowledge: [docs/index.md](docs/index.md).

- Keep it static: no JavaScript, no cookies, no third-party requests.
  Anything that changes what a visitor's browser sends or what is
  stored changes `site/privacy.html` in the same commit.
- Full check before a push ([docs/checks.md](docs/checks.md)):

  ```sh
  reuse lint
  ```

  ```sh
  npm --prefix tools ci
  ```

  ```sh
  npm --prefix tools run check
  ```

- The CI job `check` is the required status check in
  `.github/rulesets/main.json`; rename both together.
- Never invent the owner's name, address or contact data. What only
  the owner can do goes into [docs/owner-checks.md](docs/owner-checks.md).
- Check pages at 360 px width and at a desktop size, light and dark.

Agents without import support read `../phosh-toolkit/agents/core.md`
themselves (phosh-toolkit checked out next to this repository).
