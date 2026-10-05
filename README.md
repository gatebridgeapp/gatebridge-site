# Gatebridge website

Marketing site for [Gatebridge](https://gatebridge.app) (`gatebridge.app`), built with [Astro](https://astro.build).

Product/protocol source lives in [fido2-android-bridge](https://github.com/andreparames/fido2-android-bridge). This repo is only the static site and its GitHub Pages pipeline.

## Quick start

```bash
# Requires Node.js 22+
npm install
npm run dev        # http://localhost:4321
npm run build      # static output to dist/
npm run preview    # preview the production build
```

## Deploy

Push to `main` → GitHub Actions builds and deploys to GitHub Pages.

Custom domain: `gatebridge.app` (HTTPS enforced). Configured in repo Settings → Pages.

## Plan

See [`WEBSITE_PLAN.md`](./WEBSITE_PLAN.md) for structure, style, and funnel notes.

## Related

- [fido2-android-bridge](https://github.com/andreparames/fido2-android-bridge) — daemon, Android app, protocol
- [gatebridge.app](https://gatebridge.app) — live site
