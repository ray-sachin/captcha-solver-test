# Captcha Solver (Client-side)

MIT-licensed, single-page app that loads a captcha image from a URL parameter and uses in-browser OCR (Tesseract.js) to estimate the captcha text. Defaults to an attached `sample.png`.

- URL parameter: `?url=https://.../image.png`
- Displays the passed captcha URL on the page
- Shows original and preprocessed images
- Solves and displays the recognized text, typically within 15 seconds
- Optional CORS proxy for cross-origin images

## Overview

This app is a lightweight captcha recognizer running entirely in the browser. It:
- Accepts an image URL via `?url=` query parameter (or uses `sample.png` by default).
- Uses basic image preprocessing (upscale + threshold + denoise).
- Runs Tesseract.js with the fast English dataset to extract text.
- Shows progress, confidence, and timing.

Because many image servers block cross-origin access, a built-in CORS proxy option is provided to fetch images reliably.

Note: This is for demo/educational purposes. Robust production captcha solving requires more advanced models and is often against site terms of service.

## Setup

No build steps are required.

- Place `index.html`, `README.md`, and the provided `sample.png` in the same directory (sample is referenced by default).
- Open `index.html` in any modern browser with internet access (to load Tesseract.js and language data via CDN).

## Usage

- Basic:
  - Open: `index.html`
  - It will auto-load and attempt to solve `sample.png` in the same directory.
- With a custom captcha URL:
  - Open: `index.html?url=https://example.com/path/to/captcha.png`
- CORS proxy options:
  - Default uses the cors.isomorphic proxy for cross-origin images.
  - To disable proxy: `index.html?url=...&proxy=0`
  - To force a specific proxy:
    - `&proxy=cors` (cors.isomorphic)
    - `&proxy=weserv` (images.weserv.nl)
- Advanced tuning:
  - `&psm=8` (page segmentation mode; 8=single word, 7=single line, 10=single char, etc.)
  - `&scale=3` (upscale factor for preprocessing)

On the page:
- The "Image URL param" field shows the exact URL you passed via `?url=...`.
- "Used source" shows the actual fetch URL (including proxy if enabled).
- You can adjust Scale and PSM for better results, then click "Solve Captcha".

## License

MIT License

Copyright (c) 2025

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.