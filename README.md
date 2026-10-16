# Sankeet Shayak — frontend (backend-ready)

The original site (intro, hero, pipeline, physics, credits) is unchanged. This version adds a
**honest, backend-ready** demo: camera preview, recognition results, translation, speech, live
landmarks, live motion graphs, session history and a connection-status panel.

## Run it
```bash
python3 -m http.server 8080        # or: node tests/serve.js 8080
# open http://localhost:8080  (camera needs https:// or localhost)
```
No build step, no dependencies.

## Connect the backend  → edit **`js/config.js`** (the only place)
```js
backend: { baseUrl: 'http://localhost:8000', transport: 'http' /* | 'websocket' | 'sse' */ }
```
Contract and examples: **`docs/BACKEND_API.md`**. A runnable stand-in server: `node tests/fake-backend.js 8000`.

## Demo without a backend (development only)
`mode: 'mock'` in `js/config.js` (or `?mock=1` on localhost), then press **Run demo data**.
Deterministic sequence, labelled **DEMO DATA** everywhere, never used in `real` mode, and
`js/mock-backend.js` is not even loaded unless mock mode is on.

## Tests
```bash
node --test tests/unit.test.js                         # contract, analytics, adapter (no browser)
NODE_PATH=$(npm root -g) node tests/browser.test.js    # real Chromium: needs `playwright` + a Chromium build
```
