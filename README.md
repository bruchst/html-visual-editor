# HTML Visual Editor

A tiny, no-dependency web app to **paste an HTML page, edit it visually, and download the result.**

Built for editing single-file HTML decks and prototypes without learning a CMS or signing up to anything.

## Features

- **Paste or open** any HTML file — sample, file picker, drag-paste, or shared link.
- **Live preview** on the right; the source code stays on the left and the two stay in sync.
- **Click any text** in the preview while edit mode is on, change it, and the edit lands back in the source automatically.
- **Download** the edited HTML as a new file. No upload, no account, no server.
- **Share link** for small snippets (up to ~25 KB raw HTML, ~32 KB URL): compresses the HTML into a URL hash so anyone with the link sees your version. The hash never leaves the browser.
- **Keyboard shortcuts**: `E` toggle edit, `Cmd/Ctrl+S` download, `Cmd/Ctrl+O` open file.
- Works offline once loaded. No tracking, no analytics, no cookies.

## Limits

- External images/fonts/stylesheets referenced by **relative** paths won't load in the preview iframe — they will work again when you put the downloaded file back into its original folder.
- Share links work up to ~32 KB URL (~25 KB raw HTML, ~20 KB compressed). Anything bigger goes through **Download**.
- Edits inside `<script>` and `<style>` tags must be done in the source pane on the left.
- Generic `<div>` elements are deliberately not made editable to avoid making whole containers click-into-edit. Add `data-editable="true"` to any element you want to opt in.

## Run locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

That's it — no build step. The only runtime dependency is [LZ-String](https://github.com/pieroxy/lz-string) loaded from jsDelivr with an SRI hash for integrity.

## Deploy

This is a single static HTML file. Push to GitHub and import to [Vercel](https://vercel.com/new) — zero config.

```bash
gh repo create html-visual-editor --public --source=. --push
# then point Vercel at the repo
```

## License

MIT.
