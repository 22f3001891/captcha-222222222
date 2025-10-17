# Captcha Solver (Client-side OCR)

## Overview
This is a single-file web app that solves simple captcha images entirely in the browser. It:
- Accepts an image URL via the `?url=` query parameter.
- Displays the provided captcha image.
- Preprocesses the image (upscaling, grayscale, Otsu binarization, de-speckling).
- Runs OCR using Tesseract.js with tuned settings to extract alphanumeric text.
- Aims to display the solved text within 15 seconds.

To avoid CORS issues when loading external images, the app proxies images through `images.weserv.nl` automatically (no server required).

## Setup
No build step needed.

- Option 1: Double-click `index.html` to open it in a modern browser.
- Option 2: Serve it via any static server (recommended):
  - Python: `python3 -m http.server 8080`
  - Node: `npx serve .`

The app pulls Tesseract.js from a CDN.

## Usage
- Provide your captcha image URL in the query string:
  - Example: `index.html?url=https://example.com/sample.png`
- The page will:
  1. Echo the provided URL.
  2. Load and display the captcha (via a CORS-safe image proxy).
  3. Preprocess the image and run OCR.
  4. Show the solved text and timing information.

You can also paste a URL into the input field and click “Solve”.

Notes:
- For best results, captchas consisting of uppercase letters and digits are supported; the OCR is biased toward `A–Z` and `0–9`.
- If your image host blocks hotlinking or has unusual CORS rules, the proxy should still work. Data URLs also work directly.

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

THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE
OR OTHER DEALINGS IN THE SOFTWARE.