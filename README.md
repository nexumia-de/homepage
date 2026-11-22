# nexumia.de

The homepage at <https://nexumia.de/>: one static page that points to
the Nexumia couch games at <https://games.nexumia.de/> and to the apps
for Linux phones at <https://flatpak.nexumia.de/>.

Plain HTML and CSS, no build step, no JavaScript, no external requests:
the fonts (Figtree, Bricolage Grotesque) are served from `site/assets/fonts/`.
Colours, type and the couch mark follow the Nexumia visual system in
LocalGameGalaxy's `DESIGN.md`; the logo and game-area icons are copied
from its `design/brand/`. The app icons are copied from each app's
repository (`data/icons/`); Nuntius still uses Fractal's icon, so the
page shows its own neutral chat icon (`site/assets/nuntius.svg`).

## Layout

- `site/`: everything that is published (`index.html`, `404.html`, `style.css`, `assets/`).
- `wrangler.jsonc`: Cloudflare Worker `nexumia-homepage`, static assets only, custom domains `nexumia.de` and `www.nexumia.de`.
- `.github/workflows/deploy.yml`: job `check`, then the deploy on every push to `main`; pull requests get a preview URL.
- `tools/`: pinned tools for the checks and the deploy (`package.json`); not published.
- `docs/`: knowledge bundle, entry `docs/index.md`; what only the owner can do is in `docs/owner-checks.md`.
- `AGENTS.md`: rules for coding agents; it imports the shared rules from a phosh-toolkit checkout next to this repository.

## Preview locally

```sh
python3 -m http.server -d site 8000
# or, exactly as Cloudflare serves it (after `npm --prefix tools ci`):
npm --prefix tools exec -- wrangler dev
```

Check the page at 360 px width and at a desktop size, in light and dark
mode.

## Checks

CI runs the job `check` before every deploy: licences (REUSE), valid
HTML, internal links and assets, and the Worker configuration. Locally:

```sh
reuse lint
npm --prefix tools ci
npm --prefix tools run check
```

Details: `docs/checks.md`.

## Publish on Cloudflare Workers

Hosted like games.nexumia.de (LocalGameGalaxy): GitHub Actions runs
`wrangler deploy` with `cloudflare/wrangler-action`. One-time setup:

1. **API token.** Cloudflare dashboard → My Profile → API Tokens →
   *Create Token* → template *Edit Cloudflare Workers*. Account
   resources: your account; zone resources: *Specific zone* →
   `nexumia.de`. The token LocalGameGalaxy uses works too if it covers
   the `nexumia.de` zone.
2. **Account ID.** Dashboard → Workers & Pages → right-hand side
   *Account ID*.
3. **Repository secrets.** GitHub → `nexumia-de/homepage` → Settings →
   Secrets and variables → Actions → *New repository secret*:
   `CLOUDFLARE_API_TOKEN` and `CLOUDFLARE_ACCOUNT_ID`.
4. **Free the domain.** A custom domain needs the hostname to have no
   DNS record yet. Cloudflare dashboard → `nexumia.de` → DNS → Records:
   delete any `A`, `AAAA` or `CNAME` record for `nexumia.de` (`@`) and
   `www`. Leave `games`, `flatpak` and mail records (`MX`, `TXT`) alone.
5. **Deploy.** Push to `main` (or Actions → *Check and deploy* → *Run workflow*).
   Wrangler creates the Worker, the DNS records and the certificates for
   `nexumia.de` and `www.nexumia.de` itself.
6. **Check.** Workers & Pages → `nexumia-homepage` → Settings → Domains
   & Routes lists both domains; <https://nexumia.de/> shows the page
   after a minute or two.

Without a domain the Worker is also reachable at
`https://nexumia-homepage.<your-subdomain>.workers.dev`.

## Licence

Code and text: GNU Affero General Public License v3.0 or later. Fonts:
SIL Open Font License 1.1. See `REUSE.toml` and `LICENSES/`. The licence does not grant the right to use the name
Nexumia or its logo for other projects.
