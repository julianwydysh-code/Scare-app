# Scare-app

Computer vision demo: a full-screen mirrored webcam with MediaPipe face tracking (green dots), served by a Cloudflare Worker.

## Files

| File | Purpose |
| --- | --- |
| `wrangler.toml` | Cloudflare Worker config; serves the `public/` folder |
| `public/index.html` | The whole app: webcam, MediaPipe Face Landmarker, controls |

## Controls

| Button | Key | Action |
| --- | --- | --- |
| Face dots | `D` | Toggle green face-landmark dots |
| Flip | `M` | Toggle mirror |
| Snapshot | | Save a PNG (includes dots) |
| Fullscreen | `F` | Toggle fullscreen |

## Deploy

Cloudflare dashboard → Workers & Pages → Create → Import a repository → `Scare-app`.
Every push to `main` redeploys. Open the `*.workers.dev` URL and allow camera access (HTTPS required).

## Run locally

```sh
npx wrangler dev
```

Then open http://localhost:8787. MediaPipe and the face model load from CDN, so an internet connection is needed.
