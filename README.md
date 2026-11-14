# Insta Export

Turn any video (4K, 1080p, phone, camera, any format your browser can play) into an Instagram-ready master. Everything runs in the browser on your own device — the video is never uploaded anywhere.

## Use it

Open `index.html` in Chrome or Edge, or host it (below) and open the link on your phone.

1. Choose a video. It is analysed against Instagram's published spec.
2. **Auto** picks resolution, frame rate, bitrate and audio for that video and explains why. **Manual** unlocks every setting.
3. Export, then Save (or Share straight to Instagram on a phone).

## Colour looks (LUTs)

Add your own 3D `.cube` LUTs with **Add .cube** (or drop them on the page). Pick one, set its **Power** from 0–100%, and check it on the live preview — **Show original** flips back for comparison. The LUT is baked into the export. Your LUTs are saved in that browser, so they are there next time; each device keeps its own list.

If a file already meets the spec, Auto does a **lossless rewrap** instead of re-encoding — zero quality change.

## Put it on GitHub Pages (free link for phone + laptop)

1. Create a new repository on github.com and upload `index.html` and the `vendor` folder (keep the folder structure).
2. In the repository: **Settings → Pages → Source: Deploy from a branch → main → / (root) → Save**.
3. After a minute your link is `https://<your-username>.github.io/<repo-name>/`.

## What it exports

| Setting | Auto value |
|---|---|
| Container | MP4, index at the front (fast start) |
| Video | H.264 High profile (HEVC optional where the device supports it) |
| Resolution | 1080p in the video's own shape — 1080×1920 for 9:16 |
| Frame rate | Kept if 23–30 fps; 50/60 → 25/30; always constant |
| Video bitrate | About 12 Mbps at 1080p30, scaled by size and frame rate, never above 25 Mbps |
| Audio | Original AAC copied untouched, otherwise AAC 48 kHz at the device's best bitrate |

Spec source: Meta's Instagram Platform documentation, "Reel specifications".

## Browser support

- **Best:** Chrome or Edge on Windows, Mac and Android.
- **iPhone/iPad:** Safari 17 or newer. Audio re-encoding needs a recent iOS; if it is missing the page tells you.
- Firefox can't encode AAC audio, so use it only for silent clips.

Very large exports are built in memory. On a phone, keep clips to a few minutes.

## Honest limits

- Instagram re-encodes every upload. This tool gives it the cleanest possible input; it cannot stop Instagram's own compression.
- HDR video is converted to standard range by the browser and colours can shift.
- Re-encoding uses your device's hardware encoder, not a studio encoder like x264. At these bitrates the difference is not visible after Instagram's own pass.

Encoding library: [Mediabunny](https://mediabunny.dev) (MPL-2.0), bundled in `vendor/`.
