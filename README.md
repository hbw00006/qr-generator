# QR Code Generator (Static Page)

A simple static page that lets a user enter a URL, generates a QR code, displays it on the screen, and allows downloading it as a PNG.

Files:
- `index.html` — main static page. Uses QRious via CDN.

Quick usage:
1. Open `index.html` in a browser (double-click or serve from any static host).
2. Enter a URL including protocol (e.g. `https://example.com`).
3. Click "Generate".
4. QR code will appear. Click "Download PNG" to save the QR code image.

Example image
- Example QR image for `https://example.com` (served by Google Chart API):  
  https://chart.googleapis.com/chart?cht=qr&chs=300x300&chl=https://example.com

How to add to your repository (local workflow)
1. Clone your repo (if not already):
   git clone git@github.com:hbw00006/qr-generator.git
   cd qr-generator

2. Create and switch to a branch:
   git checkout -b qr-generator-ui

3. Add the files (create `index.html` and `README.md`) then:
   git add index.html README.md
   git commit -m "Add static QR code generator UI"
   git push -u origin qr-generator-ui

4. Open a PR from `qr-generator-ui` into your main branch in GitHub, review, and merge.

Test plan & expected results
- Tests to perform (manual):
  1. Open `index.html` in a desktop browser.
  2. Enter `https://example.com` and click Generate.
     - Expected: a 300×300 QR code appears on the page.
  3. Click "Download PNG".
     - Expected: a file named `qrcode.png` downloads. Opening it shows the same QR pattern as on screen.
  4. Scan the downloaded PNG (or the on-screen QR) using a phone camera / QR scanner app.
     - Expected: the scanner recognizes the QR and suggests opening `https://example.com`.
  5. Enter a non-URL or empty string and press Generate.
     - Expected: an alert prompts for a valid URL.
  6. Test with long URLs / query strings to ensure the QR still generates. (Very long URLs produce denser patterns; consider a shortener if scanning fails.)
  7. Test on mobile:
     - Open `index.html` in mobile browser (or host it and open the hosted URL). Generate a QR for a test link and scan it using a second phone or another app.

- Example verification checklist:
  - [ ] QR appears after clicking Generate.
  - [ ] Downloaded PNG opens and matches the on-screen QR.
  - [ ] Scanning opens the correct URL.
  - [ ] Clear button hides and clears the QR.

Notes and considerations
- The demo uses QRious (lightweight) that draws to canvas. The code uses canvas.toDataURL(...) to create the downloadable PNG.
- If you want server-side generation or higher-resolution images, we can add an endpoint that returns PNG/SVG or add an option to increase canvas size before rendering.
- For accessibility, the canvas is not inherently accessible; consider adding an adjacent text-only link to the encoded URL (if that's acceptable for your use-case).

If you'd like, I can:
- Add these files directly to the `qr-generator` repository on a new branch and open a pull request for you, or
- Add an alternate implementation that outputs an SVG (smaller file size and crisp scaling), or
- Add a small Node.js script to pre-generate QR images for a list of URLs.

Please tell me which of the above you want me to do next.
