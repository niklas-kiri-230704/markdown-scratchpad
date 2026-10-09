# 📝 Markdown Scratchpad

A live-preview Markdown editor that runs entirely in the browser.

- Two-pane layout: editor on the left, rendered preview on the right (stacks / toggles on narrow screens)
- **Markdown renderer is pure inline JS** — no marked.js, no markdown-it, no libraries or CDNs
- Supports headings, bold/italic/inline-code, fenced code blocks, blockquotes, ordered + unordered (nested) lists, links, images, horizontal rules, paragraphs and line breaks
- All source text is HTML-escaped before transforming, and only http/https/relative/mailto links are allowed — the preview can never inject scripts
- **Autosave** to localStorage (debounced) and restore on load
- **Multiple named documents**: new / switch / delete, all in localStorage
- **Share via URL hash**: copy a link with the whole document base64-encoded in `location.hash` — no backend needed
- **Export** the document as a `.md` file, and **Copy HTML** of the rendered output
- Live word / character count

## In the homelab

Served on port 2110 by the shared `statics` process — not as a PM2 app of its
own. Seventeen single-file apps each having their own Node process cost ~33MB apiece, which is what got Termux OOM-killed on the phone; one process now serves them all. Appears as a tile on the landing hub and is reachable behind the
gateway at `/markdown/`. Nothing to configure.

`server.js` here is still what runs the app standalone (`npm start`) and on GitHub Pages; it is simply not what serves it on the phone.

## Run locally

```sh
node server.js
```

Then visit http://localhost:2110

## Deploy to GitHub Pages

Pure static, no build step. Put `index.html` at a repo root, push, then
Settings → Pages → Deploy from a branch → `main` / root. Live at
`https://<user>.github.io/<repo>/`.
