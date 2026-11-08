# dslot-site

The DSlot website and its user manual, for the Anbernic RG DS+, from one set of Markdown
files, so the two never drift. DSlot is the game system: the shelf, the emulators, and the card
image that carries them on nibOS. nibOS, the Linux system underneath, has its own site and
manual at https://nibos.alanb.dev/ ([nibos-site](https://github.com/abradburne/nibos-site)),
built from the same templates; a change to the design goes into both. It's a static site: no scripts, no tracking, no cookies and no
requests to other sites. Light and dark follow the reader's setting. It uses DSlot's look:
DSlot's boot screen logo, Roboto Condensed (self-hosted, subset to Latin), near-black and gold, and DSlot's own
screenshots shown as they are, top screen over touch screen, with no device drawn around them.

```sh
brew install zola      # Zola 0.23 (one binary; https://www.getzola.org for other systems)
make                   # build into public/; every internal link and anchor is checked
make serve             # http://127.0.0.1:1111, rebuilt on every change
make check             # and every external link
```

## Layout

| Path | What |
|---|---|
| `content/_index.md` | The home page. Its front matter holds the words: the headline, the screenshots, the systems by maker, the notes, the install steps and the stack |
| `content/download.md` | The image, how to check it, release notes, licences, the source |
| `content/manual/` | The manual, one chapter per file, ordered by each file's `weight` |
| `content/apps.md` (Emulators and apps), `faq.md`, `contributing.md`, `licences.md` | The other pages |
| `zola.toml` | The site's settings, and the release: `[extra.release]` is the one place where a release's version, file, size, checksum and update key are written. The home and download pages read it. `nibos_site` is the nibOS site's address |
| `templates/` | The pages' HTML (Tera 2) and `404.html`; `components.html` holds the components: two-screen captures, screenshots, icons and the download cards |
| `static/` | The stylesheet, the font, the icon and the screenshots |
| `tools/rgds-plus.py` | The RG DS+ modelled in Blender, for the home page's render: `blender -b -P tools/rgds-plus.py -- --shot <capture.png> --out <render.png> --samples 256 --res 2000`. A capture is DSlot's `--shot`, headless, 1024 × 1536 |
| `.github/workflows/pages.yml` | Builds the site and publishes it on GitHub Pages |

## Publishing

The site lives at **https://dslot.alanb.dev/**. The workflow runs on every push to `main`, or
by hand from the Actions tab: it installs a pinned Zola release, checking its checksum, builds
the site and deploys it to GitHub Pages.

- **GitHub:** Settings → Pages → Source: **GitHub Actions**; Custom domain: `dslot.alanb.dev`;
  then **Enforce HTTPS** once GitHub has issued the certificate.
- **DNS:** a `CNAME` record `dslot` → `abradburne.github.io`.
- The address is written in two places, which must agree: `base_url` in `zola.toml` (links,
  the canonical link, the sitemap) and `static/CNAME`.

## A new release

DSlot's card image is built and published with each nibOS release, on nibOS's GitHub release, as
`dslot-<version>-rg-ds-plus.img.xz`; this site and the nibOS site change together.

1. In `zola.toml`, under `[extra.release]`, set the version, tag, date and commit, the image's
   size and SHA-256 (copied from the release's `SHA256SUMS`), and `published = true` once the
   files are on the release page.
2. Update the release notes in `content/download.md`.
3. Change the manual wherever behaviour has changed, and update Known issues.

## Writing

- Plain, precise English, to a reference standard. Describe what is true of the image a reader
  installs, and nothing that hasn't been run on a device.
- No comparisons with other firmwares or emulators. No ROMs, BIOS files or game artwork, in
  text or pictures. The screenshots are DSlot's own, with the made-up demo games DSlot draws. The
  `dslot-*.webp` captures and the render show those demo games with made-up box art and labels,
  generated for this site; the games don't exist.
- For engineering detail, link the projects' own documentation rather than repeating it.
- Links between pages take the form `@/manual/install.md#anchor`. Zola checks each one when it
  builds, so a renamed heading breaks the build rather than the site.
- Notes use GitHub's alert syntax (`> [!NOTE]`, `> [!WARNING]`), which renders on GitHub too.

## Licences

| | Licence |
|---|---|
| The screenshots (`static/img/*.png`) | From [DSlot](https://github.com/abradburne/DSlot)'s documentation, GPL-3.0-or-later. The games in them are DSlot's made-up demo titles and icons |
| The home page's render (`static/img/rgds-plus.webp`), its captures (`static/img/dslot-*.webp`) and the made-up game art in them | Made for this site: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/). The render is from `tools/rgds-plus.py` (Blender 5), MIT |
| Roboto Condensed (`static/fonts/`) | SIL Open Font License 1.1 ([OFL.txt](static/fonts/OFL.txt)), copyright 2011 The Roboto Project Authors; subset to Latin |
| The logo (`static/img/logo.svg`) and the icon made from it (`static/img/icon.svg`) | DSlot's boot screen logo, from nibOS's `rootfs/splash/pictures/logo.svg`; GPL-3.0-or-later |
| The text (`content/`) | [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) ([LICENSE-CC-BY-SA-4.0.txt](LICENSE-CC-BY-SA-4.0.txt)) |
| The templates, stylesheet (with the CSS-drawn device), `zola.toml`, `Makefile` and workflow | MIT ([LICENSE-MIT](LICENSE-MIT)) |

[LICENSE](LICENSE) says which licence covers which file.
