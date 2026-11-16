# USB-Stick-Checkliste

Ordner und Dateien, die ein USB-Stick für PS4 und PS5 typischerweise braucht. Teil der inoffiziellen consolecheat-Werkzeuge rund um [consolecheat.com](https://consolecheat.com). German is the primary language, English is the other. Light and dark theme, self-hosted fonts, footer, Impressum, and Datenschutz are included. There is no Webmail link.

No account, no tracking, nothing uploaded. Fonts (Outfit, Source Sans 3) are self-hosted from `@fontsource`, so the page makes no request to Google or any other third party. The Impressum fields are placeholders until the operator fills them in. No name or address was invented.

Site: <https://robfreak.github.io/consolecheat-ex12/>

Inoffiziell. Nicht von Sony.

## What it does

A local checklist for the folders and files a USB stick typically needs on a PS4 and a PS5. Open it at `/consolecheat-ex12/`. German is the default. English is the other language. Light and dark follow `consolecheat-theme`.

Tabs are **PS4**, **PS5**, and **Beide** (English: **Both**). Each row is a checkbox. The progress line counts the visible rows (`2 von 13`). **Text herunterladen** and **Markdown herunterladen** build a file in the browser from the current checks. **Text kopieren** and **Markdown kopieren** use the clipboard when the browser allows it. The plain-text export stays on the page as a preview. **Haken leeren** clears the ticks and writes an empty list.

The page does not read the stick. There is no file dialog, no USB device API, and no scan of the drive. FAT32 and exFAT are named the way Sony support names them for media and for a system update. That is not a certification of the stick. Folder names Sony support publishes (`Music`, `PS4/UPDATE/PS4UPDATE.PUP`, `PS5/UPDATE/PS5UPDATE.PUP`) are marked **Sony-Hilfe**. Anything less certain, including `AV_CONTENTS` (an internal console folder, not a USB media folder) and capture folders the console writes itself, is marked **Prüfen**: verify on your console / official Sony support. Extended storage is a separate section. It is a drive the console formats, not a folder you create on this stick.

Checks and the chosen console stay in this browser under `localStorage` key `consolecheat-usb-checks-v1` (`version` 1, `console`, `checked`). The key is written when you tick a row, switch the console, or clear the checks. A missing key is not created until then. A value that does not parse, or a different version, is left untouched until you change something. Clearing the checks writes an empty list. Removing the key, together with `consolecheat-lang` and `consolecheat-theme`, is the button on the Datenschutz page. Language and appearance reuse those two shared keys.

## Storage

- `consolecheat-usb-checks-v1` (localStorage)
- `consolecheat-lang` and `consolecheat-theme` (localStorage, shared with the other consolecheat tools on robfreak.github.io)

The Datenschutz page has a button that removes this page's keys. Nothing else is stored.

## Run and test

```bash
npm install
npm test        # node --experimental-strip-types --test src/usb/*.test.ts
npm run dev     # http://127.0.0.1:5173/consolecheat-ex12/
npm run build   # typecheck, Vite build (base /consolecheat-ex12/), offline check of dist/
npm run preview # http://127.0.0.1:4173/consolecheat-ex12/
```

Node `>=22.6` (`package.json` `engines`).

## Files

- `index.html` — the HTML entry (Vite input)
- `src/usb/` — React + TypeScript source, styles, and tests
- `src/usb/tools.ts` + `src/usb/tool-links.tsx` — the footer list **Weitere Werkzeuge** (keep it identical across the consolecheat repos)
- `public/` — `favicon.svg`, `FONT-OFL.txt`, `.nojekyll`
- `scripts/check-dist.mjs` — offline check of `dist/` (no third-party hosts, no `.woff` fallback, woff2 fonts present)
- `.github/workflows/pages.yml` — test, build, and deploy to `gh-pages`

## Other tools

The footer group **Weitere Werkzeuge** (English: **Other tools**) links to the other consolecheat tools: Title-ID-Finder (ex1), PS-Plus-Archiv (ex2), Controller-Tester (ex3), Save-Info-Leser (ex4), Fehlercode-Nachschlager (ex5), the [Spiele-Merkliste](https://robfreak.github.io/consolecheat-ex6/), and [Bildschirm-Test](https://robfreak.github.io/consolecheat-ex7/), [Download-Zeit-Rechner](https://robfreak.github.io/consolecheat-ex8/), [Tastenbelegung](https://robfreak.github.io/consolecheat-ex9/), [HDR/Helligkeit](https://robfreak.github.io/consolecheat-ex10/), [Audio-Kanal-Test](https://robfreak.github.io/consolecheat-ex11/), [Combo-Trainer](https://robfreak.github.io/consolecheat-ex13/), [Sprite-Animator](https://robfreak.github.io/consolecheat-ex14/). These are ordinary links. The page does not request those sites.

This tool was moved here from [Robfreak/consolecheat-ex6](https://github.com/Robfreak/consolecheat-ex6).

## GitHub Pages

`.github/workflows/pages.yml` runs install, test, and build on pull requests and on every push. A push to `main` also pushes `dist/` to the orphan branch `gh-pages` (`peaceiris/actions-gh-pages`, Jekyll off). Vite `base` is `/consolecheat-ex12/`, which matches the project site <https://robfreak.github.io/consolecheat-ex12/>.

Enable once in the repository settings:

1. **Settings → Actions → General → Workflow permissions → Read and write permissions.** Save.
2. **Settings → Pages → Build and deployment → Source: Deploy from a branch.** Branch: **`gh-pages`**, folder: **`/ (root)`.** Save.

After that, every push to `main` updates the site.

## Credits

Outfit and Source Sans 3 are bundled from `@fontsource` under the SIL Open Font License; see `public/FONT-OFL.txt` and `THIRD_PARTY_NOTICES.md`.

Replace the Impressum placeholders with the operator’s real details before treating that page as a legal notice.
