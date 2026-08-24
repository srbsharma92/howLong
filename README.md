# Hold Counter

A single-page, no-build HTML app with one button and three live readouts:

1. **Last Hold** — how long the most recent press lasted
2. **Presses** — how many times the button has been pressed
3. **Cumulative Hold Time** — total time held, added up across every press this session

All state lives in browser memory (plain JavaScript variables), so it resets whenever the page is refreshed — no backend, database, or cookies involved.

## Run it locally

No build step. Just open the file:

```bash
open index.html      # macOS
# or
xdg-open index.html  # Linux
# or double-click it in Finder/Explorer
```

Or serve it locally if you prefer a real URL:

```bash
npx serve .
```

## Deploy to Cloudflare Pages

**Option A — Connect the GitHub repo (recommended, auto-deploys on push)**

1. Push this project to a GitHub repository (see below).
2. Go to the [Cloudflare dashboard](https://dash.cloudflare.com/) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
3. Select this repository.
4. Build settings:
   - **Framework preset:** None
   - **Build command:** (leave blank)
   - **Build output directory:** `/`
5. Click **Save and Deploy**. Cloudflare will give you a `*.pages.dev` URL, and every future push to `main` redeploys automatically.

**Option B — Direct upload (no GitHub needed)**

1. Go to **Workers & Pages** → **Create** → **Pages** → **Upload assets**.
2. Drag in this folder (or just `index.html`).
3. Deploy — you'll get a `*.pages.dev` URL immediately.

**Option C — Wrangler CLI**

```bash
npm install -g wrangler
wrangler pages deploy . --project-name=hold-counter
```

## Push this project to GitHub

```bash
cd button-press-tracker
git init
git add .
git commit -m "Initial commit: hold counter"
git branch -M main
git remote add origin https://github.com/<your-username>/<your-repo>.git
git push -u origin main
```

## Customizing

Everything lives in `index.html` — markup, styles, and script are all in one file for simplicity. Key spots:

- `formatSeconds()` — change how durations are displayed (e.g. add milliseconds, or always show `m:ss`).
- The CSS `:root` variables at the top of `<style>` — swap the palette.
- `resetBtn` handler — wire this to persist stats somewhere (e.g. `localStorage`, or a Cloudflare Worker + KV/D1) if you want counts to survive a refresh.

## License

MIT — see `LICENSE`.
