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

Runs as the `markdown` PM2 app on port 2110 and appears as a tile on the landing
hub. Reachable behind the gateway at `/markdown/`. `server.js` simply serves
`index.html` — there is nothing to configure.

## Run locally

```sh
node server.js
```

Then visit http://localhost:2110

## Deploy to GitHub Pages

Pure static, no build step. Put `index.html` at a repo root, push, then
Settings → Pages → Deploy from a branch → `main` / root. Live at
`https://<user>.github.io/<repo>/`.
