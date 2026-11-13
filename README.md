# 🗞️ Daily Bugle Tech Bootcamp — Landing Page

> *"With great code comes... ok you get it, let's go build something."*

A single-file, self-contained landing page and registration portal for the **Daily Bugle Tech Bootcamp**, organized by **Google Developer Group (GDG), Pillai College of Engineering** [cite: 1]. 

Themed around the Spider-Man / Daily Bugle universe, it blends a vintage newsprint comic-book aesthetic (halftone textures, torn notebook paper, rubber ink stamps) with modern futuristic web design (glitch typography, glassmorphism, and scroll-scrubbed video) [cite: 1]. **No build step, bundler, or `npm install` required**—just open `index.html` in a browser.

---

## 📋 Table of Contents
- [✨ Key Features](#-key-features)
- [📚 Curriculum Stages](#-curriculum-stages)
- [🏗️ Architecture & File Structure](#️-architecture--file-structure)
- [🛠️ Tech Stack](#️-tech-stack)
- [🚀 Quick Start](#-quick-start)
- [🎨 Customizing Content](#-customizing-content)
- [♿ Accessibility & Browser Support](#-accessibility--browser-support)
- [⚠️ Known Limitations](#️-known-limitations)
- [👤 Credits & Acknowledgments](#-credits--acknowledgments)

---

## ✨ Key Features

- **🕸️ Comic-Book & Newsprint Aesthetic:** Custom CSS `clip-path` torn notebook paper cards, binder hole cutouts, halftone dot-matrix overlays, and a crimson/cream palette (`#0d0b14`, `#660B05`, `#8C1007`, `#FFF0C4`) [cite: 1].
- **⚛️ Interactive Stage Carousel (React Island):** Standalone React 18 component displaying the Bootcamp Overview and Stages 1–4 [cite: 1]. Supports:
  - Prev/Next navigation buttons & numbered stage progress dots [cite: 1]
  - Touch-swipe gestures on mobile devices [cite: 1]
  - Left/Right keyboard arrow navigation when focused [cite: 1]
  - `aria-live` announcements for screen readers [cite: 1]
- **📝 3D Flip-Card Registration Portal:** Submitting the team registration form triggers a pure CSS 3D flip (`backface-visibility`) to reveal a confirmation slip complete with a personalized team message and an animated rubber-stamp **"APPROVED"** ink effect [cite: 1].
- **🎬 Scroll-Driven Video Background:** Scrubs through `lol5.mp4` frame-by-frame in sync with vertical scroll position (automatically disabled on screens `≤ 600px` to prevent mobile scroll jank) [cite: 1].
- **💥 Micro-Interactions & Motion Effects:**
  - **Glitch Hero Typography:** CSS keyframe clip-rect animations on *"DAILY BUGLE TECH BOOTCAMP"* [cite: 1].
  - **Typewriter Subtitle:** Auto-typing intro quote on page load [cite: 1].
  - **Click Sparks:** Multi-colored particle burst originating from the cursor on every click [cite: 1].
  - **Scroll Reveals:** Smooth fade/slide-up entrance animations powered by `IntersectionObserver` [cite: 1].
- **🧭 Sticky Glass Navbar & Side Drawer:** Slide-out navigation drawer with a web-shooter close icon, backdrop blur, and smooth-scroll section/slide linking [cite: 1].

---

## 📚 Curriculum Stages

| Stage | Title | Core Focus | Key Topics & Hands-On Challenge |
| :--- | :--- | :--- | :--- |
| **00** | **Overview** | Program Structure | Introduction to the bootcamp journey from logic fundamentals to live pitching [cite: 1]. |
| **01** | **Homecoming** | Algorithmic Logic & Engineering | Data structures (Arrays, Stacks, Queues, Hash Maps, BSTs), Big-O complexity ($O(n^2) \rightarrow O(n \log n)$), timed coding puzzles [cite: 1]. |
| **02** | **Far From Home** | Modern Web Engineering & UI | Component-driven React architecture, responsive CSS Grid/Flexbox, async API integration, interactive dashboard build [cite: 1]. |
| **03** | **No Way Home** | Advanced Optimization & Debugging | Memory leak profiling, database indexing/caching, fault tolerance, refactoring legacy code to cut latency by >60% [cite: 1]. |
| **04** | **Brand New Day** | Technical Leadership & Pitching | Translating architecture into value propositions, demo night prep, delivering a 3-minute live technical pitch [cite: 1]. |

---

## 🏗️ Architecture & File Structure

Everything is intentionally self-contained inside a single HTML file alongside three local media assets [cite: 1]:

```text
daily-bugle-bootcamp/
├── index.html              # Complete markup, CSS, vanilla JS, and React JSX
├── gdg.svg                 # GDG logo (navbar, favicon, and footer)
├── lol5.mp4                # Background video for desktop scroll-scrubbing
└── web_white close.png     # Web-shooter close button icon for the side drawer
```

### Inside `index.html`
```text
index.html
├── <head>
│   ├── Google Fonts (Orbitron & Courier Prime)
│   ├── React 18 & ReactDOM 18 (UMD CDN builds)
│   ├── Babel Standalone (in-browser JSX compilation)
│   └── <style> ── Reset, Glitch FX, Carousel, Torn Paper, 3D Flip, Responsive Breakpoints
└── <body>
    ├── <video id="scrollVideo"> ── Fixed scroll-scrubbed background
    ├── <nav class="navbar"> ── Sticky glassmorphic header
    ├── <main class="hero-container"> ── Glitching title + typewriter subtitle
    ├── <div class="content-wrapper">
    │   ├── #stack-carousel-root ── React mount point for the 5-card stage carousel
    │   ├── #login-section ── 3D flip registration form & confirmation slip
    │   └── .footer-details ── Event credits & quote
    ├── #sideMenu ── Slide-out drawer navigation
    ├── <script> ── Vanilla JS (menu toggle, video scrub, typewriter, reveal, sparks, form flip)
    └── <script type="text/babel"> ── React <CarouselApp /> & <NotebookCard /> components
```

---

## 🛠️ Tech Stack

| Layer | Technology | Purpose |
| :--- | :--- | :--- |
| **Structure & Styling** | HTML5 & CSS3 | Custom `clip-path` polygons, CSS 3D transforms, keyframe animations, responsive media queries (`900px`, `600px`, `380px`) [cite: 1]. |
| **Interactive Carousel** | React 18 + Babel Standalone | Isolated to `#stack-carousel-root` to cleanly manage slide state, touch swipes, and menu deep-links without a build pipeline [cite: 1]. |
| **DOM & Visual FX** | Vanilla JavaScript (ES6+) | Drives video scrubbing, `IntersectionObserver` reveals, click particle bursts, typewriter text, and form flip state [cite: 1]. |
| **Typography** | Google Fonts | **Orbitron** (primary display/UI font) and **Courier Prime** (loaded for optional monospace styling) [cite: 1]. |

> **Design Note:** An earlier iteration used Framer Motion for a drag-based stacked card deck, which conflicted with vertical page scrolling on touchscreens. It was replaced with the current lightweight horizontal track carousel for reliable cross-device UX.

---

## 🚀 Quick Start

Because React, Babel, and Google Fonts load from CDNs at runtime, an active internet connection is required, but **no local build tools are needed**.

1. **Verify Assets:** Ensure `gdg.svg`, `lol5.mp4`, and `web_white close.png` are in the same directory as `index.html` [cite: 1].
2. **Run Locally:** Open `index.html` directly in your browser, or spin up a quick local static server:

```bash
# Option 1: Python 3
python3 -m http.server 8000

# Option 2: Node.js (npx)
npx serve .
```
3. Visit `http://localhost:8000` (or the port shown in your terminal).

---

## 🎨 Customizing Content

<details>
<summary><strong>Click to expand customization guide</strong></summary>

- **Edit Carousel Stages:** Locate `const cardsContent = [...]` inside `function CarouselApp()` in the `<script type="text/babel">` block at the bottom of `index.html` [cite: 1]. Add, remove, or edit `<NotebookCard title="...">` components [cite: 1].
- **Modify Registration Form:** Edit `<form id="registerForm">` in the HTML body [cite: 1]. Keep `id="fullName"` intact if adding fields, as the submit handler reads it to personalize the confirmation slip [cite: 1].
- **Change Theme Colors:** Search and replace the core hex codes across `<style>` and the `sparkColors` JS array:
  - Background Dark: `#0d0b14` [cite: 1]
  - Paper Cream: `#FFF0C4` [cite: 1]
  - Primary Crimson: `#8C1007` [cite: 1]
  - Deep Maroon: `#660B05` [cite: 1]

</details>

---

## ♿ Accessibility & Browser Support

- **Reduced Motion (`prefers-reduced-motion`):** Automatically disables glitch animations, smooth scrolling, typewriter effects, click sparks, and scroll-reveal transitions for users with OS-level motion sensitivity enabled [cite: 1].
- **Keyboard & Screen Reader Friendly:** Supports `ArrowLeft`/`ArrowRight` carousel navigation, visible focus rings (`:focus-visible`), and an `aria-live="polite"` slide announcer [cite: 1].
- **Browser Compatibility:** Targets modern evergreen browsers (Chrome, Edge, Firefox, Safari) supporting CSS `clip-path`, `backdrop-filter` (with `-webkit-` prefix), CSS Grid, and 3D `backface-visibility` [cite: 1].

---

## ⚠️ Known Limitations

- **Frontend-Only Registration:** Submitting the form triggers the 3D flip confirmation animation locally; no backend API or database is wired up yet.
- **Hardcoded Copy:** All stage descriptions and event details live directly in `index.html` rather than an external JSON/CMS file [cite: 1].
- **Media Dependency:** `lol5.mp4` is required for the desktop background video effect [cite: 1].

---

## 👤 Credits & Acknowledgments

- **Organized By:** Google Developer Group (GDG), Pillai College of Engineering
- **Developed By:** Peter Parker (Ayesha Kazi)
- **Event:** Daily Bugle Expo
