# coop-replay-web

Link: https://coop-replay-web.firlin123.workers.dev/

A modified copy of https://replayweb.page/ to support **Godot 4 games** working inside web archives (`.warc`/`.wacz`).

### The Problem
The official `replayweb.page` doesn't serve COOP/COEP headers. Because Godot 4 web exports use multi-threaded WebAssembly, they require `SharedArrayBuffer`, which browsers instantly block without those headers. 

### The Fix
I ripped the static assets straight from the official ReplayWeb.page site, tossed them into the `public/` folder, and added a Cloudflare `_headers` file to force-inject the required headers:

```http
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Embedder-Policy: require-corp
```

Now Godot 4 games actually boot up when you view them.

---

## How to use it

### 1. Install

```bash
npm install
```

### 2. Run locally

```bash
npm run dev
```

### 3. Deploy to Cloudflare Pages

```bash
npm run deploy
```
