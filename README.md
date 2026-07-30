# 🗞️ Daily Bugle Tech Bootcamp

A Spider-Man-themed, interactive landing page and registration portal built for the **Daily Bugle Tech Bootcamp**, organized by **Google Developer Group (GDG), Pillai College of Engineering**.

This project features a comic-book vintage aesthetic combined with modern futuristic web design elements—including glitch typography, notebook paper cards with halftone textures, scroll-driven video backgrounds, interactive React components, and custom visual effects.

---

## ✨ Features

- **🕸️ Spider-Man / Daily Bugle Aesthetic:** Custom-styled torn paper cards, notebook hole cutouts, halftone comic-print textures, and crimson/cream color schemes (`#660B05`, `#8C1007`, `#FFF0C4`).
- **📱 Responsive Layout & Mobile Optimization:** Smooth fluid layout using `clamp()`, media queries, touch-swipe support for carousels, and mobile-friendly performance tweaks.
- **⚛️ Interactive React Stage Carousel:** In-browser standalone React 18 component (using Babel Standalone) displaying boot camp stages with touch gesture support, dot indicators, and keyboard navigation (`ArrowLeft` / `ArrowRight`).
- **📝 Dynamic Registration Form with Ink Stamp Flip:** Interactive registration form that flips to a confirmation slip featuring an animated rubber-stamp ink effect upon submission.
- **🎬 Scroll-Driven Video Sync:** Background video (`lol5.mp4`) frame-scrubbed in sync with page scroll position (automatically disabled on mobile for performance).
- **💥 Visual & Motion Effects:**
  - Dynamic glitch text animations (`DAILY BUGLE TECH BOOTCAMP`).
  - Typewriter text effect for subtitle quote.
  - Multi-colored click spark particle burst on user interaction.
  - IntersectionObserver-powered scroll reveal animations.
- **🧭 Side Drawer Navigation:** Animated slide-out menu with web-shooter icon close trigger and backdrop overlay.

---

## 📚 Curriculum Stages

| Stage | Title | Core Focus | Key Topics |
| :--- | :--- | :--- | :--- |
| **00** | **Overview** | Program Structure | Overall introduction to the Spider-Man Tech Bootcamp. |
| **01** | **Homecoming** | Algorithmic Logic & Engineering | Data structures, Big-O complexity, logic pipelines, timed coding puzzles. |
| **02** | **Far From Home** | Modern Web Engineering & UI | React architecture, CSS Grid/Flexbox, responsive UI systems, API integration. |
| **03** | **No Way Home** | Advanced Optimization & Debugging | Memory leak detection, database indexing, performance profiling, fault tolerance. |
| **04** | **Brand New Day** | Technical Leadership & Pitching | Live product demos, technical presentation skills, hackathon leadership. |

---

## 🛠️ Tech Stack & Dependencies

- **HTML5 & CSS3:** Custom keyframe animations, CSS clip-paths, CSS variables, and layout systems.
- **JavaScript (ES6+):** Vanilla JS for DOM interaction, video scrub control, custom events, and particle effects.
- **React 18 & ReactDOM 18:** Standalone UMD distribution for UI state management.
- **Babel Standalone:** In-browser JSX compilation.
- **Google Fonts:**
  - [Orbitron](https://fonts.google.com/specimen/Orbitron) (Sci-fi / Futuristic typography)
  - [Courier Prime](https://fonts.google.com/specimen/Courier+Prime) (Monospace typewriter typography)

---

## 📁 Required Assets

To run the project locally with full visual and media fidelity, ensure the following media files are located in the root directory alongside `index.html`:

| Asset File | Type | Description |
| :--- | :--- | :--- |
| `gdg.svg` | SVG Image | Google Developer Group branding logo / favicon |
| `lol5.mp4` | MP4 Video | Background video for scroll-driven scrubbing |
| `web_white close.png` | PNG Image | Web-shooter icon button used in the side navigation drawer |

---

## 🚀 Getting Started

Since the application uses CDN links for React, Babel, and Google Fonts, no build tools (`npm`, `webpack`, `vite`) are strictly required. You can serve it using any simple static HTTP server.

### Option 1: Live Server (VS Code)
1. Open the project folder in **Visual Studio Code**.
2. Install the **Live Server** extension.
3. Right-click `index.html` and select **Open with Live Server**.

### Option 2: Python HTTP Server
Run the following command in your terminal from the project root:

```bash
# Python 3
python -m http.server 8000
```
Then open `http://localhost:8000` in your browser.

---

## 👤 Credits & Acknowledgments

- **Organized By:** Google Developer Group (GDG), Pillai College of Engineering [cite: 1]
- **Developed By:** Peter Parker (Ayesha Kazi) [cite: 1]
- **Event:** Daily Bugle Expo [cite: 1]