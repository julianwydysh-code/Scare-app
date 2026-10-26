# Scare-app

Computer vision demo: a full-screen mirrored webcam with MediaPipe face tracking (green dots) and a scare meter.

Live: https://julianwydysh-code.github.io/Scare-app/

## Files

| File | Purpose |
| --- | --- |
| `wrangler.toml` | Cloudflare Worker config; serves the `public/` folder |
| `public/index.html` | The whole app: webcam, MediaPipe Face Landmarker, scare meter, controls |
| `.github/workflows/pages.yml` | Publishes `public/` to GitHub Pages on every push to `main` |

## Controls

| Button | Key | Action |
| --- | --- | --- |
| Face dots | `D` | Toggle green face-landmark dots |
| Flip | `M` | Toggle mirror |
| Snapshot | | Save a PNG (includes dots) |
| Fullscreen | `F` | Toggle fullscreen |

## Scare meter

The bar on the right averages three readings, each 0-100: left eye openness, right eye openness, and mouth openness.
Openness is measured from face landmarks (height / width), so it works at any distance from the camera.
Tune it with `EYE_MIN`, `EYE_MAX`, `MOUTH_MIN`, `MOUTH_MAX`, and `SMOOTH` near the top of the script.

## Deploy

**GitHub Pages:** automatic on every push to `main` (see the workflow).

**Cloudflare Worker (optional):**
Cloudflare dashboard → Workers & Pages → Create → Import a repository → `Scare-app`.
Every push to `main` redeploys. Open the `*.workers.dev` URL and allow camera access (HTTPS required).

## Run locally

```sh
npx wrangler dev
```

Then open http://localhost:8787. MediaPipe and the face model load from CDN, so an internet connection is needed.
