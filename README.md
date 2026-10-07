# CPM Video Converter (browser edition)

Static web page. Conversion runs inside each visitor's browser with ffmpeg.wasm — no server, no uploads, no cost per use.

## Test on your PC first
Must be opened via http (not by double-clicking `index.html`). In this folder:
- Python: `python -m http.server 8080`  → open http://localhost:8080
- or Docker: `docker run --rm -p 8080:80 -v "%cd%":/usr/share/nginx/html:ro nginx`

## Put it online for the team (free static hosting)
Upload the whole folder (index.html + vendor/) to any static host, e.g.:
- **Netlify Drop**: drag the folder onto app.netlify.com/drop
- **Cloudflare Pages**: Create project → Direct Upload → upload the folder
- **GitHub Pages**: push the folder to a repo → Settings → Pages

Share the resulting link with the team. Check the host's free-plan limits.

## Limits
- Best for clips up to ~1 GB (hard stop ~1.6 GB); RAM of the user's PC matters.
- "Fast" mode copies the video stream when possible (seconds); otherwise it re-encodes with x264 in WebAssembly (slow, roughly real-time or slower for big/HD files).
- Files are converted one at a time. Keep the tab open.
- DAV works only if FFmpeg can decode that DVR's format; otherwise you get an "Unsupported/proprietary DAV" message.

Includes FFmpeg (ffmpeg.wasm / @ffmpeg/core, GPL build with x264) — see vendor/core/LICENSE.
