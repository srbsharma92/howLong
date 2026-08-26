# Hold Counter

A quiet, single-purpose timer: press and hold to time something, release to
log it. Rebuilt on Astro, restyled around a "dawn horizon" palette — calm,
professional, and forward-looking rather than the original arcade-console
look.

## Run it

```bash
npm install
npm run dev
```

Then open the local URL Astro prints (usually `http://localhost:4321`).

## Build for production

```bash
npm run build
npm run preview
```

## Structure

```
src/
  layouts/Layout.astro       shared HTML shell, fonts, global resets
  styles/global.css          CSS custom properties (design tokens) + resets
  components/HoldCounter.astro   the timer itself: markup, styles, logic
  pages/index.astro          renders the page
```

All state lives in memory in the browser tab — nothing is persisted or sent
anywhere. Refreshing or pressing "reset session" clears it.
