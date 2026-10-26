# nexumia.de

The homepage at <https://nexumia.de/>: one static page that points to
the Nexumia couch games at <https://games.nexumia.de/> and to the apps
for Linux phones at <https://flatpak.nexumia.de/>.

Plain HTML and CSS, no build step, no JavaScript, no external requests:
the fonts (Figtree, Bricolage Grotesque) are served from `site/assets/fonts/`.
Colours, type and the couch mark follow the Nexumia visual system in
LocalGameGalaxy's `DESIGN.md`; the logo and game-area icons are copied
from its `design/brand/`, the Cirro icon from the cirro repository.

## Layout

- `site/`: everything that is published (`index.html`, `404.html`, `style.css`, `assets/`).
- `wrangler.jsonc`: Cloudflare Worker `nexumia-homepage`, static assets only, custom domains `nexumia.de` and `www.nexumia.de`.
- `.github/workflows/deploy.yml`: deploys on every push to `main`; pull requests get a preview URL.

## Preview locally

```sh
python3 -m http.server -d site 8000
# or, exactly as Cloudflare serves it:
npx wrangler@4.151.3 dev
```

Check the page at 360 px width and at a desktop size, in light and dark
mode.

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
5. **Deploy.** Push to `main` (or Actions → *Deploy* → *Run workflow*).
   Wrangler creates the Worker, the DNS records and the certificates for
   `nexumia.de` and `www.nexumia.de` itself.
6. **Check.** Workers & Pages → `nexumia-homepage` → Settings → Domains
   & Routes lists both domains; <https://nexumia.de/> shows the page
   after a minute or two.

Without a domain the Worker is also reachable at
`https://nexumia-homepage.<your-subdomain>.workers.dev`.

## Support

The apps are free. If you want to support their development, you can do
so on [Liberapay](https://liberapay.com/suitably).

## Licence

Code and text: GNU Affero General Public License v3.0 or later. Fonts:
SIL Open Font License 1.1. See `REUSE.toml` and `LICENSES/`. The licence does not grant the right to use the name
Nexumia or its logo for other projects.
