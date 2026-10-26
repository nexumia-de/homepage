# nexumia.de

The homepage at <https://nexumia.de/>: one static page that points to
the Nexumia couch games at <https://games.nexumia.de/> and to the apps
for Linux phones at <https://flatpak.nexumia.de/>.

Plain HTML and CSS, no build step, no JavaScript, no external requests:
the fonts (Figtree, Bricolage Grotesque) are served from `assets/fonts/`.
Colours, type and the couch mark follow the Nexumia visual system in
LocalGameGalaxy's `DESIGN.md`; the logo and game-area icons are copied
from its `design/brand/`, the Cirro icon from the cirro repository.

## Preview

```sh
python3 -m http.server -d . 8000
```

Check the page at 360 px width and at a desktop size, in light and dark
mode.

## Publish

`.github/workflows/pages.yml` deploys the page to GitHub Pages on every
push to `main`. One-time setup:

1. Settings → Pages → Source: *GitHub Actions*.
2. DNS for `nexumia.de`: `A` records to `185.199.108.153`,
   `185.199.109.153`, `185.199.110.153`, `185.199.111.153` (and the
   `AAAA` records `2606:50c0:8000::153` … `2606:50c0:8003::153`).
3. Settings → Pages → Custom domain: `nexumia.de` (the `CNAME` file sets
   it as well), then *Enforce HTTPS*.

## Support

The apps are free. If you want to support their development, you can do
so on [Liberapay](https://liberapay.com/suitably).

## Licence

Code and text: MIT. Fonts: SIL Open Font License 1.1. See `REUSE.toml`
and `LICENSES/`. The licence does not grant the right to use the name
Nexumia or its logo for other projects.
