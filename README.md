# HEICtoJPG

> Convert HEIC & WebP images to JPEG entirely in your browser. Zero server uploads. Zero privacy risks.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
![Static HTML](https://img.shields.io/badge/Stack-Static%20HTML-blue)
![No Server](https://img.shields.io/badge/Server-None-brightgreen)

---

## Demo

**Live site:** [heictojpg.com]([https://heictojpg.com](https://heic2jpg-online.netlify.app/))

Convert any HEIC (iPhone default) or WebP image to high-quality JPEG — instantly, privately, and for free.

---

## Features

- **100% Client-Side** — All conversion happens in your browser using WebAssembly and Canvas API. Files never leave your device.
- **HEIC Support** — Powered by `heic-to` (libheif WASM), supporting the latest HEIC/HEIF formats including multi-frame images.
- **WebP Support** — Uses native Canvas API for WebP-to-JPEG conversion.
- **Drag & Drop** — Intuitive drag-and-drop interface for a seamless user experience.
- **Real-time Preview** — See your image instantly after selecting a file.
- **Dark Premium UI** — Professional design with gold (#F5C518) accent and smooth animations.
- **SEO Optimized** — Structured data (JSON-LD), meta tags, sitemap, and clean URLs via `_redirects`.
- **Static Hosting Ready** — Deploy anywhere (Netlify, Cloudflare Pages, Vercel, GitHub Pages) with zero backend configuration.

---

## Tech Stack

| Layer | Technology |
|---|---|
| **Frontend** | Vanilla JavaScript (ES5+), HTML5, CSS3 |
| **HEIC Decoder** | [heic-to](https://github.com/hoppergee/heic-to) (libheif WASM v1.21+) |
| **WebP Decoder** | Canvas API (`Image` → `Canvas` → `toBlob`) |
| **Fonts** | Inter (Google Fonts) |
| **Hosting** | Static (Netlify / Cloudflare Pages) |

---

## Architecture

```
User selects HEIC/WebP file
        │
        ▼
  ┌─────────────────┐
  │  heic-to (WASM) │──── HEIC → raw pixels → JPEG Blob
  │  or Canvas API  │──── WebP → Image → Canvas → JPEG Blob
  └─────────────────┘
        │
        ▼
  ┌─────────────────┐
  │  Blob URL       │──── Preview in <img> tag
  │  Download link  │──── Trigger file download
  └─────────────────┘
```

No data is sent to any server. All processing is done locally using WebAssembly and browser APIs.

---

## Project Structure

```
heictojpg/
├── index.html              # Main converter page
├── about.html              # About page
├── contact.html            # Contact page
├── how-it-works.html       # How it works page
├── privacy.html            # Privacy policy
├── terms-of-service.html   # Terms of service
├── 404.html                # Custom 404 page
├── _redirects              # Clean URL routing (Netlify/Cloudflare)
├── static/
│   ├── sitemap.xml         # SEO sitemap
│   └── robots.txt          # Robots exclusion rules
└── README.md               # This file
```

---

## Getting Started

### Prerequisites

- A modern web browser (Chrome, Firefox, Safari, Edge)
- No server, no build tools, no dependencies required

### Local Development

No build step needed. Open `index.html` directly in your browser, or serve with any static file server:

```bash
# Using Python
python -m http.server 8080

# Using Node.js (npx)
npx serve .

# Using VS Code Live Server extension
# Right-click index.html → Open with Live Server
```

### Deployment

Deploy to any static hosting provider. Zero configuration required:

| Provider | Instructions |
|---|---|
| **Netlify** | Drag `index.html` + `_redirects` into deploy, or connect your GitHub repo |
| **Cloudflare Pages** | Connect your GitHub repo, framework preset = "None" |
| **GitHub Pages** | Push to `main` branch, enable Pages from root |

---

## Performance

- **HEIC → JPEG (12MP):** ~1–3 seconds on modern hardware
- **WebP → JPEG:** ~200–500ms (synchronous Canvas API)
- **Bundle size:** ~3.3 MB (heic-to WASM loaded lazily from CDN)
- **No framework overhead:** Pure vanilla JS, zero dependencies beyond the HEIC decoder

---

## Why Client-Side Conversion?

| Concern | Server-Side | Client-Side (This Project) |
|---|---|---|
| **Privacy** | Uploads to unknown servers | Stays on your device |
| **Speed** | Upload + process + download | Process instantly |
| **Cost** | Server bills | Free (static hosting) |
| **Scalability** | Need infrastructure | Unlimited users |
| **File size limit** | Server constraints | Device memory only |

---

## License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## Author

**Mohamed Khalifa**

[![Facebook](https://img.shields.io/badge/Facebook-1877F2?style=flat&logo=facebook&logoColor=white)](https://www.facebook.com/moekhalifa8/)
[![GitHub](https://img.shields.io/badge/GitHub-mokhalifa83-181717?style=flat&logo=github)](https://github.com/mokhalifa83)

---

*Built with ❤️ using vanilla JavaScript and WebAssembly.*
