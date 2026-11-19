# EURO GAMEPLAY BOOSTER

A browser-based gameplay-video enhancer. It processes the selected video locally in the browser; the source video is not uploaded to the Cloudflare Worker.

## Current features

- Import a local video file.
- Preview with WebGL2 image adjustments: sharpening, contrast, saturation, vibrance and brightness.
- Presets for gaming, vivid, natural and cinematic looks.
- Trim start/end points.
- Export MP4 using browser WebCodecs (H.264; AAC audio when the browser can decode and encode it).
- Output framing for vertical short-form video, landscape video, or original dimensions.
- Optional experimental motion-estimation frame interpolation. This is a GPU block-search heuristic, NOT an AI model and NOT true optical-flow interpolation. Inspect the result for ghosting or artifacts.

## Requirements and limitations

- Use a recent Chrome or Edge browser with WebGL2, VideoEncoder, VideoFrame, and (for audio) AudioEncoder support.
- Video decoding/encoding runs on the user's device. Performance, supported resolutions, codecs, memory use and export time depend on the phone/PC and browser.
- Large or high-resolution files may fail on phones due to memory or hardware encoder limits. Start with a short 720p/1080p clip.
- The browser tab must remain open during export.
- No server-side video rendering, AI enhancement, guaranteed FPS increase, or guaranteed quality improvement is provided.
- This tool improves recorded video appearance and format; it does not change the live game's FPS, ping, graphics settings, or device performance.

## Deploy

GitHub Actions validates the static app and deploys it to Cloudflare Workers Static Assets.

1. In the GitHub repository, open Settings > Secrets and variables > Actions.
2. Add CLOUDFLARE_API_TOKEN with a Cloudflare API token that has Account / Workers Scripts / Edit permission for the account configured in wrangler.toml.
3. Push to main or run Deploy Cloudflare manually from the Actions tab.

The Worker name is gameplay-booster. The static site is served from the public/ directory created by the workflow.

## Development

The app is a single index.html using WebGL2 and browser WebCodecs. No backend is needed for local video processing.

## Licensing

No license file is currently included. Unless a license is added, the repository is not granted an open-source reuse license.