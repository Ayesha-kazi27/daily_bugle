# Daily Bugle Tech Bootcamp — Landing Page

A single-file, self-contained landing page for a Google Developer Group tech bootcamp, themed around the Daily Bugle / Spider‑Man universe. Built with vanilla HTML/CSS, a small amount of vanilla JS, and one React island (loaded via CDN + in-browser Babel) for the stage carousel.

No build step, no bundler, no `npm install` — just open `index.html` in a browser.

---

## Quick start

1. Place these three asset files in the **same folder** as `index.html`:
   - `gdg.svg` — GDG logo (used in the navbar, favicon, and footer)
   - `lol5.mp4` — background video (scroll‑scrubbed on desktop, disabled on mobile for performance)
   - `web_white close.png` — close icon for the side menu
2. Open `index.html` directly in a browser, or serve the folder with any static file server:
   ```bash
   npx serve .
   # or
   python3 -m http.server
   ```
3. That's it — everything else (fonts, React, Babel) loads from CDNs at runtime, so an internet connection is required.

---

## What's on the page

- **Sticky glass navbar** with the GDG logo and a slide‑out side menu (Home / About / Stages / Login), all reachable by keyboard and mouse.
- **Scroll‑scrubbed hero video** behind a glitching "DAILY BUGLE / TECH BOOTCAMP" headline (video scrubbing is skipped on small screens to avoid jank).
- **Typewriter‑animated subtitle** that types itself out on page load.
- **Stage carousel** — a React component showing five "torn notebook paper" cards (Bootcamp Overview + Stages 1–4). Supports:
  - Prev/Next buttons
  - Numbered dot navigation (doubles as a stage progress indicator)
  - Swipe on touch devices
  - Arrow‑key navigation when focused
  - An `aria-live` region announcing the active slide for screen readers
- **Halftone comic‑print texture** overlaid on every notebook/paper card for a newsprint look.
- **Flip‑card registration form** — submitting the form flips the torn paper over (pure CSS 3D transform, no library) to reveal a confirmation slip with an animated ink "APPROVED" stamp and a personalized message using the entered team name. A "Register Another Team" button flips it back and resets the form.
- **Scroll‑triggered reveal** — the login card and footer fade/slide into view the first time they enter the viewport (`IntersectionObserver`).
- **Click sparks** — a small burst of particles fires from the cursor on every click, purely decorative.
- **Reduced‑motion support** — the typewriter, click sparks, and scroll reveals are all skipped/simplified if the OS‑level "reduce motion" setting is on.
- **Responsive down to small phones** — breakpoints at 900px / 600px / 380px cover tablets, phones, and small phones; the sticky navbar, carousel, and forms all resize accordingly.

---

## File structure

Everything lives in one file:

```
index.html
├── <head>
│   ├── Google Fonts (Orbitron, Courier Prime)
│   ├── React 18 + ReactDOM (CDN, development build)
│   ├── Babel Standalone (compiles the inline JSX at runtime)
│   └── <style> — all CSS, organized in commented sections
├── <body>
│   ├── Background video + overlay
│   ├── Navbar
│   ├── Hero (glitch text)
│   ├── Content wrapper
│   │   ├── #stack-carousel-root  ← React mounts the carousel here
│   │   ├── Flip‑card registration form
│   │   └── Footer details
│   ├── Side menu + backdrop
│   ├── <script> — vanilla JS (menu, video scrub, typewriter, reveal,
│   │   click sparks, form flip/stamp logic)
│   └── <script type="text/babel"> — the React carousel component
```

---

## Tech stack

| Piece | Choice | Why |
|---|---|---|
| Markup/styling | Plain HTML + CSS | No build step needed |
| Carousel | React 18 (CDN) + Babel Standalone | Only the carousel needed component state; kept isolated to one mount point rather than converting the whole page |
| Everything else | Vanilla JS | Menu toggle, video scrub, typewriter, scroll reveal, click sparks, and the form flip don't need a framework |
| Fonts | Orbitron (display), Courier Prime (loaded, currently unused — available if you want a typewriter‑style body font) | |

> Note: an earlier version used Framer Motion for a drag‑based "stack" carousel. It was replaced with a plain button/dot/swipe carousel because drag gestures conflicted with page scrolling on touch devices. Framer Motion is no longer loaded.

---

## Customizing content

- **Carousel slides**: edit the `cardsContent` array inside `function CarouselApp()` (near the bottom `<script type="text/babel">` block). Each slide is a `<NotebookCard title="...">...</NotebookCard>`.
- **Ticker / announcements**: (removed in the current version — see below if you want it back.)
- **Ticker headlines** *(if re‑added)*: were plain `<span class="ticker-item">` elements, duplicated once in the DOM for a seamless CSS scroll loop.
- **Registration form fields**: edit the `<form id="registerForm">` markup; the submit handler reads `#fullName` by ID, so keep that ID if you add more fields.
- **Confirmation message**: edit the fallback string in the `registerForm.addEventListener('submit', ...)` handler in the vanilla `<script>` block.
- **Colors**: the palette is driven by a handful of hex values reused throughout (`#0d0b14` background, `#FFF0C4` cream, `#8C1007` / `#660B05` red accents). Search and replace to re‑theme.

---

## Browser support notes

- Requires a browser with CSS `clip-path`, `backdrop-filter`, and CSS Grid support (all modern evergreen browsers).
- `backdrop-filter` is prefixed with `-webkit-backdrop-filter` for Safari.
- The flip‑card confirmation uses `backface-visibility` + 3D `transform`s — supported in all current major browsers.
- No polyfills are included; this targets modern browsers only, not IE11.

---

## Known limitations

- All copy (bootcamp description, stage details, footer credits) is hardcoded in the HTML/JSX — there's no CMS or data file.
- The registration form has no backend; submitting it only triggers the front-end flip/confirmation animation, no data is actually sent anywhere.
- The background video file (`lol5.mp4`) is not included — you must supply your own.

---

## Credits

Organized by Google Developer Group, Pillai College of Engineering.